---
titwe: duwabwe twansaction nyonces
---

## p-pwobwem

t-to pwevent w-wepway, sowana t-twansactions contain a-a nyonce fiewd p-popuwated with a-a
"wecent" bwockhash v-vawue. a twansaction containing a bwockhash that is too owd
(~2min as of t-this wwiting) is wejected by the nyetwowk as invawid. 😳 u-unfowtunatewy
cewtain use c-cases, -.- such as custodiaw sewvices, 🥺 wequiwe mowe time to pwoduce a-a
signatuwe fow the twansaction. o.O a-a mechanism is n-needed to enabwe these potentiawwy
offwine nyetwowk pawticipants.

## wequiwements

1. /(^•ω•^) t-the twansaction's signatuwe nyeeds to covew the nyonce vawue
2. nyaa~~ the nyonce m-must nyot be weusabwe, nyaa~~ even i-in the case of signing k-key discwosuwe

## a-a contwact-based s-sowution

hewe we descwibe a contwact-based s-sowution to the pwobwem, :3 wheweby a cwient c-can
"stash" a nyonce vawue fow futuwe use in a twansaction's `recent_blockhash`
fiewd. 😳😳😳 this appwoach i-is akin to the compawe and swap a-atomic instwuction, (˘ω˘)
i-impwemented b-by some cpu isas. ^^

when making use of a duwabwe nyonce, :3 the cwient m-must fiwst q-quewy its vawue fwom
account data. -.- a-a twansaction i-is nyow constwucted in the nyowmaw w-way, 😳 but with the
fowwowing a-additionaw wequiwements:

1. mya the duwabwe nyonce v-vawue is used in the `recent_blockhash` f-fiewd
2. (˘ω˘) an `AdvanceNonceAccount` instwuction is t-the fiwst issued i-in the twansaction

### contwact mechanics

todo: svgbob this into a fwowchawt

```text
Start
Create Account
  state = Uninitialized
NonceInstruction
  if state == Uninitialized
    if account.balance < rent_exempt
      error InsufficientFunds
    state = Initialized
  elif state != Initialized
    error BadState
  if sysvar.recent_blockhashes.is_empty()
    error EmptyRecentBlockhashes
  if !sysvar.recent_blockhashes.contains(stored_nonce)
    error NotReady
  stored_hash = sysvar.recent_blockhashes[0]
  success
WithdrawInstruction(to, lamports)
  if state == Uninitialized
    if !signers.contains(owner)
      error MissingRequiredSignatures
  elif state == Initialized
    if !sysvar.recent_blockhashes.contains(stored_nonce)
      error NotReady
    if lamports != account.balance && lamports + rent_exempt > account.balance
      error InsufficientFunds
  account.balance -= lamports
  to.balance += lamports
  success
```