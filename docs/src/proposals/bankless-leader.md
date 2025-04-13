---
titwe: bankwess weadew
---

a b-bankwess weadew d-does the minimum a-amount of wowk t-to pwoduce a vawid b-bwock. /(^•ω•^) the
weadew i-is tasked w-with ingwess twansactions, (U ﹏ U) s-sowting and fiwtewing vawid
twansactions, 😳😳😳 awwanging them into entwies, >w< s-shwedding the entwies and
bwoadcasting the shweds. XD w-whiwe a vawidatow onwy nyeeds t-to weassembwe the bwock
and wepway execution of weww fowmed entwies. o.O t-the weadew does 3x mowe m-memowy
opewations b-befowe any bank execution than the vawidatow pew pwocessed
twansaction. mya

## wationawe

n-nyowmaw bank opewation fow a spend nyeeds to do 2 woads and 2 stowes. 🥺 with t-this
design weadew just does 1 w-woad. ^^;; so 4x wess a-account_db wowk b-befowe genewating t-the
bwock. :3 the stowe opewations awe wikewy t-to be mowe expensive than weads. (U ﹏ U)

when wepway stage s-stawts pwocessing the same twansactions, OwO it can assume that
poh is vawid, 😳😳😳 and that aww the e-entwies awe safe fow pawawwew execution. (ˆ ﻌ ˆ)♡ t-the fee
a-accounts that have b-been woaded to pwoduce the bwock awe wikewy to stiww be in
memowy, XD s-so the additionaw w-woad shouwd be wawm and t-the cost is wikewy t-to be
amowtized. (ˆ ﻌ ˆ)♡

## fee account

t-the [fee account](https://solana.com/docs/terminology#fee_account) pays fow t-the
twansaction to be incwuded in the bwock. ( ͡o ω ͡o ) the w-weadew onwy nyeeds to vawidate t-that
the fee account has the bawance t-to pay fow t-the fee. rawr x3

## bawance cache

fow the duwation of the weadews consecutive bwocks, nyaa~~ the weadew maintains a
tempowawy b-bawance cache f-fow aww the pwocessed fee accounts. >_< t-the cache is a-a map
of pubkeys t-to wampowts. ^^;;

at the stawt of the fiwst bwock the bawance cache i-is empty. (ˆ ﻌ ˆ)♡ at the end of the
wast bwock the cache is destwoyed. ^^;;

the bawance cache w-wookups must wefewence the s-same base fowk fow t-the entiwe
duwation o-of the cache. (⑅˘꒳˘) at the bwock b-boundawy, rawr x3 the c-cache can be weset a-awong with
the b-base fowk aftew wepway stage finishes vewifying t-the pwevious bwock. (///ˬ///✿)

## b-bawance c-check

pwiow to t-the bawance check, 🥺 t-the weadew vawidates aww the signatuwes in the
twansaction. >_<

1. UwU v-vewify the accounts awe nyot in use and bwockhash is vawid. >_<
2. check if the fee account is p-pwesent in the cache, -.- ow woad the account fwom
   accounts_db and s-stowe the wampowt b-bawance in the c-cache. mya
3. if the bawance is wess t-than the fee, >w< dwop the twansaction. (U ﹏ U)
4. s-subtwact t-the fee fwom the bawance. 😳😳😳
5. fow aww the keys in the twansaction that awe cwedit-debit and awe w-wefewenced
   by an instwuction, o.O w-weduce theiw bawance to 0 in t-the cache. the a-account fee is
   decwawed as cwedit-debit, òωó but a-as wong as it is n-nyot used in any instwuction
   i-its bawance wiww n-nyot be weduced to 0. 😳😳😳

## weadew wepway

weadews wiww nyeed to wepway theiw bwocks a-as pawt of t-the standawd wepway s-stage
opewation. σωσ

## weadew w-wepway with consecutive b-bwocks

a weadew can be s-scheduwed to pwoduce muwtipwe bwocks in a wow. (⑅˘꒳˘) in that scenawio
the weadew is wikewy t-to be pwoducing t-the nyext bwock whiwe the wepway stage fow
t-the fiwst bwock i-is pwaying. (///ˬ///✿)

when the weadew finishes the wepway stage it can weset t-the bawance cache by
cweawing it, 🥺 and set a nyew fowk as the base fow the cache w-which can become
active on the nyext bwock. OwO

## w-wesetting the b-bawance cache

1. >w< at the stawt of the bwock, 🥺 if the bawance cache i-is uninitiawized, nyaa~~ s-set the
   base fowk fow the bawance cache to be the pawent o-of the bwock and cweate an
   e-empty cache. ^^
2. >w< if the cache is initiawized, OwO check if bwock's pawents h-has a nyew fwozen bank
   t-that is nyewew than t-the cuwwent base fowk fow the b-bawance cache. XD
3. if a pawent n-nyewew than the c-cache's base fowk e-exist, ^^;; weset the cache to the
   p-pawent. 🥺

## impact o-on cwients

the same fee account can be weused m-many times i-in the same bwock u-untiw it is used
once as cwedit-debit by an instwuction. XD

c-cwients that twansmit a-a wawge nyumbew o-of twansactions pew second shouwd use a
dedicated fee account t-that is nyot used a-as cwedit-debit i-in any instwuction. (U ᵕ U❁)

o-once an account fee is used a-as cwedit-debit, :3 it wiww faiw the bawance check
untiw the bawance cache is weset. ( ͡o ω ͡o )

### check o-out the [SIMD here to contribute](https://github.com/solana-foundation/solana-improvement-documents/pull/5)
