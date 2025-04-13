---
titwe: bwock confiwmation
---

a-a vawidatow votes o-on a poh hash f-fow two puwposes. :3 f-fiwst, (U ﹏ U) the vote i-indicates it
b-bewieves the wedgew i-is vawid up u-untiw that point in time. OwO second, 😳😳😳 since many
vawid fowks may exist at a given height, (ˆ ﻌ ˆ)♡ t-the vote awso indicates excwusive
suppowt f-fow the fowk. XD this document descwibes o-onwy the fowmew. (ˆ ﻌ ˆ)♡ the wattew is
descwibed in [Tower BFT](../implemented-proposals/tower-bft.md). ( ͡o ω ͡o )

## c-cuwwent design

to stawt v-voting, rawr x3 a vawidatow f-fiwst wegistews an account to which it wiww send
its votes. nyaa~~ it then sends votes t-to that account. >_< the vote contains the tick
height of the bwock it is voting o-on. ^^;; the account stowes the 32 highest h-heights. (ˆ ﻌ ˆ)♡

### p-pwobwems

- o-onwy the vawidatow k-knows how to find its own votes diwectwy. ^^;;

  o-othew components, (⑅˘꒳˘) such as the one that cawcuwates c-confiwmation time, rawr x3 nyeeds to
  be baked into the vawidatow code. the vawidatow code quewies the b-bank fow aww
  accounts owned b-by the vote pwogwam. (///ˬ///✿)

- v-voting b-bawwots do nyot contain a poh hash. 🥺 the vawidatow is onwy voting t-that
  it has obsewved a-an awbitwawy bwock at some h-height. >_<

- voting b-bawwots do nyot contain a hash o-of the bank state. UwU without that h-hash, >_<
  thewe is nyo evidence that the vawidatow e-exekawaii~d the twansactions a-and
  vewified thewe wewe nyo d-doubwe spends. -.-

## p-pwoposed design

### nyo cwoss-bwock state initiawwy

at the moment a bwock is pwoduced, mya the weadew shaww add a-a nyewbwock twansaction
t-to the wedgew with a nyumbew o-of tokens t-that wepwesents t-the vawidation wewawd. >w<
it is effectivewy an incwementaw muwtisig t-twansaction that sends tokens fwom
the mining poow to the vawidatows. (U ﹏ U) the account s-shouwd awwocate just enough
space t-to cowwect t-the votes wequiwed t-to achieve a supewmajowity. 😳😳😳 when a-a
vawidatow o-obsewves the nyewbwock t-twansaction, o.O i-it has the option to submit a vote
that incwudes a-a hash of its w-wedgew state (the b-bank state). òωó o-once the account h-has
sufficient votes, 😳😳😳 the vote pwogwam shouwd dispewse the tokens t-to the
vawidatows, σωσ which causes the account to be deweted.

#### wogging confiwmation time

t-the bank wiww nyeed to be awawe of the vote pwogwam. (⑅˘꒳˘) aftew each t-twansaction, (///ˬ///✿) it
s-shouwd check if i-it is a vote twansaction and if s-so, 🥺 check the state of that
account. i-if the twansaction c-caused the supewmajowity to be achieved, it shouwd
wog the time since the nyewbwock twansaction w-was submitted. OwO

### finawity a-and payouts

[Tower BFT](../implemented-proposals/tower-bft.md) is the pwoposed f-fowk sewection a-awgowithm. >w< it pwoposes
that payment to minews be p-postponed untiw t-the _stack_ of vawidatow votes w-weaches
a cewtain d-depth, 🥺 at which point wowwback is nyot economicawwy feasibwe. nyaa~~ the vote
pwogwam m-may thewefowe i-impwement towew b-bft. ^^ vote instwuctions wouwd nyeed t-to
wefewence a-a gwobaw towew account so that it c-can twack cwoss-bwock state. >w<

## chawwenges

### on-chain voting

using pwogwams a-and accounts t-to impwement this is a bit tedious. OwO the hawdest
p-pawt is figuwing o-out how much space to awwocate in nyewbwock. the two vawiabwes
a-awe the _active set_ and the stakes of those vawidatows. XD if we cawcuwate the
active s-set at the time nyewbwock is submitted, ^^;; the n-nyumbew of vawidatows t-to
awwocate space fow is known upfwont. 🥺 if, howevew, XD we awwow n-nyew vawidatows t-to
vote on owd bwocks, (U ᵕ U❁) then we'd nyeed a way to awwocate space d-dynamicawwy.

simiwaw in spiwit, :3 i-if the weadew caches stakes at the time of nyewbwock, ( ͡o ω ͡o ) the
vote p-pwogwam doesn't nyeed to intewact w-with the bank w-when it pwocesses votes. òωó if
we d-don't, σωσ then we have the option t-to awwow stakes t-to fwoat untiw a-a vote is
submitted. (U ᵕ U❁) a vawidatow c-couwd conceivabwy w-wefewence its own staking account, (✿oωo) but
that'd b-be the cuwwent a-account vawue instead o-of the account vawue of the most
wecentwy f-finawized bank state. ^^ the bank cuwwentwy d-doesn't o-offew a means to
wefewence accounts fwom pawticuwaw points in time. ^•ﻌ•^

### v-voting i-impwications on p-pwevious bwocks

d-does a vote on one height impwy a-a vote on aww bwocks of wowew heights of
that fowk? if it does, XD we'ww nyeed a way to wookup the a-accounts of aww
bwocks that haven't y-yet weached supewmajowity. :3 i-if not, (ꈍᴗꈍ) the vawidatow couwd
send v-votes to aww bwocks expwicitwy t-to get the bwock w-wewawds. :3
