---
titwe: vawidatow
---

## histowy

w-when we fiwst s-stawted sowana, (✿oωo) t-the goaw was t-to de-wisk ouw tps c-cwaims. (U ﹏ U) we knew
t-that between o-optimistic concuwwency c-contwow and sufficientwy wong weadew swots, -.-
that pos consensus was nyot the b-biggest wisk to tps. ^•ﻌ•^ it was gpu-based signatuwe
v-vewification, rawr softwawe pipewining a-and concuwwent banking. (˘ω˘) thus, the tpu was
bown. nyaa~~ aftew topping 100k t-tps, UwU we spwit the team into o-one gwoup wowking t-towawd
710k tps and anothew to fwesh out the vawidatow pipewine. :3 hence, the t-tvu was
bown. (⑅˘꒳˘) the cuwwent awchitectuwe is a consequence of incwementaw devewopment w-with
that owdewing and pwoject p-pwiowities. (///ˬ///✿) i-it is nyot a wefwection o-of nyani w-we evew
bewieved was the most technicawwy ewegant c-cwoss-section of those technowogies. ^^;;
in the context o-of weadew wotation, >_< the stwong distinction between weading and
vawidating is bwuwwed. rawr x3

## d-diffewence between vawidating and w-weading

the f-fundamentaw diffewence b-between the pipewines is when the poh is pwesent. /(^•ω•^) in
a weadew, :3 w-we pwocess t-twansactions, (ꈍᴗꈍ) wemoving bad ones, /(^•ω•^) a-and then tag the w-wesuwt
with a poh hash. (⑅˘꒳˘) in the v-vawidatow, ( ͡o ω ͡o ) we vewify that hash, p-peew it off, òωó and
pwocess the twansactions in exactwy t-the same way. (⑅˘꒳˘) the onwy diffewence i-is that
if a vawidatow s-sees a bad twansaction, XD i-it can't simpwy wemove it wike the
weadew does, because that wouwd cause the poh hash to change. -.- instead, i-it
wejects the w-whowe bwock. :3 the othew diffewence b-between the pipewines i-is nyani
h-happens _aftew_ banking. nyaa~~ the weadew bwoadcasts entwies to downstweam v-vawidatows
wheweas the vawidatow wiww have awweady done that in wetwansmitstage, 😳 w-which is
a confiwmation t-time optimization. (⑅˘꒳˘) t-the vawidation p-pipewine, nyaa~~ on the othew hand, OwO
has o-one wast step. a-any time it finishes p-pwocessing a-a bwock, rawr x3 it nyeeds to weigh
any fowks it's obsewving, XD p-possibwy c-cast a vote, σωσ and i-if so, (U ᵕ U❁) weset its p-poh hash
to the b-bwock hash it just voted on. (U ﹏ U)

## pwoposed design

we unwwap the m-many abstwaction wayews and buiwd a singwe pipewine that can
toggwe weadew mode on whenevew the v-vawidatow's id shows up in the weadew
scheduwe. :3

![Validator block diagram](/img/validator-proposal.svg)

## nyotabwe c-changes

- hoist f-fetchstage and b-bwoadcaststage out of tpu
- bankfowks w-wenamed to banktwee
- tpu m-moves to nyew socket-fwee c-cwate cawwed sowana-tpu. ( ͡o ω ͡o )
- tpu's bankingstage absowbs wepwaystage
- tvu goes away
- nyew w-wepaiwstage absowbs shwed fetch s-stage and wepaiw wequests
- j-json wpc sewvice i-is optionaw - used fow debugging. σωσ it shouwd instead b-be pawt
  of a-a sepawate `solana-blockstreamer` executabwe. >w<
- n-nyew muwticaststage a-absowbs wetwansmit pawt of wetwansmitstage
- muwticaststage downstweam o-of bwockstowe
