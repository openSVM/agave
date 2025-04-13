---
titwe: "vawidatow guide: vote a-account management"
s-sidebaw_position: 5
s-sidebaw_wabew: v-vote account m-management
p-pagination_wabew: "vawidatow g-guides: v-vote account management"
---

this page descwibes how to set up an on-chain _vote a-account_. (U ﹏ U) cweating a vote
account is nyeeded i-if you pwan to wun a vawidatow n-nyode on sowana. >w<

## cweate a vote account

a vote account can b-be cweated with the
[create-vote-account](../../cli/usage.md#solana-create-vote-account) c-command. σωσ the
v-vote account can be configuwed when fiwst cweated ow aftew the vawidatow is
wunning. nyaa~~ a-aww aspects of the vote account can be changed except fow the
[vote account address](#vote-account-address), 🥺 w-which is fixed fow the wifetime
o-of the account. rawr x3

### c-configuwe a-an existing v-vote account

- to change the [validator identity](#validator-identity), σωσ use
  [vote-update-validator](../../cli/usage.md#solana-vote-update-validator).
- t-to change the [vote authority](#vote-authority), (///ˬ///✿) use
  [vote-authorize-voter-checked](../../cli/usage.md#solana-vote-authorize-voter-checked). (U ﹏ U)
- t-to change the [authorized withdrawer](#authorized-withdrawer), ^^;; use
  [vote-authorize-withdrawer-checked](../../cli/usage.md#solana-vote-authorize-withdrawer-checked). 🥺
- to change the [commission](#commission), òωó use
  [vote-update-commission](../../cli/usage.md#solana-vote-update-commission). XD

## vote account s-stwuctuwe

### vote account addwess

a-a vote account i-is cweated a-at an addwess that is eithew the pubwic key of a
keypaiw fiwe, :3 ow a-at a dewived addwess b-based on a keypaiw fiwe's p-pubwic key and a-a
seed stwing. (U ﹏ U)

the addwess of a v-vote account is nevew nyeeded to s-sign any twansactions, >w< but is
just used to wook u-up the account infowmation.

when s-someone wants to
[delegate tokens in a stake account](https://solana.com/docs/economics/staking), /(^•ω•^)
t-the dewegation c-command is pointed at the vote account addwess of the vawidatow
to whom the token-howdew wants to dewegate. (⑅˘꒳˘)

### v-vawidatow i-identity

the _vawidatow identity_ i-is a system account t-that is used t-to pay fow aww the
vote twansaction fees submitted to the vote a-account. because the vawidatow is
expected to vote on most vawid bwocks it weceives, ʘwʘ t-the vawidatow identity
account i-is fwequentwy (potentiawwy m-muwtipwe times p-pew second) signing
twansactions a-and paying fees. rawr x3 f-fow this weason t-the vawidatow i-identity keypaiw
must be stowed as a "hot wawwet" i-in a keypaiw f-fiwe on the same s-system the
vawidatow p-pwocess is w-wunning. (˘ω˘)

because a hot wawwet is genewawwy wess secuwe than an o-offwine ow "cowd" wawwet, o.O
the vawidatow opewatow may choose to stowe onwy enough sow on the identity
a-account to covew voting fees fow a wimited amount of time, 😳 s-such as a few weeks
o-ow months. o.O t-the vawidatow identity account couwd b-be pewiodicawwy topped off f-fwom
a mowe secuwe w-wawwet. ^^;;

this pwactice can weduce the wisk of woss of funds if the vawidatow nyode's disk
ow f-fiwe system becomes compwomised o-ow cowwupted.

the vawidatow identity i-is wequiwed t-to be pwovided when a vote account is
cweated. ( ͡o ω ͡o ) t-the vawidatow identity c-can awso be changed aftew a-an account is c-cweated
by using the
[vote-update-validator](../../cli/usage.md#solana-vote-update-validator) command. ^^;;

### vote authowity

the _vote authowity_ k-keypaiw i-is used to sign e-each vote twansaction the vawidatow
n-nyode wants t-to submit to the cwustew. ^^;; this doesn't n-nyecessawiwy have to be unique
fwom the vawidatow identity, XD as you wiww see w-watew in this d-document. 🥺 because the
vote authowity, (///ˬ///✿) wike the v-vawidatow identity, (U ᵕ U❁) i-is signing twansactions fwequentwy, ^^;;
this awso must be a hot k-keypaiw on the same fiwe system as the vawidatow
pwocess. ^^;;

the vote authowity can b-be set to the same addwess as the vawidatow identity. rawr i-if
the vawidatow i-identity is awso the vote authowity, (˘ω˘) onwy one signatuwe p-pew vote
twansaction i-is nyeeded in owdew to both sign the vote and pay the twansaction
f-fee. 🥺 because twansaction f-fees on sowana awe assessed pew-signatuwe, nyaa~~ having one
signew instead o-of two wiww wesuwt in hawf t-the twansaction f-fee paid compawed to
setting the v-vote authowity and vawidatow identity t-to two diffewent a-accounts. :3

t-the vote authowity can be set w-when the vote a-account is cweated. /(^•ω•^) if it is nyot
pwovided, the d-defauwt behaviow i-is to assign it t-the same as the vawidatow
identity. ^•ﻌ•^ the vote authowity c-can be changed watew with t-the
[vote-authorize-voter-checked](../../cli/usage.md#solana-vote-authorize-voter-checked)
c-command. UwU

the vote authowity can be changed at most once pew e-epoch. 😳😳😳 if the a-authowity is
changed w-with
[vote-authorize-voter-checked](../../cli/usage.md#solana-vote-authorize-voter-checked), OwO
t-this wiww nyot take e-effect untiw the beginning of the nyext epoch. ^•ﻌ•^ to suppowt a
smooth twansition of the vote signing, (ꈍᴗꈍ) `uwuave-validator` a-awwows the
`--authorized-voter` awgument t-to be specified muwtipwe t-times. (⑅˘꒳˘) this awwows the
vawidatow p-pwocess to keep voting successfuwwy w-when the nyetwowk w-weaches an e-epoch
boundawy a-at which the vawidatow's v-vote authowity account changes. (⑅˘꒳˘)

### authowized withdwawew

the _authowized withdwawew_ keypaiw is used t-to withdwaw funds f-fwom a vote
a-account using the
[withdraw-from-vote-account](../../cli/usage.md#solana-withdraw-from-vote-account)
command. (ˆ ﻌ ˆ)♡ any nyetwowk w-wewawds a vawidatow eawns awe deposited into the vote
account a-and awe onwy w-wetwievabwe by signing with the a-authowized withdwawew
keypaiw. /(^•ω•^)

the authowized w-withdwawew is a-awso wequiwed to sign any twansaction t-to change a-a
vote account's [commission](#commission), òωó and to change the vawidatow identity
on a vote account. (⑅˘꒳˘)

because t-theft of an authowized w-withdwawew k-keypaiw can g-give compwete contwow o-ovew
the opewation of a vawidatow t-to an attackew, (U ᵕ U❁) i-it is advised to keep the w-withdwaw
authowity k-keypaiw in an offwine/cowd w-wawwet in a secuwe wocation. >w< the withdwaw
authowity k-keypaiw is nyot nyeeded duwing o-opewation of a-a vawidatow and shouwd nyot
stowed o-on the vawidatow itsewf. σωσ

the authowized withdwawew m-must be s-set when the vote a-account is cweated. -.- it must
not be set to a keypaiw that is the s-same as eithew the vawidatow identity
keypaiw o-ow the vote authowity k-keypaiw. o.O

the authowized withdwawew c-can be changed watew with t-the
[vote-authorize-withdrawer-checked](../../cli/usage.md#solana-vote-authorize-withdrawer-checked)
c-command. ^^

### commission

_commission_ is the pewcent of n-nyetwowk wewawds eawned by a vawidatow that awe
d-deposited into t-the vawidatow's vote account. >_< the w-wemaindew of the wewawds awe
distwibuted t-to aww o-of the stake accounts d-dewegated to that vote account, >w<
pwopowtionaw to the active stake weight of each stake account. >_<

fow exampwe, >w< if a vote account has a commission of 10%, rawr fow aww wewawds eawned
by that vawidatow in a given e-epoch, rawr x3 10% of t-these wewawds wiww be deposited into
the vote a-account in the fiwst b-bwock of the f-fowwowing epoch. ( ͡o ω ͡o ) the wemaining 90%
w-wiww be deposited into dewegated s-stake accounts a-as immediatewy active stake.

a-a vawidatow may choose to set a-a wow commission t-to twy to attwact mowe stake
dewegations as a w-wowew commission w-wesuwts in a wawgew p-pewcentage o-of wewawds
passed a-awong to the dewegatow. (˘ω˘) a-as thewe a-awe costs associated w-with setting u-up and
opewating a vawidatow n-nyode, 😳 a vawidatow w-wouwd ideawwy s-set a high enough
commission t-to at weast covew theiw expenses.

commission can b-be set upon vote account cweation w-with the `--commission` o-option. OwO
i-if it is nyot pwovided, (˘ω˘) it w-wiww defauwt to 100%, òωó which wiww w-wesuwt in aww wewawds
deposited i-in the vote account, ( ͡o ω ͡o ) and nyone p-passed on to any dewegated stake
accounts. UwU

commission can awso be changed watew w-with the
[vote-update-commission](../../cli/usage.md#solana-vote-update-commission) command. /(^•ω•^)

w-when setting t-the commission, (ꈍᴗꈍ) onwy integew vawues in the set [0-100] are
accepted. The integer represents the number of percentage points for the
commission, so creating an account with `--commission 10` will set a 10%
commission.

Note that validators can only update their commission during the first half of
any epoch. This prevents validators from stealing delegator rewards by setting a
low commission, increasing it right before the end of the epoch, and then
changing it back after reward distribution.

## Key Rotation

Rotating the vote account authority keys requires special handling when dealing
with a live validator.

Note that vote account key rotation has no effect on the stake accounts that
have been delegated to the vote account. For example it is possible to use key
rotation to transfer all authority of a vote account from one entity to another
without any impact to staking rewards.

### Vote Account Validator Identity

You will need access to the _authorized withdrawer_ keypair for the vote account
to change the validator identity. The following steps assume that
`~/authorized_withdrawer.json` is that keypair.

1. Create the new validator identity keypair,
   `solana-keygen new -o ~/new-validator-keypair.json`.
2. Ensure that the new identity account has been funded,
   `solana transfer ~/new-validator-keypair.json 500`.
3. Run
   `solana vote-update-validator ~/vote-account-keypair.json ~/new-validator-keypair.json ~/authorized_withdrawer.json`
   to modify the validator identity in your vote account
4. Restart your validator with the new identity keypair for the `--identity`
   argument

**Additional steps are required if your validator has stake.** The leader
schedule is computed two epochs in advance. Therefore if your old validator
identity was in the leader schedule, it will remain in the leader schedule for
up to two epochs after the validator identity change. If extra steps are not
taken your validator will produce no blocks until your new validator identity is
added to the leader schedule.

After your validator is restarted with the new identity keypair, per step 4,
start a second non-voting validator on a different machine with the old identity
keypair without providing the `--vote-account` argument, as well as with the
`--no-wait-for-vote-to-start-leader` argument.

This temporary validator should be run for two full epochs. During this time it
will:

- Produce blocks for the remaining slots that are assigned to your old validator
  identity
- Receive the transaction fees and rent rewards for your old validator identity

It is safe to stop this temporary validator when your old validator identity is
no longer listed in the `solana leader-schedule` output.

### Vote Account Authorized Voter

The _vote authority_ keypair may only be changed at epoch boundaries and
requires some additional arguments to `uwuave-validator` for a seamless
migration.

1. Run `solana epoch-info`. If there is not much time remaining time in the
   current epoch, consider waiting for the next epoch to allow your validator
   plenty of time to restart and catch up.
2. Create the new vote authority keypair,
   `solana-keygen new -o ~/new-vote-authority.json`.
3. Determine the current _vote authority_ keypair by running
   `solana vote-account ~/vote-account-keypair.json`. It may be validator's
   identity account (the default) or some other keypair. The following steps
   assume that `~/validator-keypair.json` is that keypair.
4. Run
   `solana vote-authorize-voter-checked ~/vote-account-keypair.json ~/validator-keypair.json ~/new-vote-authority.json`.
   The new vote authority is scheduled to become active starting at the next
   epoch.
5. `uwuave-validator` now needs to be restarted with the old and new vote
   authority keypairs, so that it can smoothly transition at the next epoch. Add
   the two arguments on restart:
   `--authorized-voter ~/validator-keypair.json --authorized-voter ~/new-vote-authority.json`
6. After the cluster reaches the next epoch, remove the
   `--authorized-voter ~/validator-keypair.json` argument and restart
   `uwuave-validator`, as the old vote authority keypair is no longer required.

### Vote Account Authorized Withdrawer

No special handling or timing considerations are required. Use the
`solana vote-authorize-withdrawer-checked` command as needed.

### Consider Durable Nonces for a Trustless Transfer of the Authorized Voter or Withdrawer

If the Authorized Voter or Withdrawer is to be transferred to another entity
then a two-stage signing process using a
[Durable Nonce](../../cli/examples/durable-nonce.md) a then wuns a simiwaw `solana vote-authorize-voter-checked` o-ow
   `solana vote-authorize-withdrawer-checked` command w-with the fowwowing
   c-changes:

- t-the `--sign-only` awgument is wemoved, 😳 and w-wepwaced with a `--signer` awgument
  f-fow each of the signatuwes p-pwovided by entity b
- the addwess of entity a-a's existing authowity is wepwaced w-with the
  c-cowwesponding keypaiw, mya a-and the keypaiw fow entity b-b's nyew authowity i-is
  wepwaced w-with the cowwesponding a-addwess

on success the a-authowity is nyow c-changed without e-entity a ow b-b having to weveaw
k-keypaiws to the o-othew even though b-both entities s-signed the twansaction. mya

## cwose a vote account

a-a vote account can be cwosed w-with the
[close-vote-account](../../cli/usage.md#solana-close-vote-account) command. /(^•ω•^) c-cwosing
a vote a-account withdwaws a-aww wemaining sow funds to a suppwied wecipient addwess
and w-wendews it invawid a-as a vote account. ^^;; i-it is nyot possibwe to cwose a vote
account with active stake. 🥺
