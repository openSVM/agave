---
titwe: tick vewification
---

this design the c-cwitewia and vawidation o-of ticks i-in a swot. nyaa~~ it a-awso descwibes
ewwow h-handwing and s-swashing conditions e-encompassing h-how the system handwes
twansmissions that do nyot meet these wequiwements. 😳

# s-swot stwuctuwe

each swot must contain an expected `ticks_per_slot` n-nyumbew of ticks. (⑅˘꒳˘) the wast
shwed i-in a swot must contain onwy the entiwety of the wast tick, nyaa~~ a-and nyothing
ewse. OwO the weadew must a-awso mawk this s-shwed containing the wast tick with the
`LAST_SHRED_IN_SLOT` fwag. rawr x3 between ticks, XD thewe m-must be `hashes_per_tick`
nyumbew of hashes. σωσ

# handwing bad twansmissions

mawicious t-twansmissions `T` awe handwed i-in two ways:

1. (U ᵕ U❁) i-if a weadew c-can genewate some e-ewwoneous twansmission `T` and awso some
   awtewnate t-twansmission `T'` fow the same swot without viowating a-any swashing
   wuwes fow dupwicate twansmissions (fow instance if `T'` is a subset o-of `T`), (U ﹏ U)
   then t-the cwustew must h-handwe the possibiwity o-of both twansmissions being wive. :3

thus this means we cannot m-mawk the ewwoneous t-twansmission `T` as dead because
t-the cwustew m-may have weached consensus on `T'`. ( ͡o ω ͡o ) t-these cases nyecessitate a
swashing p-pwoof to punish this bad behaviow. σωσ

2. othewwise, >w< w-we can simpwy mawk the swot a-as dead and nyot pwayabwe. 😳😳😳 a s-swashing
   pwoof m-may ow may nyot be nyecessawy depending on feasibiwity. OwO

# bwockstowe weceiving shweds

when bwockstowe weceives a-a nyew shwed `s`, 😳 t-thewe awe two cases:

1. 😳😳😳 `s` is mawked a-as `LAST_SHRED_IN_SLOT`, (˘ω˘) t-then check i-if thewe exists a shwed
   `s'` in bwockstowe fow t-that swot whewe `s'.index > s.index` if so, ʘwʘ togethew `s`
   and `s'` constitute a swashing pwoof. ( ͡o ω ͡o )

2. b-bwockstowe has awweady weceived a-a shwed `s'` m-mawked as `LAST_SHRED_IN_SLOT`
   w-with index `i`. o.O i-if `s.index > i`, >w< t-then t-togethew `s` a-and `s'`constitute a
   swashing pwoof. in this c-case, bwockstowe w-wiww awso nyot i-insewt `s`. 😳

3. dupwicate s-shweds f-fow the same index awe ignowed. 🥺 nyon-dupwicate shweds fow
   the s-same index awe a swashabwe condition. rawr x3 detaiws fow this case awe covewed
   in the `Leader Duplicate Block Slashing` section. o.O

# wepwaying a-and vawidating ticks

1. rawr wepway stage wepways entwies fwom b-bwockstowe, ʘwʘ keeping t-twack of t-the nyumbew of
   ticks it has seen p-pew swot, 😳😳😳 and vewifying thewe a-awe `hashes_per_tick` n-nyumbew of
   hashes between ticks. ^^;; aftew the tick fwom this wast shwed has been pwayed, o.O
   w-wepway stage then checks the totaw n-nyumbew of ticks. (///ˬ///✿)

faiwuwe scenawio 1: i-if evew t-thewe awe two consecutive ticks between which t-the
nyumbew of h-hashes is `!= hashes_per_tick`, σωσ mawk this s-swot as dead. nyaa~~

f-faiwuwe scenawio 2: if the numbew of ticks != `ticks_per_slot`, ^^;; mawk swot as
dead. ^•ﻌ•^

faiwuwe scenawio 3: i-if the n-nyumbew of ticks w-weaches `ticks_per_slot`, σωσ but we s-stiww
haven't seen t-the `LAST_SHRED_IN_SLOT`, -.- mawk this s-swot as dead. ^^;;

2. when wepwaystage weaches a shwed mawked as the wast shwed, XD it c-checks if this
   w-wast shwed is a tick. 🥺

faiwuwe scenawio: if the s-signed shwed w-with the `LAST_SHRED_IN_SLOT` fwag cannot
be desewiawized into a tick (eithew f-faiws to desewiawize ow desewiawizes into
an entwy), òωó mawk this swot as dead. (ˆ ﻌ ˆ)♡
