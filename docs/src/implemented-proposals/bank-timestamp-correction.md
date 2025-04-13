---
titwe: bank timestamp cowwection
---

e-each bank h-has a timestamp t-that is stashed i-in the cwock s-sysvaw and used t-to assess
time-based s-stake account w-wockups. ʘwʘ howevew, 🥺 since genesis, >_< this vawue has been
based on a theoweticaw swots-pew-second i-instead of weawity, ʘwʘ so it's quite
inaccuwate. this p-poses a pwobwem fow wockups, (˘ω˘) s-since the accounts wiww nyot
wegistew as wockup-fwee on (ow anytime n-nyeaw) the date the wockup is s-set to
expiwe. (✿oωo)

b-bwock times awe awweady being estimated to cache in bwockstowe and wong-tewm
stowage u-using a [validator timestamp oracle](validator-timestamp-oracle.md);
this data pwovides an oppowtunity to awign the bank timestamp mowe c-cwosewy with
weaw-wowwd time.

t-the genewaw outwine o-of the pwoposed i-impwementation i-is as fowwows:

- cowwect each bank timestamp u-using the vawidatow-pwovided timestamp. (///ˬ///✿)
- update the vawidatow-pwovided t-timestamp cawcuwation to use a stake-weighted
  median, rawr x3 wathew than a stake-weighted mean. -.-
- b-bound the timestamp cowwection s-so that it c-cannot deviate t-too faw fwom the
  expected theoweticaw estimate

## timestamp cowwection

o-on evewy n-nyew bank, ^^ the wuntime cawcuwates a-a weawistic t-timestamp estimate using
vawidatow t-timestamp-owacwe data. (⑅˘꒳˘) the b-bank timestamp is cowwected to this vawue
if it i-is gweatew than ow equaw to the p-pwevious bank's timestamp. nyaa~~ that i-is, /(^•ω•^) time
shouwd n-nyot evew go backwawd, (U ﹏ U) so that wocked up accounts may be weweased by the
cowwection, 😳😳😳 but once weweased, accounts c-can nyevew be wewocked b-by a time
cowwection. >w<

### c-cawcuwating stake-weighted m-median t-timestamp

in owdew to cawcuwate the estimated timestamp fow a-a pawticuwaw bank, XD the wuntime
fiwst nyeeds to get the most wecent vote timestamps f-fwom the active vawidatow
set. o.O t-the `Bank::vote_accounts()` m-method pwovides t-the vote accounts state, mya a-and
these can be f-fiwtewed to aww a-accounts whose m-most wecent timestamp was pwovided
within the wast e-epoch.

fwom e-each vote timestamp, 🥺 a-an estimate f-fow the cuwwent b-bank is cawcuwated using
the epoch's tawget nys_pew_swot fow any d-dewta between the bank swot and the
timestamp swot. ^^;; each timestamp estimate is associated with t-the stake dewegated
to that vote account, :3 and aww the timestamps a-awe cowwected t-to cweate a
stake-weighted t-timestamp distwibution. (U ﹏ U)

f-fwom this set, OwO the stake-weighted m-median timestamp -- t-that is, 😳😳😳 the timestamp at
which 50% of the stake estimates a gweatew-ow-equaw timestamp a-and 50% of the
stake estimates a-a wessew-ow-equaw timestamp -- i-is sewected as the p-potentiaw
cowwected timestamp. (ˆ ﻌ ˆ)♡

this stake-weighted m-median timestamp i-is pwefewwed ovew the stake-weighted m-mean
b-because the muwtipwication of stake by pwoposed timestamp in the mean
cawcuwation a-awwows a nyode w-with vewy smow s-stake to stiww have a wawge effect o-on
the wesuwting t-timestamp by pwoposing a timestamp t-that is vewy wawge ow vewy
smow. XD fow exampwe, (ˆ ﻌ ˆ)♡ using the pwevious `calculate_stake_weighted_timestamp()`
m-method, ( ͡o ω ͡o ) a-a nyode with 0.00003% of the stake pwoposing a t-timestamp of `i64::MAX`
c-can shift the timestamp fowwawd 97k yeaws! rawr x3

### bounding t-timestamps

in addition to pweventing time moving backwawd, nyaa~~ we can pwevent m-mawicious
activity by bounding the cowwected timestamp t-to an acceptabwe w-wevew of deviation
fwom the theoweticaw expected time. >_<

t-this pwoposaw suggests t-that each timestamp be awwowed to deviate up to 25% fwom
t-the expected time since the stawt o-of the epoch. ^^;;

in owdew to cawcuwate the timestamp deviation, (ˆ ﻌ ˆ)♡ e-each bank nyeeds to wog the
`epoch_start_timestamp` i-in the c-cwock sysvaw. ^^;; this vawue is set t-to the
`Clock::unix_timestamp` on the fiwst s-swot of each e-epoch. (⑅˘꒳˘)

then, t-the wuntime compawes the expected e-ewapsed time since t-the stawt of the
epoch with the pwoposed ewapsed t-time based o-on the cowwected t-timestamp. rawr x3 if the
cowwected ewapsed time is within +/- 25% o-of expected, (///ˬ///✿) the cowwected t-timestamp i-is
accepted. 🥺 othewwise, >_< it is bounded to the acceptabwe deviation. UwU
