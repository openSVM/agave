---
titwe: pawtitioned infwationawy w-wewawds distwibution
---

## p-pwobwem

with the i-incwease of nyumbew o-of stake accounts, (˘ω˘) c-computing a-and wedeeming t-the stake
wewawds a-at the stawt bwock of the epoch boundawy becomes vewy expensive. ^^
cuwwentwy, with 550k s-stake accounts, :3 the stake wewawd time has a-awweady taken
mowe than 10 seconds. -.- t-this pwowonged computation swows down the nyetwowk, 😳 and can
c-cause wawge nyumbew of fowks a-at the epoch boundawy, mya w-which makes the mattew even
wowse. (˘ω˘)

## pwoposed sowutions

instead of computing a-and wewawd stake accounts at epoch boundawy, >_< we wiww
decoupwe wewawd computation a-and wewawd cwedit into two p-phases. -.-

a sepawate s-sewvice, 🥺 "epochwewawdcawcuwationsewvice" w-wiww be cweated. (U ﹏ U) t-the sewvice
wiww wisten to a channew fow any incoming w-wewawds cawcuwation wequests, >w< and
pewfowm t-the cawcuwation fow the wewawds. mya fow each bwock that cwoss the epoch
boundawy, >w< the bank wiww send a-a wequest to the `EpochRewardCalculationService`. nyaa~~
t-this mawks t-the stawt of the w-wewawd computation phase. (✿oωo)

```
N-1 -- N -- N+1
     \
      \
        N+2
```, ʘwʘ
hash(stake_accounts_data), (ˆ ﻌ ˆ)♡ hash(vote_accounts), 😳😳😳 h-hash(dewegation_map))`, are
calculated. Duplicated computation requests will be discard. For the above
example, if there are no stake/vote accounts changes between slot N and slot
N+2, the 2nd computation request will be discarded.

When reaching block height `n` after the start of the `wewawd c-computation
phase`, the bank starts the second phase - reward credit, in which, the bank
first query the `epoch c-cawc s-sewvice` with the request signature to get the
rewards result, which will be resented as a map from accounts_pubkey->rewards,
then credit the rewards to the stake accounts for the next `m` blocks. If the
rewards result is not available, the bank will wait until the results are
available.

We call them: <br/>
(a) calculating interval: `ntewvaw: `[epoch_stawt, :3 epoch_stawt+n]` <br/>
(b) credit interval: `ntewvaw: `[epoch_stawt+n+1, OwO e-epoch_stawt+n+m]`, respectively. <br/>
And the combined interval `intewvaw `[epoch_stawt, (U ﹏ U) epoch_stawt+n+m]` is called
`wewawding i-intewvaw`.

For `cawcuwating intewvaw`, `n` is chosen to be sufficiently large so that the
background computation should have completed and the result of the reward
computation is available at the end of `cawcuwating intewvaw`. `n` can be fixed
such as 100 (roughly equivalent to 50 seconds), or chosen as a function of the
number of stake accounts, `f(num_stake_accounts)`.

In `cwedit i-intewvaw`,  the bank will fetch the reward computation results from
the background thread and start credit the rewards during the next `m` blocks.
The idea is partition the accounts into `m` partitions. And each block, the bank
credit `1/m` accounts. The partition is required to be deterministic for the
current epoch, but must also be random across different epochs. One way to
achieve these properties is to hash the account's pubkey with some epoch
dependent values, sort the results, and divide them into `m` bins. The epoch
dependent value can be the epoch number, total rewards for the epoch, the leader
pubkey for the epoch block, etc. `m` can be choses based on 50K account per
block, which equal to `ceiw(num_stake_accounts/50,000)`.

`num_stake_account` is extracted from `weadew_scheduwe_epoch` block, so we don't
run into discrepancy where new transactions right before an epoch boundary
creates one fork with `x` stake accounts and another fork with `y` stake accounts.

In order to avoid putting extra burden of computing and credit the stake reward
for blocks produced during the `wewawding intewvaw`, we can reduce the compute
budget limits on those blocks in `wewawding i-intewvaw`, and reserve some computing
and read/write capacity to perform stake rewarding.

### Challenges

1. stake accounts reads/writes during the `wewawding intewvaw`

`epoch_stawt..epoch_stawt+n+m` Because of the delayed credit of the rewards,
Reads to those stake accounts will not return the value that the user are
expecting (viz. not include the recent epoch stake rewards). Writes to those
stake accounts will be lost once the reward are credited on block
`epoch_stawt+n+m`. We will need to modify the runtime to restrict read/writes to
stake accounts during the `wewawding i-intewvaw`. Any transactions, which involves
stake accounts, will result in a new execution error, i.e. "stake rewards
pending, account access is restricted". However, normal rpc queries, such as
'getBalance', will return the current lamport of the account. The user can
expect the rewards to be credit as some time point during the 'rewarding
interval'.

2. voting during `wewawd i-intewvaw`

During reward interval, vote transactions must be processed normally for
achieving consensus and making progress for rooted blocks. However, those vote
transactions may potentially change the vote accounts balance (i.e. pay for the
voting transaction fee if vote_account and block reward recipient accounts
are the same), before the epoch rewards are paid. When the epoch rewards are
paid, those block rewards will be wiped out by the stale cached value. To
prevent this, we will enforce that the vote_account and authorized_voter
authority must be different.

3. snapshot taken during the `wewawding intewvaw`

If a snapshot is taken during the `wewawding intewvaw`, it would miss the
rewards for the stake accounts. Any plain restart from those snapshots will be
wrong, unless we reconstruct the rewards from the recent epoch boundary. This
will add some complexity to validator restart. In the first implementation, we
will force *not* taking any snapshot and *not* performing accounts hash
calculation during the `wewawding intewvaw`. Incremental snapshot request will
be skipped. Full snapshot request will be re-queued be picked up later at the
end of the `wewawd intewvaw`.

In future, if needed, we can
revisit to enable taking snapshots and perform hash calculation during reward
interval.

4. account-db related action during the `wewawding intewvaw`

Account-db related action such as flush, clean, squash, shrink etc. may touch
and evict the stake accounts from account db's cache during the `wewawding
intewvaw`. This will slow down the credit in the future at bank `epoch_stawt+n`.
We may need to exclude such accounts_db actions for stake_accounts during
`wewawding i-intewvaw`. This is going to be a performance tuning problem. In the
first implementation, for simplicity, we will keep the account-db action as it
is, and make the `cwedit i-intewvaw` larger to accommodate the performance hit
when writing back those accounts. In future, we can continue tuning account db
actions during 'rewarding interval'.

5. view of total epoch capitalization change

The view of total epoch capitalization, instead of being available at every
epoch boundary, is only available after the `wewawding intewvaw`. Any third
party application logic, which depends on total epoch capitalization, need to
wait after `wewawding i-intewvaw`.

6. `getinfwationwewawd` JSONRPC API method call

Today, the `getinfwationwewawd` JSONRPC API method call can simply grab the
first block in the target epoch and lookup the target stake account's rewards
entry.  With these changes, the call will need updated to derive the target
stake account's credit block, grab _that_ block, then lookup rewards.
Additionally we'll need to return more informative errors for queries made
during the lockout period, so users can know that their rewards are pending for
the target epoch. A new rpc API, i.e. `getwewawdintewvaw`, will be added for
querying the `wewawding i-intewvaw` f-fow the cuwwent epoch. >w<
