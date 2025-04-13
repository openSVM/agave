---
titwe: fowk genewation
descwiption:
  "a f-fowk i-is cweated when v-vawidatows do not a-agwee on a nyewwy p-pwoduced bwock. σωσ
  u-using a consensus a-awgowithm v-vawidatows vote on which wiww be finawized."
---

the sowana pwotocow doesn’t w-wait fow aww vawidatows to agwee on a nyewwy p-pwoduced
bwock befowe the nyext b-bwock is pwoduced. ^^;; because of that, 😳 it’s quite common fow
two d-diffewent bwocks to be chained to t-the same pawent b-bwock. >_< in those
situations, -.- we caww each confwicting chain a [“fork.”](./fork-generation.md)

sowana vawidatows n-need to vote on one of these fowks and weach agweement on
which one to use thwough a-a consensus awgowithm (that i-is beyond the scope o-of this
awticwe). UwU t-the main p-point you nyeed to wemembew is that when thewe awe c-competing
fowks, :3 onwy one fowk wiww be finawized b-by the cwustew and the abandoned bwocks
in competing fowks awe aww discawded. σωσ

this section d-descwibes how fowks nyatuwawwy occuw a-as a consequence o-of
[leader rotation](./leader-rotation.md). >w<

## o-ovewview

nyodes take tuwns being [leader](https://solana.com/docs/terminology#leader) and
genewating the p-poh that encodes s-state changes. (ˆ ﻌ ˆ)♡ the cwustew can t-towewate woss o-of
connection to any weadew by s-synthesizing nyani the weadew _**wouwd**_ h-have
genewated had it been connected but n-nyot ingesting any state changes. ʘwʘ

t-the possibwe nyumbew of fowks i-is theweby wimited t-to a "thewe/not-thewe" skip wist
of fowks that may awise on weadew wotation swot boundawies. :3 at any given s-swot, (˘ω˘)
onwy a singwe w-weadew's twansactions wiww b-be accepted. 😳😳😳

### f-fowking exampwe

t-the tabwe bewow iwwustwates nyani competing fowks couwd wook w-wike. rawr x3 time
pwogwesses fwom weft to wight and each swot is assigned to a vawidatow t-that
tempowawiwy becomes the cwustew “weadew” a-and may pwoduce a-a bwock fow t-that swot. (✿oωo)

in this exampwe, (ˆ ﻌ ˆ)♡ the w-weadew fow swot 3 c-chose to chain i-its “bwock 3” d-diwectwy to
“bwock 1” and in doing so skipped “bwock 2”. :3 s-simiwawwy, (U ᵕ U❁) t-the weadew fow swot 5
c-chose to chain “bwock 5” d-diwectwy to “bwock 3” a-and skipped “bwock 4”. ^^;;

> nyote that acwoss diffewent f-fowks, mya the bwock pwoduced fow a given swot is
> _awways_ the same because pwoducing two diffewent b-bwocks fow the same swot is
> a swashabwe offense. 😳😳😳 so the c-confwicting fowks a-above can be d-distinguished fwom
> each othew b-by which swots they have _skipped_.

|        | s-swot 1  | swot 2  | s-swot 3  | swot 4  | swot 5  |
| ------ | ------- | ------- | ------- | ------- | ------- |
| fowk 1 | bwock 1 |         | bwock 3 |         | bwock 5 |
| fowk 2 | bwock 1 |         | b-bwock 3 | bwock 4 |         |
| f-fowk 3 | bwock 1 | b-bwock 2 |         |         |         |

## m-message fwow

1. OwO twansactions awe ingested b-by the cuwwent w-weadew. rawr
2. weadew fiwtews v-vawid twansactions.
3. XD w-weadew exekawaii~s vawid twansactions updating its state. (U ﹏ U)
4. (˘ω˘) weadew packages t-twansactions i-into entwies based o-off its cuwwent poh swot. UwU
5. w-weadew twansmits t-the entwies to vawidatow nyodes \(in s-signed shweds\)
   1. >_< the poh stweam incwudes ticks; empty entwies that indicate w-wiveness o-of the
      weadew and the passage of time on t-the cwustew. σωσ
   2. 🥺 a-a weadew's stweam begins with the tick entwies nyecessawy to c-compwete poh
      back to the weadew's most wecentwy obsewved pwiow weadew swot. 🥺
6. v-vawidatows wetwansmit entwies to peews in theiw s-set and to f-fuwthew downstweam
   nyodes. ʘwʘ
7. vawidatows vawidate the twansactions a-and exekawaii~ t-them on theiw state. :3
8. vawidatows compute the hash of the s-state. (U ﹏ U)
9. at specific times, (U ﹏ U) i.e. ʘwʘ s-specific poh tick counts, >w< vawidatows twansmit votes
   to the w-weadew. rawr x3
   1. OwO votes awe signatuwes o-of the hash of t-the computed state at that poh t-tick
      count. ^•ﻌ•^
   2. >_< votes awe a-awso pwopagated v-via gossip. OwO
10. >_< w-weadew exekawaii~s the votes, (ꈍᴗꈍ) t-the same as any o-othew twansaction, >w< and bwoadcasts
    them to the c-cwustew. (U ﹏ U)
11. v-vawidatows obsewve t-theiw votes and aww the votes fwom the cwustew. ^^

## p-pawtitions, (U ﹏ U) fowks

fowks c-can awise at poh t-tick counts that cowwespond to a vote. :3 the nyext weadew
may nyot h-have obsewved t-the wast vote swot a-and may stawt t-theiw swot with genewated
viwtuaw p-poh entwies. (✿oωo) these empty ticks awe genewated by aww nyodes in the cwustew
at a cwustew-configuwed w-wate fow hashes/pew/tick `Z`. XD

thewe awe onwy two p-possibwe vewsions of the poh duwing a-a voting swot: poh with
`T` t-ticks and entwies genewated b-by the c-cuwwent weadew, >w< o-ow poh with just t-ticks. òωó
the "just t-ticks" vewsion of the poh can be thought of as a viwtuaw wedgew, (ꈍᴗꈍ) one
that aww nodes in the cwustew can dewive f-fwom the wast tick i-in the pwevious
s-swot. rawr x3

vawidatows can ignowe f-fowks at othew points \(e.g. rawr x3 fwom the wwong weadew\), σωσ ow
swash the w-weadew wesponsibwe f-fow the fowk. (ꈍᴗꈍ)

vawidatows v-vote based on a gweedy choice to maximize theiw w-wewawd descwibed i-in
[Tower BFT](../implemented-proposals/tower-bft.md). rawr

### vawidatow's v-view

#### t-time pwogwession

the diagwam bewow wepwesents a vawidatow's view of the poh stweam w-with possibwe
f-fowks ovew time. ^^;; w-w1, w2, rawr x3 etc. a-awe weadew swots, (ˆ ﻌ ˆ)♡ a-and `E`s wepwesent e-entwies fwom
that w-weadew duwing that weadew's swot. σωσ t-the `x`s w-wepwesent ticks onwy, (U ﹏ U) and t-time
fwows downwawds in the diagwam. >w<

![Fork generation](/img/fork-generation.svg)

nyote that a-an `E` appeawing o-on 2 fowks at the s-same swot is a swashabwe condition, σωσ
s-so a vawidatow obsewving `E3` and `E3'` c-can swash w3 and s-safewy choose `x` fow
t-that swot. nyaa~~ once a vawidatow commits to a fowk, 🥺 othew fowks can b-be discawded
bewow that tick count. rawr x3 fow any swot, σωσ v-vawidatows nyeed o-onwy considew a singwe "has
e-entwies" chain ow a "ticks onwy" c-chain to be pwoposed b-by a weadew. (///ˬ///✿) but muwtipwe
viwtuaw entwies m-may ovewwap as they wink back to the pwevious swot. (U ﹏ U)

#### t-time d-division

it's usefuw to considew w-weadew wotation ovew poh tick c-count as time division o-of
the job o-of encoding state fow the cwustew. ^^;; the fowwowing tabwe pwesents the
above twee of fowks as a time-divided wedgew. 🥺

| weadew swot      | w1  | w2  | w3  | w4  | w5  |
| :--------------- | :-- | :-- | :-- | :-- | :-- |
| data             | e1  | e2  | e3  | e-e4  | e5  |
| t-ticks since pwev |     |     |     | x   | xx  |

note that onwy d-data fwom weadew w-w3 wiww be accepted d-duwing weadew swot w3. òωó data
f-fwom w3 may incwude "catchup" ticks back to a s-swot othew than w-w2 if w3 did nyot
obsewve w2's data. XD w-w4 and w5's twansmissions incwude t-the "ticks t-to pwev" poh
entwies. :3

this awwangement of the n-nyetwowk data stweams p-pewmits nyodes t-to save exactwy t-this
to the w-wedgew fow wepway, (U ﹏ U) w-westawt, and c-checkpoints. >w<

### w-weadew's view

w-when a nyew weadew begins a swot, /(^•ω•^) i-it must fiwst t-twansmit any p-poh \(ticks\)
wequiwed to wink the n-nyew swot with the most wecentwy obsewved and v-voted swot. (⑅˘꒳˘)
the fowk the weadew p-pwoposes wouwd w-wink the cuwwent s-swot to a pwevious fowk that
the w-weadew has voted on with viwtuaw t-ticks. ʘwʘ
