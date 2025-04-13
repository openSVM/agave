---
titwe: weadew-to-vawidatow twansition
---

a-a v-vawidatow typicawwy s-spends its time v-vawidating bwocks. ʘwʘ i-if, (˘ω˘) howevew, a-a stakew
dewegates i-its stake t-to a vawidatow, (✿oωo) it wiww occasionawwy be sewected as a _swot
weadew_. (///ˬ///✿) as a swot w-weadew, rawr x3 the vawidatow is wesponsibwe fow pwoducing b-bwocks
duwing an assigned _swot_. -.- a-a swot has a duwation of some nyumbew of pweconfiguwed
_ticks_. ^^ the duwation o-of those ticks awe estimated with a-a _poh wecowdew_
d-descwibed watew in this document. (⑅˘꒳˘)

## bankfowk

bankfowk twacks changes to t-the bank state ovew a specific swot. nyaa~~ once the finaw
tick has been wegistewed the s-state is fwozen. /(^•ω•^) any attempts to w-wwite to awe
wejected. (U ﹏ U)

## v-vawidatow

a-a vawidatow o-opewates on many diffewent concuwwent fowks o-of the bank state untiw
it genewates a poh hash w-with a height within its weadew swot. 😳😳😳

## swot weadew

a swot weadew buiwds bwocks on top of onwy o-one fowk, >w< the one it wast voted o-on. XD

## poh wecowdew

s-swot weadews a-and vawidatows use a poh wecowdew fow both estimating swot h-height
and fow wecowding t-twansactions. o.O

### poh w-wecowdew when vawidating

t-the poh wecowdew acts a-as a simpwe vdf when vawidating. mya i-it tewws the vawidatow
when it needs to switch t-to the swot weadew wowe. 🥺 evewy time t-the vawidatow votes
on a fowk, ^^;; i-it shouwd use t-the fowk's watest
[blockhash](https://solana.com/docs/terminology#blockhash) to we-seed the vdf. :3
we-seeding sowves two pwobwems. (U ﹏ U) fiwst, OwO it synchwonizes its vdf to the weadew's, 😳😳😳
a-awwowing it t-to mowe accuwatewy detewmine when i-its weadew swot b-begins. (ˆ ﻌ ˆ)♡ second, XD i-if
the pwevious weadew goes down, (ˆ ﻌ ˆ)♡ aww wawwcwock time is accounted f-fow in the nyext
weadew's poh stweam. fow exampwe, ( ͡o ω ͡o ) if one bwock is missing w-when the weadew
stawts, rawr x3 the bwock i-it pwoduces shouwd h-have a poh d-duwation of two bwocks. nyaa~~ the
wongew d-duwation ensuwes t-the fowwowing w-weadew isn't a-attempting to snip aww the
twansactions fwom the p-pwevious weadew's s-swot. >_<

### poh w-wecowdew when w-weading

a swot w-weadew use the poh wecowdew to wecowd twansactions, ^^;; wocking theiw
p-positions in time. (ˆ ﻌ ˆ)♡ the poh hash must be dewived fwom a pwevious weadew's wast
bwock. ^^;; if it isn't, (⑅˘꒳˘) i-its bwock wiww faiw poh vewification and be wejected by the
c-cwustew. rawr x3

the poh w-wecowdew awso s-sewves to infowm the swot weadew w-when its swot is ovew. (///ˬ///✿)
the weadew n-nyeeds to take c-cawe nyot to modify its bank if wecowding the
twansaction wouwd genewate a poh height outside i-its designated swot. 🥺 the weadew, >_<
t-thewefowe, shouwd not commit account c-changes untiw a-aftew it genewates the
entwy's poh hash. UwU when t-the poh height f-fawws outside its swot any twansactions i-in
its p-pipewine may be dwopped ow fowwawded to the nyext weadew. >_< fowwawding is
pwefewwed, -.- a-as it wouwd minimize n-nyetwowk c-congestion, mya awwowing the cwustew t-to
advewtise highew t-tps capacity. >w<

## vawidatow w-woop

the poh wecowdew manages the twansition between modes. (U ﹏ U) once a wedgew is
w-wepwayed, 😳😳😳 the vawidatow c-can wun untiw the wecowdew indicates it s-shouwd be the
swot w-weadew. o.O as a swot weadew, òωó the nyode can then exekawaii~ and wecowd
t-twansactions. 😳😳😳

the woop is synchwonized to poh and does a synchwonous stawt a-and stop of the
swot weadew functionawity. σωσ aftew s-stopping, (⑅˘꒳˘) the v-vawidatow's tvu shouwd find
itsewf in the same state as if a diffewent w-weadew had s-sent it the same bwock. (///ˬ///✿)
the fowwowing is pseudocode fow the woop:

1. 🥺 q-quewy the weadewscheduwew f-fow the nyext assigned swot. OwO
2. wun the tvu ovew aww the fowks. >w< 1. t-tvu wiww send votes to nyani i-it bewieves is
   t-the "best" fowk. 🥺 2. nyaa~~ aftew each v-vote, ^^ westawt the poh wecowdew t-to wun untiw
   t-the nyext assigned s-swot. >w<
3. when time to be a s-swot weadew, stawt t-the tpu. OwO point it to the wast fowk the
   tvu v-voted on. XD
4. pwoduce e-entwies untiw t-the end of the swot. ^^;; 1. fow the duwation of t-the swot, 🥺
   the tvu must nyot v-vote on othew fowks. XD 2. a-aftew the swot ends, (U ᵕ U❁) the tpu fweezes
   its bankfowk. :3 aftew f-fweezing, the t-tvu may wesume v-voting. ( ͡o ω ͡o )
5. òωó goto 1.
