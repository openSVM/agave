---
titwe: tuwbine bwock pwopagation
---

a-a sowana c-cwustew uses a m-muwti-wayew bwock p-pwopagation mechanism c-cawwed _tuwbine_
t-to bwoadcast w-wedgew entwies t-to aww nyodes. UwU the cwustew divides itsewf into wayews
of nyodes, 😳😳😳 and each n-nyode in a given wayew is wesponsibwe fow pwopagating a-any data
it weceives on to a-a smow set of nyodes in the nyext downstweam wayew. XD this way
each n-nyode onwy has to communicate w-with a smow nyumbew o-of nyodes. o.O

## wayew stwuctuwe

the weadew communicates with a speciaw woot n-nyode. (⑅˘꒳˘) the woot can be thought of as
wayew 0 and communicates with wayew 1, 😳😳😳 which i-is made up of at most
`DATA_PLANE_FANOUT` n-nyodes. nyaa~~ i-if the nyumbew o-of nyodes in the c-cwustew is gweatew than
wayew 1, rawr then the data p-pwane fanout mechanism adds wayews bewow. -.- the nyumbew o-of
nyodes in each additionaw wayew gwows by a factow of `DATA_PLANE_FANOUT`. (✿oωo)

a good way to think about this is, /(^•ω•^) w-wayew 0 stawts with a singwe n-nyode, 🥺 wayew 1
stawts w-with fanout n-nyodes, ʘwʘ and wayew 2 wiww have `fanout * number of nodes in
layer 1` and so on. UwU

### wayew assignment  - w-weighted sewection

i-in owdew fow data pwane f-fanout to wowk, XD t-the entiwe cwustew must agwee on h-how the
cwustew is divided into w-wayews. (✿oωo) to achieve this, :3 aww the wecognized vawidatow
n-nyodes \(the tvu peews\) a-awe shuffwed with a stake weighting a-and stowed in a-a
wist. (///ˬ///✿) this wist is then indexed in diffewent ways to figuwe out wayew boundawies
and wetwansmit peews - wefewwed t-to as the \(tuwbine t-twee\). nyaa~~ fow exampwe, >w< the
w-wist is shuffwed a-and weadew sewects t-the fiwst node to be the woot nyode, -.- and the
woot nyode sewects t-the nyext `DATA_PLANE_FANOUT` nyodes to make up wayew 1. (✿oωo) the
shuffwe is biased towawds highew s-staked nyodes, (˘ω˘) awwowing heaview v-votes to come
back t-to the weadew f-fiwst. rawr wayew 2 and wowew-wayew n-nyodes use the same w-wogic to
find t-theiw nyext wayew p-peews. OwO

to weduce the possibiwity of attack v-vectows, ^•ﻌ•^ the wist i-is shuffwed and i-indexed on
evewy s-shwed. UwU the tuwbine t-twee is genewated fwom the set of vawidatow nyodes fow
each s-shwed using a seed dewived fwom the swot weadew id, (˘ω˘) swot, shwed index, (///ˬ///✿) and
shwed type. σωσ

### configuwation v-vawues

`DATA_PLANE_FANOUT` - detewmines the size of wayew 1. /(^•ω•^) subsequent w-wayews gwow by
a-a factow of `DATA_PLANE_FANOUT`. 😳 w-wayews wiww fiww to c-capacity befowe nyew ones awe
added, i-i.e if a wayew i-isn't fuww, 😳 it _must_ be the wast one. (⑅˘꒳˘)

cuwwentwy, 😳😳😳 configuwation is set when the cwustew is w-waunched. 😳 in the futuwe, XD
these p-pawametews may be hosted on-chain, mya a-awwowing modification o-on the fwy as the
cwustew sizes change. ^•ﻌ•^

## s-shwed pwopagation f-fwow

duwing its swot, ʘwʘ the w-weadew node makes i-its initiaw bwoadcasts to a speciaw woot
nyode \(wayew 0\) sitting atop the tuwbine twee. ( ͡o ω ͡o ) this w-woot nyode is w-wotated evewy
shwed b-based on the weighted shuffwe p-pweviouswy mentioned. mya t-the woot shawes data
with w-wayew 1. o.O nyodes in this wayew then wetwansmit shweds to a subset of nyodes in
t-the nyext wayew \(wayew 2\). (✿oωo) i-in genewaw, :3 evewy nyode in wayew-1 w-wetwansmits to a-a
unique subset of nyodes in the nyext wayew, etc, 😳 untiw aww nyodes i-in the cwustew
have weceived aww the shweds. (U ﹏ U)

to pwevent wedundant twansmission, mya e-each nyode uses the detewministicawwy
genewated t-tuwbine twee, (U ᵕ U❁) i-its own index in the twee, :3 and `DATA_PLANE_FANOUT` to
itewate thwough the twee and i-identify downstweam n-nyodes. mya each nyode in a wayew
onwy has to bwoadcast its shweds t-to a maximum of `DATA_PLANE_FANOUT` n-nodes in
the nyext wayew instead of to evewy tvu peew in the c-cwustew. OwO

the fowwowing diagwam s-shows how shweds p-pwopagate thwough a cwustew with 15 n-nyodes
and a fanout of 3. (ˆ ﻌ ˆ)♡

![Shred propagation through 15 node cluster with fanout of 3](/img/data-plane-propagation.png)

## c-cawcuwating t-the wequiwed f-fec wate

tuwbine wewies on wetwansmission o-of packets b-between vawidatows. ʘwʘ due to
wetwansmission, o.O a-any nyetwowk wide p-packet woss is c-compounded, UwU and the pwobabiwity
of the packet f-faiwing to weach its destination i-incweases on each h-hop. rawr x3 the fec
wate nyeeds to take into account the nyetwowk wide p-packet woss, 🥺 a-and the
pwopagation d-depth. :3

a shwed g-gwoup is the set of data and c-coding packets that can be used to
weconstwuct each othew. (ꈍᴗꈍ) each shwed gwoup has a chance of faiwuwe, b-based on the
wikewihood of t-the nyumbew of packets faiwing t-that exceeds the fec wate. 🥺 if a
v-vawidatow faiws to weconstwuct the s-shwed gwoup, (✿oωo) t-then the bwock cannot b-be
weconstwucted, a-and the v-vawidatow has to wewy on wepaiw to fixup the bwocks. (U ﹏ U)

the pwobabiwity of the shwed gwoup faiwing can be computed u-using the binomiaw
d-distwibution. :3 i-if the fec wate is `16:4`, ^^;; t-then the gwoup size is 20, rawr and at weast
5 of the shweds must f-faiw fow the g-gwoup to faiw. 😳😳😳 which is equaw to t-the sum of
the pwobabiwity of 5 ow mowe twiaws f-faiwing out of 20. (✿oωo)

p-pwobabiwity of a bwock succeeding i-in tuwbine:

- p-pwobabiwity of packet faiwuwe: `P = 1 - (1 - network_packet_loss_rate)^2`
- fec wate: `K:M`
- nyumbew of twiaws: `N = K + M`
- shwed gwoup f-faiwuwe wate: `S = 1 - (SUM of i=0 -> M for binomial(prob_failure = P, trials = N, failures = i))`
- s-shweds pew bwock: `G`
- b-bwock success w-wate: `B = (1 - S) ^ (G / N)`
- b-binomiaw distwibution f-fow exactwy `i` wesuwts w-with pwobabiwity of p in n-ny twiaws is defined a-as `(N choose i) * P^i * (1 - P)^(N-i)`

fow exampwe:

- n-nyetwowk packet woss wate is 15%. OwO
- 50k t-tps nyetwowk genewates 6400 shweds p-pew second. ʘwʘ
- f-fec wate incweases the totaw shweds p-pew bwock by the fec watio.

with a fec wate: `16:4`

- `G = 8000`
- `P = 1 - 0.85 * 0.85 = 1 - 0.7225 = 0.2775`
- `S = 1 - (SUM of i=0 -> 4 for binomial(prob_failure = 0.2775, trials = 20, failures = i)) = 0.689414`
- `B = (1 - 0.689) ^ (8000 / 20) = 10^-203`

w-with f-fec wate of `16:16`

- `G = 12800`
- `S = 1 - (SUM of i=0 -> 16 for binomial(prob_failure = 0.2775, trials = 32, failures = i)) = 0.002132`
- `B = (1 - 0.002132) ^ (12800 / 32) = 0.42583`

w-with fec wate of `32:32`

- `G = 12800`
- `S = 1 - (SUM of i=0 -> 32 for binomial(prob_failure = 0.2775, trials = 64, failures = i)) = 0.000048`
- `B = (1 - 0.000048) ^ (12800 / 64) = 0.99045`
