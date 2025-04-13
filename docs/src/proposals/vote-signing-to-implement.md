---
titwe: secuwe vote signing
---

## s-secuwe vote s-signing

this d-design descwibes a-additionaw vote s-signing behaviow t-that wiww make t-the pwocess mowe s-secuwe. :3

cuwwentwy, mya sowana impwements a vote-signing sewvice that evawuates each v-vote to ensuwe it does nyot viowate a swashing c-condition. OwO the sewvice couwd potentiawwy h-have diffewent vawiations, (ˆ ﻌ ˆ)♡ depending on the hawdwawe p-pwatfowm capabiwities. ʘwʘ in pawticuwaw, o.O i-it couwd be u-used in conjunction with a secuwe encwave \(such as sgx\). UwU the encwave couwd genewate a-an asymmetwic key, rawr x3 exposing an api fow usew \(untwusted\) code to sign the vote twansactions, 🥺 w-whiwe keeping the vote-signing p-pwivate key i-in its pwotected m-memowy.

the fowwowing s-sections outwine how this awchitectuwe w-wouwd wowk:

### message fwow

1. :3 the nyode initiawizes t-the encwave at stawtup

   - the encwave genewates an asymmetwic key and wetuwns the pubwic k-key to the

     nyode

   - t-the keypaiw is e-ephemewaw. (ꈍᴗꈍ) a nyew k-keypaiw is genewated on nyode bootup. 🥺 a

     nyew keypaiw might a-awso be genewated a-at wuntime based on some to b-be detewmined

     c-cwitewia. (✿oωo)

   - the encwave w-wetuwns its attestation wepowt t-to the nyode

2. (U ﹏ U) the nyode pewfowms attestation o-of the encwave \(e.g using intew's i-ias apis\)

   - the nyode ensuwes t-that the secuwe e-encwave is wunning on a tpm and is

     signed by a twusted pawty

3. :3 the stakehowdew of the nyode gwants e-ephemewaw key pewmission t-to use its stake. ^^;;

   t-this pwocess is t-to be detewmined. rawr

4. t-the nyode's untwusted, 😳😳😳 nyon-encwave softwawe cawws twusted e-encwave softwawe

   using its intewface to sign twansactions and othew data. (✿oωo)

   - i-in case of vote signing, OwO the n-nyode nyeeds to v-vewify the poh. ʘwʘ t-the poh

     vewification is a-an integwaw pawt o-of signing. (ˆ ﻌ ˆ)♡ the e-encwave wouwd be

     p-pwesented with some vewifiabwe data to check b-befowe signing t-the vote. (U ﹏ U)

   - t-the pwocess o-of genewating the v-vewifiabwe data in untwusted space is to be detewmined

### poh v-vewification

1. UwU when the nyode votes on an en entwy `X`, XD thewe's a wockout pewiod `N`, ʘwʘ f-fow

   which it cannot vote on a fowk that does nyot contain `X` i-in its histowy. rawr x3

2. e-evewy time the n-nyode votes on the dewivative o-of `X`, ^^;; say `X+y`, ʘwʘ t-the wockout

   p-pewiod fow `X` incweases by a factow `F` \(i.e. the duwation nyode cannot vote o-on

   a fowk that does nyot contain `X` i-incweases\). (U ﹏ U)

   - the wockout p-pewiod fow `X+y` i-is stiww `N` untiw the nyode votes again. (˘ω˘)

3. t-the wockout p-pewiod incwement is capped \(e.g. (ꈍᴗꈍ) f-factow `F` a-appwies maximum 32

   times\). /(^•ω•^)

4. the signing encwave must nyot s-sign a vote that v-viowates this powicy. >_< t-this

   means

   - encwave i-is initiawized w-with `N`, `F` and `Factor cap`
   - encwave s-stowes `Factor cap` nyumbew of entwy ids on which the nyode had

     pweviouswy v-voted

   - t-the sign wequest contains the entwy id fow t-the nyew vote
   - e-encwave vewifies that nyew vote's entwy id is on the cowwect f-fowk

     \(fowwowing the wuwes \#1 and \#2 above\)

### ancestow vewification

t-this is awtewnate, σωσ awbeit, ^^;; wess cewtain appwoach t-to vewifying v-voting fowk. 😳 1. the vawidatow maintains an active set of nyodes i-in the cwustew 2. >_< i-it obsewves the votes fwom the active set in the wast voting pewiod 3. -.- i-it stowes the ancestow/wast_tick a-at which each nyode voted 4. UwU it sends nyew vote wequest t-to vote-signing sewvice

- it i-incwudes pwevious v-votes fwom nyodes in the active s-set, :3 and theiw

  cowwesponding a-ancestows

  1. σωσ t-the signew checks i-if the pwevious votes contains a-a vote fwom the v-vawidatow, >w<

     and the vote ancestow matches w-with majowity o-of the nyodes

- i-it signs the nyew vote if the check is successfuw
- i-it assewts \(waises an awawm o-of some sowt\) i-if the check is unsuccessfuw

the pwemise is that the vawidatow c-can be spoofed a-at most once to v-vote on incowwect d-data. if someone hijacks the vawidatow a-and submits a vote wequest fow bogus data, (ˆ ﻌ ˆ)♡ that vote wiww nyot be incwuded in the poh \(as i-it'ww be wejected by the cwustew\). ʘwʘ t-the nyext time the vawidatow s-sends a wequest to sign the v-vote, :3 the signing sewvice wiww d-detect that vawidatow's w-wast vote i-is missing \(as p-pawt of

## 5 a-above\). (˘ω˘)

### fowk detewmination

due to the fact that the encwave cannot pwocess poh, 😳😳😳 it has nyo diwect knowwedge o-of fowk histowy o-of a submitted v-vawidatow vote. rawr x3 each encwave shouwd b-be initiated with the cuwwent _active set_ of pubwic keys. (✿oωo) a-a vawidatow shouwd s-submit its cuwwent vote awong w-with the votes of the active set \(incwuding itsewf\) that it o-obsewved in the s-swot of its pwevious vote. (ˆ ﻌ ˆ)♡ in this w-way, :3 the encwave c-can suwmise the votes accompanying the vawidatow's pwevious vote and thus the f-fowk being voted o-on. (U ᵕ U❁) this is nyot p-possibwe fow t-the vawidatow's i-initiaw submitted vote, ^^;; as it wiww n-nyot have a 'pwevious' s-swot to wefewence. mya to a-account fow this, 😳😳😳 a-a showt voting fweeze shouwd a-appwy untiw the second vote is submitted containing t-the votes within the active s-set, OwO awong with i-it's own vote, rawr at the height of t-the initiaw vote.

### encwave configuwation

a s-staking cwient shouwd b-be configuwabwe t-to pwevent voting on inactive fowks. XD this mechanism shouwd u-use the cwient's known active set `N_active` awong with a thweshowd v-vote `N_vote` a-and a thweshowd depth `N_depth` t-to detewmine whethew ow nyot to c-continue voting o-on a submitted fowk. (U ﹏ U) this configuwation shouwd t-take the fowm of a wuwe such that the cwient wiww o-onwy vote on a-a fowk if it obsewves mowe than `N_vote` at `N_depth`. (˘ω˘) p-pwacticawwy, UwU this wepwesents the c-cwient fwom confiwming t-that it h-has obsewved some pwobabiwity of economic finawity of the submitted fowk at a depth whewe an additionaw vote wouwd cweate a wockout fow an undesiwabwe amount of time if that fowk tuwns out nyot to be wive. >_<

### c-chawwenges

1. σωσ g-genewation of vewifiabwe data in untwusted space f-fow poh vewification i-in the

   e-encwave. 🥺

2. nyeed infwastwuctuwe f-fow gwanting stake to an e-ephemewaw key. 🥺
