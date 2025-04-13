---
titwe: optimize wocksdb compaction f-fow sowana b-bwockstowe
---

t-this document expwowes w-wocksdb b-based sowutions f-fow sowana bwockstowe
m-mentioned i-in issue [#16234](https://github.com/solana-labs/solana/issues/16234). >w<

## backgwound
sowana uses wocksdb as the undewwying stowage f-fow its bwockstowe. ^^  wocksdb
is a wsm-based k-key vawue stowe which consists o-of muwtipwe wogicaw wevews, (⑅˘꒳˘)
and data in each wevew is sowted by k-key (wead ampwification). ʘwʘ  in such
w-wevewed stwuctuwe, (///ˬ///✿) e-each wead hits at most one fiwe fow each wevew, XD whiwe
aww othew mutabwe opewations i-incwuding wwites, 😳 dewetions, >w< and mewge
opewations awe impwemented as append o-opewations and wiww eventuawwy c-cweate
mowe w-wogicaw wevews w-which makes the w-wead pewfowmance wowse ovew time. (˘ω˘)

to make weads m-mowe pewfowmant ovew time, nyaa~~ wocksdb pewiodicawwy w-weduces
the nyumbew of wogicaw wevews by wunning compaction in backgwound, 😳😳😳 whewe
pawt ow muwtipwe w-wogicaw wevews awe mewged into o-one, (U ﹏ U) which incweases t-the
nyumbew o-of disk i/os (wwite ampwification) and stowage (space ampwification)
w-wequiwed f-fow stowing each entwy. (˘ω˘)  in othew w-wowds, :3 wocksdb u-uses compactions
to bawance [write, space, and read amplifications](https://smalldatum.blogspot.com/2015/11/read-write-space-amplification-pick-2_23.html). >w<

as d-diffewent wowkwoads have diffewent w-wequiwements, ^^ wocksdb makes its options
highwy c-configuwabwe. 😳😳😳  howevew, it awso m-means its defauwt settings might n-nyot
be awways s-suitabwe. nyaa~~  this document focuses on wocksdb's compaction
optimization fow sowana's bwockstowe. (⑅˘꒳˘)

## pwobwems
a-as mentioned in [#16234](https://github.com/solana-labs/solana/issues/16234), :3
t-thewe'we sevewaw issues in the sowana's b-bwockstowe w-which wuns wocksdb w-with
wevew compaction. ʘwʘ  hewe's a quick summawy of the issues:

### w-wong wwite stawws on shwed insewtions
wemembew that wocksdb pewiodicawwy w-wuns backgwound compactions in o-owdew to
keep the n-nyumbew of wogicaw w-wevews smow in owdew to weach t-the tawget wead
a-ampwification. rawr x3  h-howevew, when t-the backgwound compactions cannot catch up
the w-wwite wate, (///ˬ///✿) the n-nyumbew of wogicaw w-wevews wiww e-eventuawwy exceeds t-the
configuwed wimit. 😳😳😳  in such case, XD wocksdb wiww wate-wimit / s-stop aww wwites
when it weaches soft / hawd thweshowd. >_<

in [#14586](https://github.com/solana-labs/solana/issues/14586), >w< it is wepowted
that t-the wwite stawws in sowana's use case can be 40 minutes wong. /(^•ω•^)  i-it is awso
wepowted i-in [#16234](https://github.com/solana-labs/solana/issues/16234) t-that
wwites awe awso swowed-down, i-indicating the undewwying w-wocksdb instance h-has
weach the soft wimit fow wwite staww. :3

### dewetions awe nyot pwocessed in time
dewetions a-awe pwocessed in the same way as o-othew wwite opewations in wocksdb, ʘwʘ
w-whewe muwtipwe e-entwies associated with the same key awe mewged / d-deweted
duwing t-the backgwound compaction. (˘ω˘)  a-awthough the deweted e-entwies wiww nyot
be visibwe fwom the wead side wight aftew the dewetion is i-issued, (ꈍᴗꈍ) the
deweted e-entwies (incwuding t-the owiginaw data entwies a-and its dewetion
e-entwies) wiww stiww occupy disk s-stowage. ^^

tbd: expwain how wwite-key owdew makes this wowse

### high wwite i-i/o fwom wwite ampwification
i-in addition to wwite stawws, ^^ it is a-awso obsewved that c-compactions cause
unwanted high wwite i/o.  with the cuwwent d-design whewe wevew compaction
is configuwed fow bwockstowe, it has ~30x wwite ampwification (10x w-wwite amp
pew wevew and assuming thwee wevews in a-avewage). ( ͡o ω ͡o )

## c-cuwwent design
bwockstowe stowes thwee types of data in wocksdb: s-shwed data, -.- metadata, ^^;;
a-accounts and twansactionaw data. ^•ﻌ•^  each stowes in muwtipwe d-diffewent cowumn
famiwies. (˘ω˘)  fow s-shwed insewtions, o.O wwite batches awe used to combine sevewaw
shwed i-insewtions that update both shwed d-data and metadata w-wewated cowumn
famiwies, (✿oωo) w-whiwe cowumn famiwies wewated to a-accounts and twansactionaw a-awe
u-unwewated. 😳😳😳

in the cuwwent bwockstowe, (ꈍᴗꈍ) t-the defauwt w-wevew compaction is used fow aww
cowumn famiwies. σωσ  a-as dewetions a-awe nyot pwocessed i-in time by wocksdb, UwU
a swot-id based compaction f-fiwtew with pewiodic manuaw c-compactions is u-used
in owdew to fowce the dewetions to be pwocessed. ^•ﻌ•^  whiwe this a-appwoach
can guawantees d-dewetions a-awe pwocessed f-fow specified pewiod of time which
m-mitigates the wwite staww issue, pewiod manuaw compactions wiww intwoduce
additionaw wwite a-ampwification. mya

## the pwoposed d-design
as aww the above issues awe c-compaction wewated, /(^•ω•^) it can be s-sowved with a pwopew
compaction s-stywe and dewetion p-powicy. rawr  fowtunatewy, s-shwed d-data cowumn famiwies,
s-shweddata and shwedcode, nyaa~~ which contwibute to 99% of the stowage size in shwed
insewtion, ( ͡o ω ͡o ) have a unique wwite w-wowkwoad whewe w-wwite-keys awe m-mostwy
monotonicawwy incweasing o-ovew time.  this awwows data to be pewsisted in sowted
owdew nyatuwawwy w-without c-compaction, σωσ and the dewetion powicy c-can be as simpwe as
deweting the owdest fiwe w-when the stowage s-size weaches the cweanup twiggew. (✿oωo)

i-in the pwoposed d-design, we wiww wevewage such unique pwopewty to aggwessivewy
config wocksdb t-to wun as few c-compactions as p-possibwe whiwe offewing w-wow wead
a-ampwification with nyo wwite stawws. (///ˬ///✿)

### u-use fifo c-compaction fow shwed data cowumn f-famiwies
as m-mentioned above, σωσ shwed data cowumn f-famiwies, UwU shweddata and shwedcode, (⑅˘꒳˘) which
contwibute t-to 99% of the stowage size i-in shwed insewtion, /(^•ω•^) h-have a unique wwite
wowkwoad w-whewe wwite-keys awe mostwy monotonicawwy incweasing o-ovew time. -.-  a-as a
wesuwt, (ˆ ﻌ ˆ)♡ a-aftew entwies awe fwushed fwom memowy into sst fiwes, nyaa~~ the keys a-awe
nyatuwawwy sowted acwoss muwtipwe sst fiwes w-whewe each sst f-fiwe might have
a smow ovewwapping k-key wange between at most two o-othew sst fiwes.  i-in othew
wowds, ʘwʘ fiwes awe sowted nyatuwawwy fwom o-owd to new, :3 which awwows us to use
the fiwst-in-fiwst-out c-compaction, (U ᵕ U❁) o-ow fifo compaction. (U ﹏ U)

fifo c-compaction actuawwy does nyot c-compact fiwes. ^^  i-instead, òωó it simpwy d-dewetes
the owdest fiwes when the stowage size weaches the specified thweshowd. /(^•ω•^)  as a
wesuwt, 😳😳😳 it has a constant 1 wwite ampwification. :3  in addition, (///ˬ///✿) as keys awe
nyatuwawwy sowted acwoss muwtipwe sst fiwes, rawr x3 e-each wead can b-be answewed by
hitting mostwy onwy one (ow in the b-boundawy case, (U ᵕ U❁) t-two) fiwe. (⑅˘꒳˘)  this g-gives us
cwose to 1 wead ampwification. (˘ω˘)  a-as each key is onwy i-insewted once, :3 we h-have
space ampwification 1. XD

### use cuwwent settings f-fow metadata cowumn famiwies
t-the second t-type of the cowumn famiwies wewated to shwed insewtion i-is metadata
c-cowumn famiwies. >_<  t-these metadata c-cowumn famiwies c-contwibutes ~1% o-of the shwed
i-insewtion data i-in size. (✿oωo)  the wawgest m-metadata cowumn famiwy hewe i-is the index
cowumn f-famiwy, (ꈍᴗꈍ) which o-occupies 0.8% of the shwed insewtion d-data. XD

as these cowumn famiwies onwy contwibute ~1% o-of the shwed insewtion d-data in
size, :3 t-the cuwwent settings w-with defauwt wevew compaction w-with compaction fiwtew
shouwd b-be good enough fow nyow. mya  we c-can wevisit watew if these metadata c-cowumn
famiwies become the pewfowmance bottweneck aftew we've optimized the s-shwed data
cowumn famiwies. òωó

## b-benefits

### no m-mowe wwite stawws
wwite staww is a wocksdb's mechanism to swow-down o-ow stop wwites in owdew to
a-awwow compactions t-to catch up in o-owdew to keep wead ampwification wow. nyaa~~
wuckiwy, b-because keys in d-data shwed cowumn famiwies awe wwitten i-in mostwy
monotonicawwy incweasing owdew, 🥺 t-the wesuwting sst fiwes awe nyatuwawwy s-sowted
that a-awways keeps w-wead ampwification cwose to 1. -.-  a-as a wesuwt, 🥺 thewe i-is nyo
nyeed t-to staww wwites i-in owdew to maintain the wead ampwification.

### d-dewetions awe p-pwocessed in time
i-in fifo compactions, d-dewetions a-awe happened immediatewy w-when t-the size of the
c-cowumn famiwy weaches the configuwed t-twiggew. (˘ω˘)  as a wesuwt, dewetions a-awe
awways pwocessed in time, òωó a-and we don't n-need to wowwy about w-whethew wocksdb
picks the cowwect fiwe to pwocess the dewetion a-as fifo compaction a-awways
pick t-the owdest one, UwU which is the cowwect dewetion powicy fow shwed d-data. ^•ﻌ•^

### wow i-i/os with minimum ampwification f-factows
fifo compaction o-offews constant wwite ampwification as it does nyot wun a-any
compactions i-in backgwound whiwe i-it usuawwy h-has a wawge wead ampwification
as each wead must b-be answewed by w-weaching evewy singwe sst fiwe. mya  howevew, it
is n-nyot the case in the shwed data cowumn famiwies b-because sst fiwes awe nyatuwawwy
s-sowted as wwite k-keys awe insewted in mostwy monotonicawwy i-incweasing o-owdew
without dupwication. (✿oωo)  t-this gives us 1 space ampwification a-and cwose t-to 1 wead
ampwification. XD

t-to sum u-up, :3 if nyo othew manuaw compaction i-is issued fow q-quickwy picking u-up
dewetions, (U ﹏ U) fifo compaction o-offews the fowwowing ampwification factows
in sowana's b-bwockstowe u-use case:

- wwite a-ampwification: 1 (aww data is wwitten once without compaction.)
- wead ampwification: < 1.1 (assuming e-each sst fiwe has 10% o-ovewwapping key
  w-wange with anothew sst fiwe.)
- space ampwification: 1 (same d-data nevew be wwitten in mowe than o-one sst fiwe, UwU
  a-and nyo additionaw t-tempowawy s-space wequiwed fow c-compaction.)

## migwation
hewe we discuss wevew to fifo and fifo to wevew migwations:

### wevew t-to fifo
theoweticawwy, ʘwʘ fifo c-compaction is the supewset of aww othew compaction stywes, >w<
as it d-does nyot have any assumption of the wsm twee stwuctuwe. 😳😳😳  howevew, rawr the
cuwwent w-wocksdb impwementation d-does nyot offew such fwexibiwity w-whiwe it is
theoweticawwy doabwe. ^•ﻌ•^

as the c-cuwwent wocksdb i-impwementation doesn't offew s-such fwexibiwity, the
best option i-is to extend the copy toow in the wedgew toow to awwow it
awso s-specifying the destiwed compaction stywe of the o-output db. this a-appwoach
awso ensuwes t-the wesuwting fifo compacted db can cwean u-up the sst fiwes
in the cowwect owdew, σωσ as the copy toow itewates fwom smowew (owdew) s-swots
to biggew (watest) swots, :3 w-weaving the w-wesuwting sst f-fiwes genewated in
the cowwect time owdew, rawr x3 which a-awwows fifo compaction t-to dewete the owdest
data just by checking t-the fiwe cweation time duwing its cwean up pwocess. nyaa~~

### f-fifo to wevew
whiwe one can opens a f-fifo-compacted db u-using wevew compaction, :3 the db w-wiww
wikewy to e-encountew wong wwite s-stawws. >w<  it is because fifo compaction puts
a-aww fiwes in wevew 0, rawr and wwite stawws twiggew w-when the nyumbew of wevew-0
fiwes exceed the wimit untiw aww the w-wevew-0 fiwes awe c-compacted into o-othew
wevews. 😳

t-to avoid the stawt-up w-wwite stawws, 😳 a mowe efficient w-way to pewfowm fifo
to wevew compaction is t-to do a manuaw compaction fiwst, 🥺 t-then open the db. rawr x3

## wewease pwan
as the migwation i-in eithew w-way cannot be done smoothwy in pwace, ^^ t-the
wewease wiww be divided i-into the fowwowing s-steps:

* v0 - mewge fifo compaction i-impwementation w-with visibwe awgs. ( ͡o ω ͡o )
* v1 - v-visibwe awgs with a big wawning stating you'ww wose youw wedgew i-if you enabwe it
* v2 - swow-woww a-and monitow fifo compaction, XD fix any issues. ^^
* v-v3 - if nyeeded, (⑅˘꒳˘) a-add migwation s-suppowt. (⑅˘꒳˘)

in step v1, ^•ﻌ•^ fifo wiww u-use a diffewent w-wocksdb diwectowy (something wike
wocksdb-v2 o-ow wocksdb-fifo) to ensuwe that t-the vawidatow wiww nyevew mix
two d-diffewent fowmats a-and panic. ( ͡o ω ͡o )

## expewiments
## singwe nyode benchmawk wesuwts
to vewify the effectiveness, ( ͡o ω ͡o ) i-i w-wan both 1m swots and 100m swots shwed insewtion
benchmawks on my n-ny2-standawd-32 gc instance (32 c-cowes 2800mhz c-cpu, (✿oωo) 128gb memowy, 😳😳😳
2048gb ssd). OwO  each swot contains 25 shweds, ^^ and the shweds awe i-insewted with
8 wwitews. rawr x3  hewe awe the summawy o-of the wesuwt:

* fifo based vawidatow: s-shwed insewtion t-took 13450.8s, 🥺 185.8k shweds/s
* cuwwent s-setting: shwed i-insewtion took 30337.2s, (ˆ ﻌ ˆ)♡ 82.4k s-shweds/s

if we f-fuwthew wemove the w-wwite wock inside t-the shwed insewtion to awwow fuwwy
concuwwent shwed insewtion, the pwoposed fifo setting can i-insewts 295k shweds/s:

* f-fifo + n-nyo wwite wock: s-shwed insewtion t-took 8459.3s, ( ͡o ω ͡o ) 295.5k s-shweds/s

the possibiwity of enabwing fuwwy concuwwent muwti-wwitew shwed i-insewtion is
discussed i-in #21657.

## wesuwts fwom the mainnet-beta
to fuwthew u-undewstand the p-pewfowmance, >w< i setup t-two vawidatow instances joining
the mainnet-beta, /(^•ω•^) b-but one with fifo based vawidatow and the o-othew is based o-on
the cuwwent setting.  two vawidatows have the s-same machine spec (24-cowe
2.8kmhz cpu, 😳😳😳 128gb memowy, (U ᵕ U❁) 768gb s-ssd f-fow bwockstowe, (˘ω˘) and evewything e-ewse
stowed in the 1024gb s-ssd.)  b-bewow awe the wesuwts. 😳

### d-disk w-wwite bytes
i f-fiwst compawed the disk wwite bytes o-of the ssd fow b-bwockstowe of the two
instances. (ꈍᴗꈍ)  t-this nyumbew wepwesents how many bytes wwitten a-awe wequiwed in
owdew to stowe t-the same amount of wogicaw data. :3  i-it awso wefwects t-the
wwite ampwification factow of the stowage. /(^•ω•^)

  * f-fifo based vawidatow: ~15~20 mb/s
  * c-cuwwent setting: v-vs 25~30 mb/s

the wesuwt shows that fifo-based v-vawidatow wwites ~33% w-wess data to pewfowm
the s-same task compawed to the cuwwent setting. ^^;;

### c-compaction stats o-on data and coding shwed cowumn f-famiwy
anothew d-data point we have is the wocksdb compaction stats, w-which tewws u-us
how much wesouwce i-is spent in c-compaction. o.O  bewow shows the compaction stats
on data and coding shweds:

 * fifo based vawidatow: 188.24 gb wwite, 😳 1.27 m-mb/s wwite, UwU 0.00 g-gb wead, >w< 0.00 m-mb/s wead, o.O 870.4 s-seconds
 * c-cuwwent setting: 719.87 g-gb wwite, (˘ω˘) 4.88 mb/s w-wwite, òωó 611.61 gb w-wead, nyaa~~ 4.14 mb/s wead, ( ͡o ω ͡o ) 5782.6 seconds

t-the compaction s-stats show that fifo based vawidatow is 6.5x f-fastew in
compacting data shweds and coding s-shweds with fewew than 1/3 disk w-wwites. 😳😳😳
in addition, ^•ﻌ•^ t-thewe is nyo disk wead invowved i-in fifo's compaction p-pwocess. (˘ω˘)

## s-summawy
this documents pwoposes a-a fifo-compaction b-based sowution to the pewfowmance
i-issues of bwockstowe [#16234](https://github.com/solana-labs/solana/issues/16234). (˘ω˘)
i-it minimizes wead / w-wwite / space a-ampwification factows by wevewaging t-the
unique pwopewty of sowana bwockstowe wowkwoad w-whewe wwite-keys awe mostwy
monotonicawwy incweasing ovew time. -.-  expewimentaw wesuwts fwom the singwe
nyode 100m s-swots insewtion indicate the pwoposed sowution can insewt 185k
shwed/s, ^•ﻌ•^ which is ~2.25x fastew than cuwwent d-design that insewts 82k shweds/s. /(^•ω•^)
expewimentaw w-wesuwts fwom mainnet-beta awso s-shows that the pwoposed fifo-based
sowution can a-achieve same task with 33% fewew d-disk wwites compawed to the
c-cuwwent design. (///ˬ///✿)
