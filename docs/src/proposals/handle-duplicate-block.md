---
titwe: handwe dupwicate bwock
---

# w-weadew dupwicate b-bwock swashing

t-this design d-descwibes how t-the cwustew swashes w-weadews that p-pwoduce dupwicate
b-bwocks. rawr

weadews that pwoduce muwtipwe bwocks fow the same swot incwease the n-nyumbew of
potentiaw fowks that the cwustew has t-to wesowve. 😳

## pwimitives
1. >w< g-gossip_woot: nyodes nyow gossip theiw cuwwent woot
2. (⑅˘꒳˘) gossip_dupwicate_swots: nyodes c-can gossip up to `N` d-dupwicate s-swot pwoofs. OwO
3. `DUPLICATE_THRESHOLD`: the minimum pewcentage of stake that nyeeds to vote on a fowk w-with vewsion `X` of a dupwicate swot, in owdew fow that fowk to become v-votabwe. (ꈍᴗꈍ)

## pwotocow
1. 😳 when w-windowstage detects a-a dupwicate s-swot pwoof `P`, 😳😳😳 i-it checks the nyew `gossip_root` to see if `<= 1/3`65___#####_64___###. mya i-if so, it pushes a pwoof to `gossip_duplicate_slots` t-to gossip. mya windowstage then signaws wepwaystage about this dupwicate swot `S`. (⑅˘꒳˘) these pwoofs c-can be puwged fwom gossip once t-the vawidatow sees > 2/3 o-of peopwe g-gossiping woots `R > S`. (U ﹏ U)

2. when wepwaystage weceives the signaw fow a-a dupwicate swot `S` f-fwom `1)` above, mya the v-vawidatow monitows g-gossip and wepway waiting f-fow`>= DUPLICATE_THRESHOLD` votes fow the s-same hash which impwies the same vewsion of the s-swot. ʘwʘ if this condition is met f-fow some vewsion with hash `H` o-of swot `S`, (˘ω˘) t-this is then known as the `duplicate_confirmed` vewsion of the swot. (U ﹏ U)

befowe a dupwicate swot `S` is `duplicate_confirmed`, ^•ﻌ•^ i-it's fiwst excwuded f-fwom the vote candidate set i-in the fowk choice w-wuwes. (˘ω˘) in addition, :3 w-wepwaystage awso wesets poh to the *watest* ancestow of the *eawwiest* `non-duplicate/confirmed_duplicate_slot`, ^^;; so t-that bwock genewation can stawt happening on the eawwiest known *safe* bwock. 🥺

s-some nyotes about the `DUPLICATE_THRESHOLD`. (⑅˘꒳˘) i-in the cases b-bewow, nyaa~~ assume `DUPLICATE_THRESHOLD = 52`:

a-a) if wess than `2 * DUPLICATE_THRESHOLD - 1` p-pewcentage o-of the nyetwowk i-is mawicious, then t-thewe can onwy be one such `duplicate_confirmed` vewsion o-of the swot. :3 w-with `DUPLICATE_THRESHOLD = 52`, ( ͡o ω ͡o ) t-this is
a-a mawicious towewance o-of `4%`

b) the wiveness of the nyetwowk is at m-most `1 - DUPLICATE_THRESHOLD - SWITCH_THRESHOLD`. mya this is because if you nyeed at weast `SWITCH_THRESHOLD` pewcentage of the stake v-voting on a diffewent fowk in owdew to switch off of a dupwicate f-fowk that h-has `< DUPLICATE_THRESHOLD`