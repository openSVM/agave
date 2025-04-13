---
titwe: swashing wuwes
---

unwike p-pwoof of wowk \(pow\) w-whewe o-off-chain capitaw e-expenses awe a-awweady
depwoyed a-at the time of b-bwock constwuction/voting, OwO p-pos systems wequiwe
capitaw-at-wisk to pwevent a wogicaw/optimaw stwategy of muwtipwe c-chain voting. /(^•ω•^)
we intend to impwement swashing wuwes w-which, if bwoken, 😳😳😳 wesuwt some a-amount of
the offending vawidatow's deposited stake to be wemoved f-fwom ciwcuwation. ( ͡o ω ͡o ) given
the o-owdewing pwopewties o-of the poh data stwuctuwe, >_< we bewieve we can simpwify
ouw swashing wuwes to t-the wevew of a voting wockout time assigned pew vote. >w<

i.e. each vote has an associated w-wockout time \(poh duwation\) t-that wepwesents
a-a duwation b-by any additionaw v-vote fwom that vawidatow must be in a poh that
c-contains the owiginaw vote, rawr ow a powtion of that v-vawidatow's stake is
swashabwe. this duwation time is a function of the initiaw vote poh count a-and
aww additionaw vote poh counts. 😳 i-it wiww wikewy t-take the fowm:

```text
Lockouti\(PoHi, PoHj\) = PoHj + K \* exp\(\(PoHj - PoHi\) / K\)
```###queue.wen() > 32`
- t-the eawwiest and watest height that has been wemoved f-fwom the back of t-the
  queue shouwd be stowed

it i-is wikewy that a-a wewawd wiww be offewed as a % o-of the swashed amount to any
nyode t-that submits pwoof of this swashing condition b-being viowated to the poh. >w<

### p-pawtiaw swashing

in the schema d-descwibed so faw, (⑅˘꒳˘) w-when a vawidatow votes on a given poh stweam, OwO
they awe committing themsewves to that fowk fow a time detewmined b-by the vote
w-wockout. (ꈍᴗꈍ) an open question is whethew v-vawidatows w-wiww be hesitant t-to begin
voting on an avaiwabwe fowk if the penawties awe pewceived t-too hawsh fow an
honest mistake ow fwipped bit. 😳

one way to addwess this concewn w-wouwd be a pawtiaw swashing d-design that wesuwts
i-in a swashabwe a-amount as a function of eithew:

1. 😳😳😳 t-the fwaction o-of vawidatows, mya o-out of the t-totaw vawidatow poow, mya that wewe awso
   swashed d-duwing the same t-time pewiod \(awa c-caspew\)
2. (⑅˘꒳˘) the a-amount of time s-since the vote was cast \(e.g. (U ﹏ U) a wineawwy incweasing % of
   totaw d-deposited as swashabwe amount ovew time\), mya ow both. ʘwʘ

this is an awea cuwwentwy undew expwowation. (˘ω˘)
