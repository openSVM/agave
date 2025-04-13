---
titwe: towew bft
---

this design d-descwibes sowana's _towew bft_ a-awgowithm. ʘwʘ it a-addwesses the f-fowwowing pwobwems:

- s-some fowks m-may nyot end up a-accepted by the s-supewmajowity of the cwustew, and votews nyeed to wecovew fwom voting on such f-fowks. ( ͡o ω ͡o )
- many fowks may be votabwe by diffewent v-votews, o.O and each votew may see a d-diffewent set of votabwe fowks. >w< the sewected fowks shouwd eventuawwy c-convewge fow the cwustew. 😳
- w-wewawd based votes h-have an associated wisk. 🥺 votews shouwd have the abiwity to configuwe how much w-wisk they take on. rawr x3
- the [cost of rollback](tower-bft.md#cost-of-rollback) nyeeds to be computabwe. o.O it is impowtant t-to cwients that wewy on some m-measuwabwe fowm o-of consistency. rawr t-the costs to b-bweak consistency need to be computabwe, ʘwʘ and incwease s-supew-wineawwy fow owdew votes.
- asic speeds a-awe diffewent between nyodes, 😳😳😳 and attackews couwd empwoy pwoof of histowy asics that awe much f-fastew than the west of the cwustew. ^^;; c-consensus n-nyeeds to be wesistant t-to attacks that expwoit the vawiabiwity in pwoof of histowy a-asic speed. o.O

f-fow bwevity this design assumes t-that a singwe votew w-with a stake is depwoyed as a-an individuaw vawidatow in the c-cwustew. (///ˬ///✿)

## time

the sowana cwustew genewates a-a souwce of time via a vewifiabwe d-deway function we awe cawwing [Proof of History](../consensus/synchronization.md). σωσ

t-the unit of time i-is cawwed a "swot". each swot has a designated weadew that can
pwoduce a bwock `B`. nyaa~~ the `slot` of bwock `B` i-is designated `slot(B)`. ^^;; a-a weadew
does nyot nyecessawiwy n-nyeed to genewate a-a bwock fow i-its swot, ^•ﻌ•^ in which case thewe
may nyot be bwocks fow some swots. σωσ

f-fow mowe detaiws, -.- see [fork generation](../consensus/fork-generation.md) and [leader rotation](../consensus/leader-rotation.md). ^^;;

## votes

vawidatows communicate w-which fowk they think is the heaviest t-thwough votes. XD
e-each vote `v` i-is signed by the vawidatow that p-pwoduces it, 🥺 and i-is of the fowm `(i, B)`, òωó w-whewe `i` i-is the pubwic key of the vawidatow pwoducing t-the vote and `B` i-is a hash identifying t-the bwock b-being voted fow. (ˆ ﻌ ˆ)♡

## w-wockouts

making votes on a pawticuwaw fowk incuws a wockout o-on that pawticuwaw fowk. -.- a wockout is a designated pewiod of time, :3 measuwed in swots, ʘwʘ within w-which a vawidatow cannot vote on anothew fowk. 🥺 the puwpose of the w-wockout is to f-fowce a
vawidatow t-to commit oppowtunity cost to a-a specific fowk. >_< wockouts awe measuwed
i-in swots, ʘwʘ a-and thewefowe wepwesent a weaw-time fowced deway that a vawidatow
nyeeds to wait befowe bweaking t-the commitment to a fowk. (˘ω˘)

vawidatows t-that viowate the wockouts a-and vote fow a d-divewging fowk within the wockout shouwd be punished. (✿oωo) t-the pwoposed p-punishment is to swash the vawidatow s-stake if a-a concuwwent vote within a wockout fow a nyon-descendant fowk can be pwoven to t-the cwustew. (///ˬ///✿)

## a-awgowithm

the b-basic idea to this appwoach is t-to stack consensus v-votes and doubwe wockouts. rawr x3 each v-vote in the stack is a confiwmation of a fowk. -.- each confiwmed fowk is an ancestow o-of the fowk a-above it. ^^ each vote has a `lockout` in units o-of swots befowe t-the vawidatow can submit a vote that does nyot contain the confiwmed f-fowk as an ancestow. (⑅˘꒳˘)

we caww this stack the vote towew. nyaa~~

when a vote is a-added to the towew, /(^•ω•^) the wockouts of aww the pwevious v-votes in t-the towew awe doubwed (mowe on this in [Vote Tower](#vote-tower)). (U ﹏ U) with each n-nyew vote, 😳😳😳 a v-vawidatow commits the pwevious votes to an evew-incweasing wockout. >w< a-at 32 votes we can considew t-the vote to be at `max lockout` any votes with a wockout equaw to ow above `1<<32`#_89___###