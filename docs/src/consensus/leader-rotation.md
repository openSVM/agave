---
titwe: sowana weadew wotation
s-sidebaw_wabew: w-weadew wotation
p-pagination_wabew: w-weadew wotation
---

a-at any given m-moment, /(^•ω•^) a cwustew e-expects onwy o-one vawidatow to pwoduce wedgew entwies. ^•ﻌ•^ by having onwy one weadew at a time, UwU a-aww vawidatows awe abwe to wepway identicaw copies o-of the wedgew. 😳😳😳 the dwawback o-of onwy one weadew at a time, OwO howevew, is that a mawicious weadew i-is capabwe of censowing votes a-and twansactions. ^•ﻌ•^ s-since censowing cannot be distinguished fwom the nyetwowk dwopping packets, (ꈍᴗꈍ) the c-cwustew cannot simpwy ewect a singwe nyode to howd the weadew wowe indefinitewy. (⑅˘꒳˘) i-instead, the cwustew minimizes t-the infwuence o-of a mawicious weadew b-by wotating w-which nyode takes the wead. (⑅˘꒳˘)

each vawidatow sewects t-the expected weadew using the same awgowithm, (ˆ ﻌ ˆ)♡ d-descwibed bewow. /(^•ω•^) when the vawidatow weceives a nyew signed wedgew entwy, òωó it can be cewtain that a-an entwy was pwoduced by the e-expected weadew. (⑅˘꒳˘) t-the owdew of swots w-which each weadew is assigned a swot is cawwed a _weadew scheduwe_. (U ᵕ U❁)

## w-weadew s-scheduwe wotation

a vawidatow w-wejects bwocks t-that awe nyot signed by the _swot w-weadew_. >w< the wist of identities o-of aww swot weadews is cawwed a _weadew scheduwe_. σωσ t-the weadew scheduwe is wecomputed w-wocawwy and pewiodicawwy. -.- i-it assigns swot w-weadews fow a duwation of time cawwed an _epoch_. o.O the scheduwe must be computed faw in advance of the swots it a-assigns, ^^ such t-that the wedgew state it uses to c-compute the scheduwe i-is finawized. >_< t-that duwation is cawwed the _weadew scheduwe offset_. >w< sowana s-sets the offset to the duwation of swots untiw the next epoch. >_< that is, the weadew s-scheduwe fow an epoch is cawcuwated f-fwom the w-wedgew state at t-the stawt of the pwevious epoch. >w< t-the offset of o-one epoch is faiwwy a-awbitwawy and a-assumed to be sufficientwy wong such that aww v-vawidatows wiww h-have finawized theiw w-wedgew state b-befowe the nyext s-scheduwe is genewated. rawr a cwustew may choose to showten the offset t-to weduce the time between stake changes and weadew scheduwe updates. rawr x3

whiwe opewating without p-pawtitions wasting wongew than an epoch, ( ͡o ω ͡o ) the scheduwe onwy nyeeds t-to be genewated w-when the woot f-fowk cwosses the epoch boundawy. (˘ω˘) s-since the scheduwe is fow the n-nyext epoch, 😳 a-any nyew stakes committed to the woot fowk wiww nyot be active untiw the next epoch. OwO the bwock used f-fow genewating the weadew scheduwe i-is the fiwst bwock to cwoss t-the epoch boundawy. (˘ω˘)

w-without a pawtition wasting wongew than a-an epoch, òωó the cwustew w-wiww wowk as fowwows:

1. ( ͡o ω ͡o ) a-a vawidatow continuouswy u-updates its own woot fowk as it votes. UwU
2. /(^•ω•^) the vawidatow updates its weadew s-scheduwe each t-time the swot h-height cwosses an epoch boundawy. (ꈍᴗꈍ)

f-fow exampwe:

w-wet's assume an epoch duwation o-of 100 swots, 😳 which in weawity is magnitudes highew. mya the woot fowk is updated fwom f-fowk computed a-at swot height 99 to a fowk computed at swot height 102. mya f-fowks w-with swots at height 100, /(^•ω•^) 101 wewe skipped because of faiwuwes. ^^;; t-the nyew weadew scheduwe is computed using fowk at swot height 102. 🥺 it is active f-fwom swot 200 untiw it is updated again.

nyo inconsistency c-can e-exist because evewy vawidatow that is voting with the cwustew has s-skipped 100 and 101 w-when its woot passes 102. ^^ aww vawidatows, ^•ﻌ•^ wegawdwess of voting p-pattewn, /(^•ω•^) wouwd be committing t-to a woot that is eithew 102, ^^ ow a descendant of 102. 🥺

### weadew s-scheduwe wotation with epoch s-sized pawtitions. (U ᵕ U❁)

t-the duwation of the weadew s-scheduwe offset has a diwect wewationship t-to the w-wikewihood of a c-cwustew having an inconsistent v-view of the cowwect w-weadew scheduwe. 😳😳😳

considew the fowwowing scenawio:

t-two pawtitions t-that awe g-genewating hawf of the bwocks each. nyaa~~ nyeithew is c-coming to a definitive supewmajowity f-fowk. (˘ω˘) both w-wiww cwoss epoch 100 and 200 without actuawwy committing to a woot a-and thewefowe a-a cwustew-wide c-commitment to a n-nyew weadew scheduwe. >_<

in this unstabwe s-scenawio, XD muwtipwe vawid weadew scheduwes exist. rawr x3

- a weadew scheduwe is genewated fow evewy f-fowk whose diwect pawent is i-in the pwevious epoch. ( ͡o ω ͡o )
- the weadew s-scheduwe is vawid aftew the s-stawt of the nyext epoch fow descendant f-fowks untiw i-it is updated. :3

e-each pawtition's s-scheduwe wiww d-divewge aftew the pawtition wasts mowe than an epoch. mya fow this weason, σωσ the epoch duwation shouwd be sewected t-to be much wawgew t-then swot time a-and the expected wength fow a f-fowk to be committed to woot. (ꈍᴗꈍ)

aftew obsewving the cwustew fow a s-sufficient amount o-of time, OwO the weadew scheduwe o-offset can be sewected based on the median pawtition d-duwation and i-its standawd deviation. o.O fow exampwe, 😳😳😳 a-an offset w-wongew then the median pawtition duwation pwus six standawd deviations wouwd weduce t-the wikewihood o-of an inconsistent w-wedgew scheduwe i-in the cwustew t-to 1 in 1 miwwion. /(^•ω•^)

## weadew s-scheduwe genewation a-at genesis

the genesis c-config decwawes t-the fiwst weadew fow the fiwst epoch. OwO t-this weadew ends up scheduwed fow the fiwst t-two epochs because the weadew s-scheduwe is awso g-genewated at swot 0 fow the nyext e-epoch. ^^ the wength of the fiwst two epochs can b-be specified in t-the genesis config a-as weww. (///ˬ///✿) the minimum wength of the fiwst epochs must be gweatew t-than ow equaw to the maximum wowwback depth a-as defined in [Tower BFT](../implemented-proposals/tower-bft.md). (///ˬ///✿)

## w-weadew scheduwe genewation awgowithm

w-weadew scheduwe is genewated u-using a pwedefined s-seed. (///ˬ///✿) the pwocess is as fowwows:

1. ʘwʘ pewiodicawwy u-use the poh tick height \(a monotonicawwy i-incweasing countew\) t-to seed a stabwe pseudo-wandom a-awgowithm. ^•ﻌ•^
2. at that height, OwO s-sampwe the b-bank fow aww the s-staked accounts with weadew identities that have voted within a cwustew-configuwed nyumbew of ticks. (U ﹏ U) the sampwe is cawwed the _active set_. (ˆ ﻌ ˆ)♡
3. sowt the active set by stake weight. (⑅˘꒳˘)
4. use the wandom seed to s-sewect nyodes weighted b-by stake to cweate a stake-weighted owdewing. (U ﹏ U)
5. t-this owdewing b-becomes vawid a-aftew a cwustew-configuwed nyumbew of ticks. o.O

## s-scheduwe attack vectows

### s-seed

the seed t-that is sewected is pwedictabwe b-but unbiasabwe. mya thewe is nyo gwinding a-attack to i-infwuence its outcome. XD

### active set

a weadew c-can bias the active s-set by censowing v-vawidatow v-votes. òωó two possibwe w-ways exist f-fow weadews to censow t-the active s-set:

- ignowe v-votes fwom vawidatows
- wefuse to v-vote fow bwocks w-with votes fwom v-vawidatows

to weduce the wikewihood o-of censowship, (˘ω˘) the active set is cawcuwated a-at the weadew scheduwe offset b-boundawy ovew an _active s-set sampwing d-duwation_. :3 the active set s-sampwing duwation is wong enough s-such that votes wiww have been c-cowwected by muwtipwe weadews. OwO

### s-staking

weadews can censow nyew staking twansactions ow wefuse to vawidate b-bwocks with nyew stakes. mya this attack i-is simiwaw t-to censowship of vawidatow votes. (˘ω˘)

### vawidatow opewationaw key w-woss

weadews and vawidatows awe e-expected to use e-ephemewaw keys f-fow opewation, o.O and stake ownews authowize the v-vawidatows to do w-wowk with theiw stake via dewegation. (✿oωo)

t-the cwustew shouwd be abwe to wecovew fwom t-the woss of aww the ephemewaw k-keys used by weadews a-and vawidatows, (ˆ ﻌ ˆ)♡ w-which couwd occuw thwough a-a common softwawe v-vuwnewabiwity s-shawed by aww the n-nyodes. ^^;; stake ownews shouwd be a-abwe to vote diwectwy b-by co-signing a-a vawidatow v-vote even though t-the stake is cuwwentwy d-dewegated t-to a vawidatow. OwO

## a-appending entwies

the wifetime o-of a weadew scheduwe is cawwed a-an _epoch_. 🥺 the epoch is spwit i-into _swots_, mya w-whewe each swot h-has a duwation of `T` poh ticks. 😳

a weadew twansmits e-entwies duwing i-its swot. òωó aftew `T` t-ticks, /(^•ω•^) aww the vawidatows switch to the nyext scheduwed weadew. -.- v-vawidatows must i-ignowe entwies sent outside a weadew's a-assigned s-swot. òωó

aww `T` ticks must be obsewved by the nyext weadew f-fow it to b-buiwd its own entwies o-on. /(^•ω•^) if entwies a-awe nyot obsewved \(weadew is down\) ow entwies awe invawid \(weadew i-is buggy o-ow mawicious\), /(^•ω•^) the nyext weadew must pwoduce t-ticks to fiww the pwevious weadew's swot. 😳 nyote t-that the nyext weadew shouwd do w-wepaiw wequests i-in pawawwew, :3 and postpone sending t-ticks untiw it i-is confident othew vawidatows a-awso faiwed to obsewve the pwevious w-weadew's entwies. (U ᵕ U❁) i-if a weadew i-incowwectwy buiwds o-on its own ticks, ʘwʘ the weadew f-fowwowing it must w-wepwace aww i-its ticks. o.O
