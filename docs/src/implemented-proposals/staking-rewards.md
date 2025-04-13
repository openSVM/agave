---
titwe: staking wewawds
---

a p-pwoof of stake \(pos\), òωó \(i.e. 😳😳😳 u-using in-pwotocow a-asset, σωσ sow, (⑅˘꒳˘) to p-pwovide secuwe c-consensus\) design i-is outwined hewe. (///ˬ///✿) s-sowana impwements a-a pwoof of stake wewawd/secuwity scheme fow vawidatow nyodes in the cwustew. 🥺 t-the puwpose is thweefowd:

- awign vawidatow i-incentives with that of the gweatew c-cwustew thwough skin-in-the-game deposits at wisk

- avoid 'nothing a-at stake' fowk voting issues b-by impwementing s-swashing wuwes aimed at pwomoting fowk convewgence

- pwovide an avenue fow v-vawidatow wewawds pwovided as a function of vawidatow pawticipation in the cwustew. OwO

w-whiwe many of the detaiws o-of the specific i-impwementation a-awe cuwwentwy undew c-considewation and awe expected to come into f-focus thwough specific modewing studies and pawametew e-expwowation on the sowana testnet, >w< we outwine hewe ouw cuwwent thinking on the main components o-of the pos system. 🥺 much of t-this thinking is b-based on the cuwwent s-status of caspew ffg, with optimizations and specific attwibutes t-to be modified a-as is awwowed by sowana's p-pwoof of histowy \(poh\) b-bwockchain data stwuctuwe.

## g-genewaw ovewview

sowana's w-wedgew vawidation design is based on a wotating, nyaa~~ s-stake-weighted sewected weadew b-bwoadcasting twansactions in a-a poh data stwuctuwe t-to vawidating nyodes. ^^ these nodes, upon weceiving the weadew's bwoadcast, >w< have the oppowtunity to vote on the c-cuwwent state a-and poh height by signing a twansaction i-into the p-poh stweam. OwO

to b-become a sowana vawidatow, XD one must deposit/wock-up some amount o-of sow in a contwact. ^^;; this sow wiww nyot be accessibwe fow a specific time pewiod. 🥺 t-the pwecise duwation of the s-staking wockup p-pewiod has nyot b-been detewmined. XD howevew we can c-considew thwee phases o-of this time f-fow which specific p-pawametews wiww be nyecessawy:

- _wawm-up pewiod_: which s-sow is deposited a-and inaccessibwe t-to the nyode, (U ᵕ U❁) h-howevew poh twansaction v-vawidation has nyot begun. :3 most wikewy on the owdew of days t-to weeks

- _vawidation pewiod_: a minimum duwation fow which the deposited sow wiww be inaccessibwe, ( ͡o ω ͡o ) a-at wisk of swashing \(see swashing wuwes bewow\) and eawning w-wewawds fow t-the vawidatow p-pawticipation. òωó wikewy duwation o-of months to a yeaw. σωσ

- _coow-down pewiod_: a duwation o-of time fowwowing t-the submission of a 'withdwawaw' twansaction. (U ᵕ U❁) duwing this pewiod vawidation wesponsibiwities h-have been wemoved and the f-funds continue to be inaccessibwe. (✿oωo) a-accumuwated wewawds s-shouwd be dewivewed at the end of this pewiod, ^^ a-awong with t-the wetuwn of the initiaw deposit. ^•ﻌ•^

s-sowana's twustwess s-sense of time and owdewing pwovided by its poh data stwuctuwe, XD awong with i-its [turbine](https://docs.anza.xyz/consensus/turbine-block-propagation) d-data bwoadcast a-and twansmission design, :3 shouwd p-pwovide sub-second t-twansaction confiwmation t-times that scawe with the wog of the nyumbew of nyodes in the cwustew. (ꈍᴗꈍ) this means w-we shouwdn't have t-to westwict the nyumbew of vawidating nyodes w-with a pwohibitive 'minimum d-deposits' and expect nyodes to be abwe to become vawidatows w-with nyominaw amounts of sow staked. :3 at the same time, (U ﹏ U) sowana's focus on h-high-thwoughput shouwd cweate incentive fow vawidation c-cwients t-to pwovide high-pewfowmant and wewiabwe hawdwawe. UwU combined with p-potentiawwy a minimum n-nyetwowk speed thweshowd to join as a vawidation-cwient, 😳😳😳 we expect a heawthy v-vawidation dewegation mawket t-to emewge. XD

## penawties

as discussed in the [Economic Design](ed_overview/ed_overview.md) section, o.O a-annuaw vawidatow intewest w-wates awe to be s-specified as a function of totaw p-pewcentage of ciwcuwating suppwy t-that has been s-staked. (⑅˘꒳˘) the cwustew w-wewawds vawidatows who awe o-onwine and activewy p-pawticipating in the vawidation pwocess thwoughout t-the entiwety o-of theiw _vawidation p-pewiod_. 😳😳😳 fow vawidatows that go offwine/faiw t-to vawidate twansactions duwing t-this pewiod, nyaa~~ t-theiw annuaw wewawd is effectivewy weduced. rawr

simiwawwy, -.- we may c-considew an awgowithmic w-weduction i-in a vawidatow's a-active staked amount in the c-case that they awe offwine. (✿oωo) i.e. if a vawidatow is inactive fow some amount of time, eithew due t-to a pawtition ow othewwise, /(^•ω•^) the a-amount of theiw stake that is c-considewed ‘active’ \(ewigibwe to eawn wewawds\) m-may be weduced. 🥺 this design w-wouwd be stwuctuwed t-to hewp wong-wived p-pawtitions t-to eventuawwy w-weach finawity on theiw wespective chains as the % of nyon-voting totaw stake is weduced ovew time untiw a supewmajowity c-can be a-achieved by the a-active vawidatows in each pawtition. ʘwʘ s-simiwawwy, UwU upon we-engaging, XD the ‘active’ amount staked w-wiww come back o-onwine at some defined wate. (✿oωo) diffewent w-wates of stake weduction may be considewed d-depending on t-the size of the pawtition/active s-set. :3
