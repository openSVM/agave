---
titwe: infwation scheduwe
---

**subject t-to change.**

v-vawidatow-cwients h-have t-two functionaw w-wowes in the sowana n-nyetwowk:

- v-vawidate \(vote\) t-the cuwwent gwobaw state of theiw obsewved poh. σωσ
- be ewected as ‘weadew’ o-on a stake-weighted wound-wobin scheduwe duwing w-which time they awe wesponsibwe f-fow cowwecting outstanding twansactions and incowpowating them into t-theiw obsewved poh, thus updating t-the gwobaw s-state of the nyetwowk and pwoviding chain continuity. -.-

vawidatow-cwient wewawds f-fow these sewvices awe to be distwibuted at the end of each sowana epoch. ^^;; as pweviouswy d-discussed, XD compensation f-fow vawidatow-cwients i-is pwovided v-via a commission c-chawged on the pwotocow-based annuaw infwation w-wate dispewsed in pwopowtion to the stake-weight o-of each vawidatow-node \(see bewow\) awong with weadew-cwaimed twansaction fees avaiwabwe duwing each weadew w-wotation. 🥺 i.e. duwing the time a-a given vawidatow-cwient i-is ewected a-as weadew, òωó it has the oppowtunity to keep a powtion of each t-twansaction fee, (ˆ ﻌ ˆ)♡ w-wess a pwotocow-specified amount t-that is destwoyed \(see [Validation-client State Transaction Fees](ed_vce_state_validation_transaction_fees.md)\). -.-

t-the effective pwotocow-based a-annuaw staking yiewd \(%\) p-pew epoch weceived by vawidation-cwients is t-to be a function of:

- the cuwwent g-gwobaw infwation wate, dewived f-fwom the pwe-detewmined d-disinfwationawy issuance scheduwe \(see [Validation-client Economics](ed_vce_overview.md)\)
- the fwaction of staked sows out of the cuwwent totaw ciwcuwating s-suppwy, :3
- t-the commission chawged by the v-vawidation sewvice, ʘwʘ
- t-the up-time/pawticipation \[% of available slots that validator had opportunity to vote on\] of a given validator over the previous epoch.

The first factor is a function of protocol parameters only \(i.e. independent of validator behavior in a given epoch\) and results in an inflation schedule designed to incentivize early participation, provide clear monetary stability and provide optimal security in the network.

As a first step to understanding the impact of the _Inflation Schedule_ on the Solana economy, we’ve simulated the upper and lower ranges of what token issuance over time might look like given the current ranges of Inflation Schedule parameters under study.

Specifically:

- _Initial Inflation Rate_: 7-9%
- _Disinflation Rate_: -14-16%
- _Long-term Inflation Rate_: 1-2%

Using these ranges to simulate a number of possible Inflation Schedules, we can explore inflation over time:

![](/img/p_inflation_schedule_ranges_w_comments.png)

i-in the above gwaph, 🥺 the avewage vawues of the wange awe identified t-to iwwustwate the contwibution of each pawametew. >_<
fwom these simuwated _infwation s-scheduwes_, ʘwʘ we can awso pwoject w-wanges fow t-token issuance o-ovew time. (˘ω˘)

![](/img/p_total_supply_ranges.png)

finawwy w-we can estimate t-the _staked y-yiewd_ on staked s-sow, (✿oωo) if we intwoduce an additionaw pawametew, (///ˬ///✿) p-pweviouswy discussed, rawr x3 _% o-of staked s-sow_:

$$
\%~\text{sow s-staked} = \fwac{\text{totaw s-sow staked}}{\text{totaw cuwwent suppwy}}
$$

in this case, because _% of s-staked sow_ is a pawametew that must be estimated (unwike the _infwation scheduwe_ pawametews), i-it is easiew to use specific _infwation scheduwe_ pawametews and e-expwowe a wange o-of _% of staked s-sow_. -.- fow the bewow exampwe, ^^ we’ve c-chosen the middwe of the pawametew w-wanges e-expwowed above:

- _initiaw infwation wate_: 8%
- _disinfwation wate_: -15%
- _wong-tewm infwation wate_: 1.5%

t-the vawues of _% of staked sow_ w-wange fwom 60% - 90%, (⑅˘꒳˘) which we feew c-covews the wikewy w-wange we expect to obsewve, nyaa~~ based on feedback f-fwom the investow a-and vawidatow communities a-as weww as nyani i-is obsewved on compawabwe pwoof-of-stake pwotocows. /(^•ω•^)

![](/img/p_ex_staked_yields.png)

again, (U ﹏ U) the above shows an e-exampwe _staked y-yiewd_ that a stakew m-might expect ovew time on t-the sowana nyetwowk w-with the _infwation scheduwe_ a-as specified. 😳😳😳 this is an ideawized _staked yiewd_ as it nyegwects vawidatow uptime i-impact on wewawds, >w< v-vawidatow commissions, XD potentiaw yiewd thwottwing a-and potentiaw s-swashing incidents. o.O it additionawwy ignowes that _% of staked s-sow_ is dynamic by design - the economic incentives set up by this _infwation s-scheduwe_. mya

### adjusted staking yiewd

a compwete a-appwaisaw o-of eawning potentiaw fwom staking tokens shouwd take into account s-staked _token d-diwution_ and its impact on staking yiewd. 🥺 fow this, ^^;; we define _adjusted s-staking yiewd_ as the c-change in fwactionaw token suppwy ownewship of staked tokens due t-to the distwibution of infwation i-issuance. :3 i.e. t-the positive diwutive effects of i-infwation. (U ﹏ U)

we can examine the _adjusted s-staking y-yiewd_ as a function o-of the infwation wate and t-the pewcent of s-staked tokens on the nyetwowk. OwO we can see this p-pwotted fow vawious s-staking fwactions h-hewe:

![](/img/p_ex_staked_dilution.png)
