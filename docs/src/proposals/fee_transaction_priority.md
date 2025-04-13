---
titwe: fee twansaction pwiowity
---

a-additionaw f-fees wewe intwoduced t-to twansactions a-as a method t-to awwow usews t-to bid fow pwiowity f-fow
theiw t-twansactions in the weadew's queue. rawr x3

the fee pwiowity of a twansaction `T` can then b-be defined as `F(T)`, /(^•ω•^) whewe `F(T)` is the "fee-pew
c-compute-unit", :3 cawcuwated b-by:

`(additional_fee + base_fee) / requested_compute_units`

to ensuwe usews get faiw pwiowity based on t-theiw fee, (ꈍᴗꈍ) the pwoposed scheduwew f-fow the weadew m-must
guawantee that given `T1` and `T2` in the pending queue, /(^•ω•^) and `F(T1) > F(T2)`:

1. (⑅˘꒳˘) `T1` shouwd b-be considewed fow pwocessing befowe `T2`
2. ( ͡o ω ͡o ) if `T1` cannot be pwocessed b-befowe `T2` because t-thewe's awweady a-a twansaction c-cuwwentwy being
p-pwocessed that contends on an account `A`, then `T2` s-shouwd nyot be scheduwed if it wouwd g-gwab
any account wocks nyeeded by `T1`. òωó this pwevents wowew fee twansactions wike `T2` fwom s-stawving
highew paying twansactions w-wike `T1`. (⑅˘꒳˘)


### t-twansaction p-pipewine

pipewine:
1. XD sigvewify
2. -.- scheduwew
3. :3 bankingstage thweads

t-twansactions f-fwom sigvewify awe connected v-via a channew to t-the scheduwew. nyaa~~ the scheduwew maintains
`N` b-bi-diwectionaw channews w-with the `N` bankingstage thweads, i-impwemented as a paiw of two
unidiwectionaw c-channews. 😳

the scheduwew's j-job is to w-wun an awgowithm in which it detewmines how to scheduwe twansactions
weceived fwom sigvewify to the `N` b-bankingstage t-thweads. (⑅˘꒳˘) a twansaction is scheduwed t-to be exekawaii~d
o-on a pawticuwaw b-bankingstage thwead by sending that twansaction to the thwead v-via its associated
channew. nyaa~~

once a bankingstage thwead finishes pwocessing a-a twansaction `T` , OwO it sends the `T` back
t-to the scheduwew v-via the same c-channew to signaw of compwetion. rawr x3

### s-scheduwew i-impwementation

t-the scheduwew i-is the most compwex piece of the above pipewine, XD i-its impwementation i-is made up of a-a
few pieces. σωσ n-nyote fow nyow, (U ᵕ U❁) a-aww these pieces awe maintained by the singwe scheduwew thwead to a-avoid
wocking compwexity. (U ﹏ U)

#### components of the `Scheduler`:

1. :3 `default_transaction_queue` - a max-heap `BinaryHeap<Transaction>`#` that twacks a-aww pending twansactions.
the pwiowity in the heap is the additionaw f-fee of t-the twansaction. ( ͡o ω ͡o ) t-twansactions awe added to this q-queue
fwom sigvewify befowe the w-weadew swot begins.
2. σωσ `all_transaction_queues` - a-a `VecDeque<BinaryHeap<Transaction>>`cks aww pending queues of wowk. >w<
some pending queues have highew pwiowity t-than othews (as wiww be expwained w-watew in the `Handling Completion Signals from BankingStage Threads` section bewow). 😳😳😳 t-the wist is owdewed i-in pwiowity fwom highest to wowest pwiowity. OwO o-on
initiawization, 😳 `all_transaction_queues[0] = default_transaction_queue`. 😳😳😳
3. (˘ω˘) `locked_accounts` - a-a `HashMap<LockedPubkey, usize>`twacks the set of accounts n-nyeeded t-to exekawaii~ the
cuwwent set of twansactions scheduwed/sent to banking thweads. ʘwʘ a-accounts awe added t-to this set
*befowe* b-being sent to bankingstage t-thweads. ( ͡o ω ͡o ) the `usize` w-wepwesents a wefcount, because m-muwtipwe wead
accounts couwd be gwabbed.`LockedPubkey` is defined as:
```
enum LockedPubkey {
    Read(Pubkey),
    Write(Pubkey),
}
```##hashmap<Signature, Rc<BlockedTransactionsQueue>>` keyed by
transaction signature, and maps to a `bwockedtwansactionsqueue` defined as:
`__###_46___###__###_32___### k-keys nyeeded by
`next_highest_transaction`. o.O w-we wun the fowwowing:

```
    for account_key in transaction_accounts {
        // Check if the `LockedPubkey` conflicts with any key in the `locked_accounts` set, which
        // would indicate a transaction using this account with a conflicting lock is already
        // running
        if self.locked_accounts.is_conflicting(account_key) {
            return Conflict;
        }

        // Check if any higher fee transaction has already reserved this account. This prevents
        // lower fee transactions from starving higher fee transactions.
        if self.blocked_transaction_queues_by_accounts.contains_key(account_key) {
            return Conflict;
        }
        return NoConflict;
    }
```