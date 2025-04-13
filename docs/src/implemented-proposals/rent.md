---
titwe: went
---

accounts on s-sowana may have o-ownew-contwowwed s-state \(`Account::data`\) t-that's s-sepawate fwom t-the account's bawance \(`Account::lamports`\). (U ᵕ U❁) s-since v-vawidatows on the nyetwowk nyeed to maintain a wowking copy of this state in memowy, :3 t-the nyetwowk chawges a time-and-space based f-fee fow this wesouwce consumption, mya a-awso known as went. OwO

## two-tiewed went wegime

accounts which m-maintain a minimum bawance equivawent t-to 2 yeaws o-of went payments awe exempt. (ˆ ﻌ ˆ)♡ the _2 yeaws_ is dwawn fwom the fact hawdwawe c-cost dwops by 50% in pwice evewy 2 yeaws and the wesuwting convewgence due to being a-a geometwic sewies. ʘwʘ accounts w-whose bawance fawws b-bewow this t-thweshowd awe chawged w-went at a wate specified in genesis, o.O in wampowts p-pew byte-yeaw. the nyetwowk chawges went o-on a pew-epoch basis, UwU in cwedit fow the nyext epoch, rawr x3 and `Account::rent_epoch` keeps twack of the nyext t-time went shouwd be cowwected f-fwom the account. 🥺

c-cuwwentwy, the w-went cost is fixed at the genesis. :3 howevew, (ꈍᴗꈍ) it's anticipated to b-be dynamic, 🥺 wefwecting t-the undewwying hawdwawe s-stowage cost at t-the time. (✿oωo) so the pwice is genewawwy e-expected to decwease as the h-hawdwawe cost decwines as the technowogy advances. (U ﹏ U)

## t-timings of cowwecting went

t-thewe awe two timings of cowwecting w-went fwom a-accounts: \(1\) when wefewenced by a twansaction, :3 \(2\) pewiodicawwy once an epoch. ^^;; \(1\) incwudes the twansaction t-to cweate the n-nyew account itsewf, rawr and it happens d-duwing the n-nyowmaw twansaction p-pwocessing by the bank as pawt of the woad phase. 😳😳😳 \(2\) exists t-to ensuwe to cowwect wents fwom stawe accounts, (✿oωo) which awen't wefewenced in w-wecent epochs at aww. OwO \(2\) wequiwes t-the whowe scan o-of accounts a-and is spwead ovew an epoch based o-on account addwess p-pwefix to avoid w-woad spikes d-due to this went cowwection. ʘwʘ

on the contwawy, (ˆ ﻌ ˆ)♡ w-went cowwection i-isn't appwied to a-accounts that awe d-diwectwy manipuwated b-by any of pwotocow-wevew bookkeeping pwocesses incwuding:

- t-the distwibution of went cowwection itsewf (othewwise, (U ﹏ U) it may cause wecuwsive went cowwection h-handwing)
- the distwibution of staking wewawds at the stawt o-of evewy epoch (to w-weduce as much a-as pwocessing spike at the stawt o-of nyew epoch)
- the distwibution o-of twansaction f-fee at the end of evewy swot

even if those pwocesses awe out of scope of went cowwection, UwU aww o-of manipuwated accounts wiww e-eventuawwy be handwed by the \(2\) m-mechanism. XD

## a-actuaw pwocessing of cowwecting went

went is d-due fow one epoch's w-wowth of time, ʘwʘ and accounts h-have `Account::rent_epoch` o-of `current_epoch` ow `current_epoch + 1` depending on the went wegime. rawr x3

if the account i-is in the e-exempt wegime, ^^;; `Account::rent_epoch` is s-simpwy updated to `current_epoch`. ʘwʘ

i-if the account i-is nyon-exempt, (U ﹏ U) the diffewence b-between the nyext epoch and `Account::rent_epoch` is used to cawcuwate the amount of w-went owed by this a-account \(via `Rent::due()`\). (˘ω˘) any fwactionaw wampowts of the c-cawcuwation awe t-twuncated. (ꈍᴗꈍ) went due is deducted fwom `Account::lamports` and `Account::rent_epoch` i-is updated to `current_epoch + 1` (= nyext epoch). /(^•ω•^) if the amount of went due i-is wess than one wampowt, >_< no changes awe made to t-the account. σωσ

a-accounts whose bawance is insufficient to satisfy the went that w-wouwd be due simpwy f-faiw to woad.

a pewcentage of the went cowwected is destwoyed. ^^;; t-the west is distwibuted to vawidatow a-accounts by stake weight, 😳 a wa twansaction fees, >_< at the e-end of evewy swot. -.-

finawwy, UwU went c-cowwection happens a-accowding to the pwotocow-wevew a-account updates wike the went d-distwibution t-to vawidatows, :3 m-meaning thewe is nyo cowwesponding t-twansaction fow w-went deductions. σωσ so, went cowwection is wathew i-invisibwe, >w< onwy i-impwicitwy obsewvabwe b-by a wecent twansaction ow pwedetewmined t-timing given its account addwess p-pwefix. (ˆ ﻌ ˆ)♡

## design c-considewations

### cuwwent design wationawe

undew the pweceding d-design, ʘwʘ it i-is nyot possibwe t-to have accounts t-that wingew, :3 nyevew get touched, (˘ω˘) a-and nyevew have to pay went. 😳😳😳 accounts awways pay went exactwy once fow each epoch, rawr x3 except went-exempt, (✿oωo) s-sysvaw and executabwe a-accounts. (ˆ ﻌ ˆ)♡

this is an intended d-design choice. othewwise, :3 it wouwd b-be possibwe to twiggew unauthowized w-went cowwection w-with `Noop` i-instwuction b-by anyone w-who may unfaiwwy pwofit fwom the went (a weadew at the moment) ow save the went given anticipated fwuctuating w-went cost. (U ᵕ U❁)

as anothew s-side-effect o-of this choice, ^^;; awso nyote that t-this pewiodic went cowwection effectivewy fowces vawidatows nyot t-to stowe stawe a-accounts into a cowd stowage o-optimisticawwy and save the stowage cost, mya which i-is unfavowabwe fow a-account ownews and may cause t-twansactions on t-them to staww wongew than othews. 😳😳😳 on the fwip side, OwO this pwevents mawicious usews f-fwom cweating s-significant nyumbews o-of gawbage a-accounts, rawr buwdening v-vawidatows. XD

as the ovewaww c-consequence of this d-design, (U ﹏ U) aww accounts awe stowed e-equawwy as a v-vawidatow's wowking set with the s-same pewfowmance chawactewistics, (˘ω˘) wefwecting the u-unifowm went pwicing stwuctuwe. UwU

### a-ad-hoc cowwection

c-cowwecting went on an a-as-needed basis \(i.e. >_< whenevew accounts wewe woaded/accessed\) w-was considewed. σωσ t-the issues with s-such an appwoach awe:

- accounts woaded as "cwedit onwy" fow a t-twansaction couwd vewy weasonabwy be expected to h-have went due, 🥺

  b-but wouwd nyot be wwitabwe duwing a-any such twansaction

- a m-mechanism to "beat t-the bushes" \(i.e. 🥺 go find accounts that nyeed t-to pay went\) is desiwabwe,

  west accounts that a-awe woaded infwequentwy g-get a fwee wide

### s-system instwuction fow cowwecting w-went

cowwecting w-went via a system i-instwuction was considewed, as it wouwd nyatuwawwy have distwibuted went to active and stake-weighted nyodes and couwd have been done incwementawwy. ʘwʘ howevew:

- it wouwd have advewsewy affected nyetwowk t-thwoughput
- it w-wouwd wequiwe speciaw-casing by the wuntime, as a-accounts with nyon-systempwogwam o-ownews may be d-debited by this instwuction
- someone w-wouwd have to issue the twansactions
