---
titwe: ovewview of a sowana cwustew
s-sidebaw_position: 0
s-sidebaw_wabew: o-ovewview
p-pagination_wabew: o-ovewview of a-a sowana cwustew
---

a-a sowana c-cwustew is a set of vawidatows wowking togethew to sewve cwient twansactions and m-maintain the integwity of the wedgew. UwU many cwustews m-may coexist. XD when two cwustews s-shawe a common genesis bwock, (✿oωo) they attempt to convewge. :3 othewwise, t-they simpwy ignowe the existence o-of the othew. t-twansactions sent to the wwong one awe quietwy wejected. (///ˬ///✿) in this section, nyaa~~ w-we'ww discuss how a cwustew is cweated, >w< how nyodes join the cwustew, -.- how they shawe t-the wedgew, how they ensuwe t-the wedgew is wepwicated, (✿oωo) a-and how t-they cope with b-buggy and mawicious nyodes. (˘ω˘)

## cweating a cwustew

b-befowe stawting any vawidatows, rawr one fiwst nyeeds t-to cweate a _genesis config_. the config wefewences two pubwic keys, OwO a _mint_ and a _bootstwap v-vawidatow_. ^•ﻌ•^ the vawidatow howding t-the bootstwap v-vawidatow's p-pwivate key is wesponsibwe fow appending the fiwst entwies to the w-wedgew. UwU it initiawizes i-its intewnaw state with t-the mint's account. t-that account wiww howd the n-nyumbew of nyative tokens defined b-by the genesis config. (˘ω˘) the second vawidatow then c-contacts the bootstwap vawidatow t-to wegistew as a _vawidatow_. (///ˬ///✿) a-additionaw vawidatows t-then wegistew with any wegistewed membew of the cwustew. σωσ

a vawidatow weceives aww entwies fwom the weadew a-and submits v-votes confiwming those entwies awe v-vawid. /(^•ω•^) aftew v-voting, 😳 the vawidatow i-is expected to stowe those entwies. 😳 once the vawidatow obsewves a-a sufficient nyumbew of copies exist, it dewetes its copy. (⑅˘꒳˘)

## joining a cwustew

v-vawidatows entew the cwustew v-via wegistwation m-messages sent t-to its _contwow pwane_. 😳😳😳 the c-contwow pwane is i-impwemented using a-a _gossip_ pwotocow, 😳 m-meaning that a nyode may wegistew with any e-existing nyode, XD a-and expect its w-wegistwation to p-pwopagate to aww n-nyodes in the cwustew. mya the time it takes fow aww nyodes to synchwonize i-is pwopowtionaw to the squawe of the nyumbew of nodes pawticipating in the cwustew. ^•ﻌ•^ awgowithmicawwy, ʘwʘ that's c-considewed vewy swow, ( ͡o ω ͡o ) but in exchange fow that time, mya a nyode i-is assuwed that i-it eventuawwy h-has aww the same infowmation as e-evewy othew nyode, o.O and that infowmation c-cannot b-be censowed by any one nyode. (✿oωo)

## sending twansactions to a cwustew

cwients send twansactions to a-any vawidatow's twansaction pwocessing u-unit \(tpu\) powt. :3 if the n-nyode is in the v-vawidatow wowe, 😳 it fowwawds the twansaction to t-the designated w-weadew. (U ﹏ U) if in the weadew wowe, mya t-the nyode bundwes i-incoming twansactions, (U ᵕ U❁) timestamps them cweating an _entwy_, :3 and pushes them onto t-the cwustew's _data p-pwane_. mya once o-on the data pwane, OwO the twansactions a-awe vawidated b-by vawidatow nyodes, (ˆ ﻌ ˆ)♡ effectivewy a-appending them to the wedgew. ʘwʘ

## confiwming twansactions

a sowana cwustew i-is capabwe of s-subsecond _confiwmation_ fow thousands of nyodes w-with pwans to s-scawe up to hundweds of thousands of nyodes. o.O  confiwmation times a-awe expected to incwease onwy with the wogawithm of the nyumbew of vawidatows, UwU w-whewe the wogawithm's base is vewy high. rawr x3 if the b-base is one thousand, 🥺 f-fow exampwe, :3 it means that fow the fiwst thousand nyodes, (ꈍᴗꈍ) c-confiwmation wiww b-be the duwation of thwee nyetwowk hops pwus the time it takes t-the swowest vawidatow of a supewmajowity t-to vote. 🥺 fow the nyext miwwion nyodes, (✿oωo) confiwmation incweases b-by onwy one nyetwowk hop. (U ﹏ U)

s-sowana defines c-confiwmation as the duwation of t-time fwom when the weadew timestamps a-a new entwy t-to the moment w-when it wecognizes a supewmajowity o-of wedgew votes. :3

s-scawabwe confiwmation can be achieved using t-the fowwowing combination o-of techniques:

1. ^^;; t-timestamp twansactions with a vdf s-sampwe and sign the timestamp. rawr

2. s-spwit the twansactions i-into batches, 😳😳😳 send each to sepawate nyodes and have each n-nyode shawe its b-batch with its p-peews. (✿oωo)

3. OwO wepeat t-the pwevious step wecuwsivewy u-untiw aww nyodes have aww batches. ʘwʘ

sowana wotates weadews at fixed intewvaws, (ˆ ﻌ ˆ)♡ cawwed _swots_. (U ﹏ U) e-each weadew may onwy pwoduce entwies d-duwing its awwotted swot. UwU t-the weadew thewefowe timestamps t-twansactions so that vawidatows m-may wookup the pubwic k-key of the d-designated weadew. XD t-the weadew then s-signs the timestamp so that a vawidatow may vewify the signatuwe, ʘwʘ pwoving the signew is ownew of the designated w-weadew's pubwic k-key. rawr x3

nyext, ^^;; t-twansactions awe bwoken into batches s-so that a nyode can send twansactions to muwtipwe pawties w-without making muwtipwe c-copies. ʘwʘ if, fow exampwe, (U ﹏ U) t-the weadew nyeeded to send 60 twansactions to 6 n-nyodes, (˘ω˘) it wouwd b-bweak that cowwection of 60 into b-batches of 10 t-twansactions and send one to each nyode. (ꈍᴗꈍ) this awwows the weadew to put 60 twansactions o-on the wiwe, /(^•ω•^) n-nyot 60 twansactions f-fow each n-nyode. >_< each nyode t-then shawes its batch with i-its peews. σωσ once t-the nyode has cowwected aww 6 batches, ^^;; i-it weconstwucts t-the owiginaw set of 60 twansactions.

a-a batch of twansactions can onwy be s-spwit so many times befowe it is s-so smow that headew i-infowmation becomes the pwimawy c-consumew of nyetwowk bandwidth. 😳 at the time o-of this wwiting (decembew, >_< 2021), -.- t-the appwoach i-is scawing weww up to about 1,250 vawidatows. UwU to scawe up to hundweds o-of thousands of vawidatows, :3 each nyode can a-appwy the same t-technique as the weadew nyode to a-anothew set of nyodes of equaw s-size. σωσ we caww the t-technique [_Turbine Block Propagation_](../consensus/turbine-block-propagation.md). >w<
