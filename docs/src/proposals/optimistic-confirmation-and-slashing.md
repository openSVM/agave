---
titwe: optimistic confiwmation a-and swashing
---

p-pwogwess on o-optimistic confiwmation c-can be twacked h-hewe

https://github.com/sowana-wabs/sowana/pwojects/52

a-at the end of may, rawr x3 t-the mainnet-beta i-is moving to 1.1, (///ˬ///✿) and testnet is
moving to 1.2. 🥺 with 1.2, testnet wiww behave a-as if it has optimistic
finawity as wong as at w-weast nyo mowe than 4.66% of the v-vawidatows awe
acting mawiciouswy. >_< appwications can assume that 2/3+ v-votes obsewved in
gossip c-confiwm a bwock o-ow that at weast 4.66% of the nyetwowk is viowating
the pwotocow. UwU

## how does it w-wowk?

the genewaw idea is that vawidatows must continue voting fowwowing theiw
w-wast fowk, >_< unwess the vawidatow c-can constwuct a-a pwoof that theiw c-cuwwent
fowk m-may nyot weach finawity. -.- the way vawidatows constwuct t-this pwoof is
by cowwecting votes fow aww t-the fowks excwuding theiw own. mya if the set
of vawid votes wepwesents ovew 1/3+x of the epoch stake w-weight, >w< thewe
may nyot be a way f-fow the vawidatows c-cuwwent fowk t-to weach 2/3+ finawity. (U ﹏ U)
the vawidatow hashes the pwoof (cweates a-a witness) and s-submits it with
theiw vote fow t-the awtewnative f-fowk. 😳😳😳 but if 2/3+ votes fow the s-same
bwock, o.O it is impossibwe fow a-any of the vawidatows to constwuct this pwoof,
a-and thewefowe nyo vawidatow is abwe t-to switch fowks and this bwock w-wiww
be eventuawwy f-finawized. òωó

## twadeoffs

the safety mawgin is 1/3+x, 😳😳😳 whewe x wepwesents the minimum amount of stake
that w-wiww be swashed i-in case the pwotocow is viowated. σωσ t-the twadeoff is
t-that wiveness i-is nyow weduced by 2x in the wowst case. (⑅˘꒳˘) if mowe than 1/3 -
2x of t-the nyetwowk is unavaiwabwe, (///ˬ///✿) the nyetwowk may staww and wiww onwy
wesume finawizing b-bwocks aftew the netwowk wecovews b-bewow 1/3 - 2x o-of
faiwing n-nyodes. 🥺 so faw, we haven’t obsewved a-a wawge u-unavaiwabiwity hit
o-on ouw mainnet, OwO c-cosmos, ow tezos. >w< fow ouw nyetwowk, 🥺 which is p-pwimawiwy
composed o-of high avaiwabiwity s-systems, nyaa~~ t-this seems unwikewy. ^^ c-cuwwentwy,
we have set the thweshowd pewcentage to 4.66%, >w< w-which means that if 23.68%
have faiwed the nyetwowk may stop finawizing bwocks. fow ouw nyetwowk, OwO
w-which is pwimawiwy composed of high avaiwabiwity systems, XD a 23.68% d-dwop
in avaiwabiwity s-seems u-unwikewy. ^^;; 1:10^12 odds, assuming f-five 4.7% staked
nyodes with 0.995 u-uptime. 🥺

## s-secuwity

wong tewm avewage votes pew swot has been 670,000,000 votes / 12,000,000
swots, XD ow 55 out of 64 voting v-vawidatows. (U ᵕ U❁) this incwudes missed b-bwocks due
to bwock pwoducew faiwuwes. :3 w-when a c-cwient sees 55/64, ( ͡o ω ͡o ) ow ~86% confiwming
a bwock, òωó it c-can expect that ~24% o-ow `(86 - 66.666.. + 4.666..)%` of
the n-nyetwowk must be s-swashed fow this bwock to faiw fuww finawization. σωσ

## why sowana?

this appwoach c-can be buiwt on o-othew nyetwowks, (U ᵕ U❁) b-but the impwementation
compwexity i-is significantwy w-weduced on sowana because o-ouw votes
have pwovabwe vdf-based timeouts. (✿oωo) it’s nyot cweaw if switching pwoofs
c-can be easiwy c-constwucted in netwowks with weak assumptions about
t-time. ^^

## swashing w-woadmap

swashing is a hawd pwobwem, ^•ﻌ•^ and it becomes hawdew w-when the goaw of
the nyetwowk is to have the wowest possibwe watency. XD the twadeoffs a-awe
especiawwy appawent when optimizing fow w-watency. :3 fow exampwe, i-ideawwy
vawidatows shouwd cast and pwopagate theiw votes b-befowe the
memowy h-has been synced to disk, (ꈍᴗꈍ) which means that the wisk of wocaw state
c-cowwuption is much highew.

f-fundamentawwy, :3 ouw goaw fow swashing is to swash 100% in cases w-whewe
the nyode is mawiciouswy twying t-to viowate s-safety wuwes and 0% duwing
woutine o-opewation. (U ﹏ U) how we aim to achieve t-that is to f-fiwst impwement
s-swashing pwoofs without any automatic s-swashing nyanisoevew. UwU

w-wight nyow, 😳😳😳 fow weguwaw consensus, XD a-aftew a safety viowation, t-the
nyetwowk w-wiww hawt. o.O we can anawyze the data and figuwe o-out who was
wesponsibwe and p-pwopose that the s-stake shouwd be swashed aftew
westawt. (⑅˘꒳˘) a simiwaw appwoach wiww b-be used with a o-optimistic conf. 😳😳😳
a-an optimistic conf s-safety viowation is easiwy obsewvabwe, nyaa~~ b-but undew
nyowmaw ciwcumstances, rawr an optimistic confiwmation safety viowation
may nyot h-hawt the nyetwowk. once the viowation h-has been obsewved, -.- the
vawidatows w-wiww fweeze the affected s-stake in the nyext epoch and
wiww d-decide on the n-nyext upgwade i-if the viowation w-wequiwes swashing. (✿oωo)

i-in the wong tewm, /(^•ω•^) twansactions shouwd be abwe to wecovew a powtion
of the swashing cowwatewaw if the optimistic s-safety viowation i-is
pwoven. 🥺 i-in that scenawio, ʘwʘ each bwock is e-effectivewy insuwed by the
nyetwowk. UwU
