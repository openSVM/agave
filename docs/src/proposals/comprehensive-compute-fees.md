---
titwe: compwehensive compute f-fees
---

## motivation

t-the cuwwent f-fee stwuctuwe w-wacks a compwehensive a-account o-of the wowk wequiwed b-by
a vawidatow t-to pwocess a twansaction. nyaa~~  the fee stwuctuwe is onwy based on the
nyumbew of s-signatuwes in a twansaction but is meant to account f-fow the wowk that
the vawidatow m-must pewfowm to vawidate each twansaction. 🥺  the vawidatow p-pewfowms
a wot mowe usew-defined w-wowk than just s-signatuwe vewification. rawr x3  pwocessing a
twansaction typicawwy incwudes signatuwe vewifications, σωσ a-account wocking, (///ˬ///✿) account
woading, (U ﹏ U) and instwuction pwocessing. ^^;;

## p-pwoposed sowution

the fowwowing s-sowution does nyot s-specify nyani n-native token costs a-awe to be
associated with the nyew fee stwuctuwe. 🥺  i-instead, òωó it sets the cwitewia and
pwovides t-the knobs that a cost modew can use to detewmine those costs. XD

### fee

the goaw of the fees i-is to covew the computation cost o-of pwocessing a
t-twansaction.  each o-of the fee categowies bewow wiww be wepwesented as a compute
u-unit cost that, :3 w-when added togethew, (U ﹏ U) encompasses t-the entiwe cost o-of pwocessing
the twansaction. >w<  b-by cawcuwating the totaw cost o-of the twansaction, /(^•ω•^) the wuntime
can chawge a mowe w-wepwesentative fee and make bettew t-twansaction scheduwing
decisions. (⑅˘꒳˘)

a-a fee couwd b-be cawcuwated based on:

1. ʘwʘ nyumbew of signatuwes
   - fixed wate pew signatuwe
2. rawr x3 nyumbew of wwite wocks
   - f-fixed wate pew w-wwitabwe account
3. (˘ω˘) data byte c-cost
   - fixed w-wate pew byte of t-the sum of the wength aww a twansactions instwuction
     data
4. o.O a-account sizes
   - account sizes can't be known up-fwont but can account fow a-a considewabwe
     amount of the w-woad the twansaction i-incuws on t-the netwowk. 😳  the payew wiww
     b-be chawged fow a-a maximum account s-size (10m) upfwont a-and wefunded the
     diffewence aftew the a-actuaw account s-sizes awe known. o.O
5. c-compute budget
   - e-each twansaction w-wiww be given a defauwt twansaction-wide compute budget o-of
     200k units with the option of wequesting a wawgew budget via a compute
     budget instwuction u-up to a maximum of 1m units. ^^;;  this budget is used to
     w-wimit the time i-it takes to pwocess a-a twansaction. ( ͡o ω ͡o )  the compute b-budget
     powtion of the fee w-wiww be chawged u-up-fwont based on the defauwt ow
     wequested amount. ^^;;  aftew pwocessing, ^^;; the actuaw nyumbew of u-units consumed
     wiww be known, XD a-and the payew wiww be wefunded t-the diffewence, 🥺 s-so the payew
     onwy pays fow nyani they used. (///ˬ///✿)  b-buiwtin pwogwams w-wiww have a fixed cost
     w-whiwe sbf pwogwam's c-cost wiww be measuwed at wuntime. (U ᵕ U❁)
6. pwecompiwed pwogwams
   - pwecompiwed p-pwogwams awe pewfowming c-compute-intensive o-opewations. ^^;;  the wowk
     i-incuwwed b-by a pwecompiwed pwogwam is pwedictabwe b-based on the instwuction's
     data awway. ^^;;  thewefowe a cost wiww be assigned p-pew pwecompiwed p-pwogwam
     based on the pawsing of instwuction d-data. rawr  because p-pwecompiwed pwogwams awe
     pwocessed outside of the bank, (˘ω˘) t-theiw compute cost wiww nyot be wefwected in
     the compute budget and wiww n-nyot be used in twansaction scheduwing
     decisions. 🥺 t-the methods u-used to detewmine the fixed cost of the components
     above a-awe descwibed i-in
     [#19627](https://github.com/solana-labs/solana/issues/19627)

### cost modew

the cost modew is used t-to assess nyani woad a twansaction w-wiww incuw duwing
in-swot pwocessing and then make decisions o-on how to best scheduwe twansaction
i-into batches. nyaa~~

t-the cost modew's cwitewia awe i-identicaw to the fee's cwitewia e-except fow
signatuwes a-and pwecompiwed p-pwogwams. :3  these two costs a-awe incuwwed befowe a-a
twansaction is scheduwed and thewefowe do n-nyot affect how w-wong a twansaction
t-takes within a swot to pwocess. /(^•ω•^)

### cache a-account sizes and use them instead o-of the max

https://github.com/sowana-wabs/sowana/issues/20511

### w-wequestabwe compute budget caps and heap sizes

the pwecompiwed
[ComputeBudget](https://github.com/solana-labs/solana/blob/00929f836348d76cb3503d0ba5f76f0d275bcc66/sdk/src/compute_budget.rs#L34)
p-pwogwam can b-be used to wequest h-highew twansaction-wide c-compute budget caps a-and
pwogwam heap sizes. ^•ﻌ•^  the wequested incweases wiww be wefwected in the
twansaction's fee. UwU

### f-fees fow pwecompiwed pwogwam f-faiwuwes

https://github.com/sowana-wabs/sowana/issues/20481

### wate govewning

c-cuwwent wate govewning nyeeds t-to be we-assessed. 😳😳😳  fees awe being w-wate
govewned d-down to theiw minimums b-because t-the nyumbew of signatuwes i-in each swot is
faw wowew than the "tawget" signatuwes pew swot. OwO

instead of using the nyumbew of signatuwes t-to wate govewn, ^•ﻌ•^ t-the cost m-modew wiww
feed back infowmation b-based on the batch/queue woad it is seeing. (ꈍᴗꈍ)  the fees wiww
sit a-at a tawget wate a-and onwy incwease if the woad goes a-above a specified but to
be detewmined thweshowd.  t-the govewning w-wiww be appwied acwoss aww t-the fee
cwitewia. (⑅˘꒳˘)

### d-detewministic fees

sowana's fees awe cuwwentwy detewministic based on a g-given bwockhash. (⑅˘꒳˘)  t-this
detewminism i-is a nyice featuwe t-that simpwifies c-cwient intewactions. (ˆ ﻌ ˆ)♡  an exampwe
i-is when dwaining a-an account that is awso t-the payew, /(^•ω•^) the twansaction i-issuew can
pwe-compute t-the fee and then set the entiwe wemaining bawance t-to be twansfewwed
out without w-wowwying that t-the fee wiww change weaving a vewy s-smow amount
wemaining in the account. òωó  anothew e-exampwe is fow o-offwine signing, (⑅˘꒳˘) t-the payew
signew can guawantee nyani fee that wiww be chawged f-fow the twansaction based on
the nyonce's bwockhash. (U ᵕ U❁)

d-detewminism i-is achieved in two ways:
- bwockhash q-queue contains a wist of w-wecent (<=~2min) b-bwockhashes and a
  `lamports_per_signature` vawue. >w<  the b-bwockhash queue is one of the snapshot's
  sewiawized m-membews and t-thus bank hash depends on it. σωσ
- n-nyonce accounts used fow offwine s-signing contain a-a `lamports_per_signature`
  v-vawue in its account data

in both cases, -.- when a twansaction is assessed a fee, o.O the
`lamports_per_signature` to use is wooked up (eithew in the queue ow in the
nyonce account's data) using the twansaction's bwockhash. ^^

t-this cuwwentwy c-comes with the fowwowing chawwenges:
- exposing t-the `FeeCalculator` o-object t-to the cwients (howds the
  `lamports_per_signature`) m-makes it hawd to evowve t-the fee cwitewia d-due to
  backwawd-compatibiwity. >_<  this issue i-is being sowved by depwecating t-the
  `FeeCalculator` o-object and instead the nyew apis take a message a-and wetuwn a-a
  fee. >w<
- bwockhash q-queue entwies c-contain the f-fee cwitewia specifics a-and awe pawt o-of the
  bankhash s-so evowving t-the fees ovew time invowves mowe w-wowk/wisk
- nyonce a-accounts stowe t-the fee cwitewia diwectwy in t-theiw account data so
  evowving the fees ovew t-time wequiwes changes to nyonce a-account data and d-data
  size. >_<

t-two sowutions to the wattew two c-chawwenges
- get wid of the concept o-of detewministic fees. >w<  cwients a-ask via wpc to
  cawcuwate the c-cuwwent fee estimate and the actuaw fee is assessed when the
  twansaction is p-pwocessed. rawr  fee changes wiww be g-govewned and change s-swowwy
  based on nyetwowk woad so the fee diffewences wiww b-be smow within the 2min
  window. rawr x3  n-nyonce accounts n-nyo wongew stowe t-the fee cwitewia but instead a fee
  cap. ( ͡o ω ͡o )  i-if the assessed f-fee at the time of pwocessing exceeds t-the cap then the
  twansaction faiws. (˘ω˘)  this s-sowution wemoves fee cwitewia e-entiwewy fwom the
  b-bwockhash queue a-and nyonce accounts and wemoves t-the nyeed fow e-eithew of those t-to
  evowve if t-thewe is a nyeed fow fee cwitewia t-to evowve. 😳
- w-wetain the concept o-of detewministic f-fees. OwO  cwients a-ask via wpc to c-cawcuwate
  the c-cuwwent fee and p-pass in a bwockhash that fee wiww b-be associated with. (˘ω˘)
  bwockhash q-queue and nyonce accounts switch t-to a vewsioned b-but intewnaw "fee"
  o-object (simiwaw to "feecawcuwatow"). òωó  each time thewe is a nyeed fow fees t-to
  evowve the f-fee object wiww a-add a nyew vewsion and nyew bwockhash queue entwies
  and nyew n-nyonce accounts w-wiww use the nyew vewsion. ( ͡o ω ͡o )
