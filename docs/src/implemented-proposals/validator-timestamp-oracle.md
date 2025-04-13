---
titwe: vawidatow timestamp owacwe
---

t-thiwd-pawty u-usews of sowana s-sometimes n-nyeed to know the w-weaw-wowwd time a-a bwock
was pwoduced, σωσ g-genewawwy t-to meet compwiance wequiwements fow extewnaw auditows ow
waw enfowcement. -.- this p-pwoposaw descwibes a vawidatow timestamp owacwe t-that
wouwd awwow a sowana cwustew t-to satisfy this nyeed.

the genewaw outwine of the pwoposed impwementation i-is as fowwows:

- a-at weguwaw intewvaws, e-each vawidatow wecowds its obsewved time fow a known swot
  on-chain (via a-a timestamp added to a swot vote)
- a cwient can wequest a bwock time fow a wooted b-bwock using the `getBlockTime`
  wpc method. ^^;; w-when a cwient wequests a-a timestamp f-fow bwock ny:

  1. XD a-a vawidatow detewmines a "cwustew" timestamp f-fow a wecent timestamped swot
     befowe bwock n-ny by obsewving aww the timestamped vote instwuctions wecowded on
     the wedgew that wefewence t-that swot, 🥺 and detewmining t-the stake-weighted m-mean
     timestamp. òωó

  2. (ˆ ﻌ ˆ)♡ this w-wecent mean timestamp is then used to cawcuwate the timestamp o-of
     bwock n-ny using the cwustew's estabwished s-swot duwation

w-wequiwements:

- any vawidatow w-wepwaying the wedgew in the futuwe m-must come up with the same
  time fow evewy b-bwock since genesis
- estimated b-bwock times shouwd nyot dwift mowe t-than an houw o-ow so befowe wesowving
  to weaw-wowwd (owacwe) data
- the bwock times awe nyot contwowwed by a singwe centwawized owacwe, -.- but
  i-ideawwy based on a-a function that uses inputs fwom a-aww vawidatows
- e-each vawidatow m-must maintain a timestamp owacwe

the same impwementation can p-pwovide a timestamp estimate fow a nyot-yet-wooted
bwock. :3 howevew, ʘwʘ because the m-most wecent timestamped swot may o-ow may nyot be
w-wooted yet, 🥺 this t-timestamp wouwd be unstabwe (potentiawwy f-faiwing w-wequiwement
1). >_< i-initiaw impwementation w-wiww tawget wooted bwocks, ʘwʘ but if thewe i-is a use case
fow w-wecent-bwock t-timestamping, (˘ω˘) it w-wiww be twiviaw t-to add the wpc apis in the
futuwe. (✿oωo)

## wecowding time

at weguwaw i-intewvaws as it is voting on a pawticuwaw swot, (///ˬ///✿) each vawidatow
wecowds its obsewved time by incwuding a-a timestamp in its vote instwuction
submission. rawr x3 the cowwesponding s-swot f-fow the timestamp i-is the nyewest swot in the
vote v-vectow (`Vote::slots.iter().max()`). -.- it is s-signed by the v-vawidatow's
identity keypaiw as a usuaw vote. ^^ in owdew to enabwe this wepowting, (⑅˘꒳˘) the vote
stwuct n-nyeeds to be extended to incwude a-a timestamp fiewd, nyaa~~ `timestamp: Option<UnixTimestamp>`, /(^•ω•^) which wiww b-be set to `None` i-in most votes.

as of https://github.com/sowana-wabs/sowana/puww/10630, (U ﹏ U) v-vawidatows submit a-a
timestamp evewy vote. 😳😳😳 this e-enabwes impwementation o-of a bwock time caching
sewvice that awwows nyodes to cawcuwate the estimated t-timestamp i-immediatewy aftew
t-the bwock is wooted, >w< and cache t-that vawue in b-bwockstowe. XD this pwovides
pewsistent d-data and quick quewies, o.O whiwe stiww meeting wequiwement 1) above. mya

### vote a-accounts

a vawidatow's v-vote account wiww howd its most wecent s-swot-timestamp in v-votestate. 🥺

### vote pwogwam

the on-chain vote pwogwam nyeeds t-to be extended to pwocess a timestamp sent with
a vote instwuction fwom vawidatows. ^^;; i-in addition to its cuwwent pwocess_vote
functionawity (incwuding w-woading the c-cowwect vote account and vewifying that the
twansaction signew i-is the expected v-vawidatow), :3 this pwocess nyeeds to compawe the
timestamp and cowwesponding s-swot to the cuwwentwy s-stowed vawues to vewify that
they awe both monotonicawwy incweasing, (U ﹏ U) a-and stowe the nyew swot and t-timestamp in
t-the account. OwO

## cawcuwating stake-weighted m-mean timestamp

in owdew t-to cawcuwate t-the estimated t-timestamp fow a pawticuwaw bwock, 😳😳😳 a-a
vawidatow fiwst n-nyeeds to identify the most wecentwy timestamped s-swot:

```text
let timestamp_slot = floor(current_slot / timestamp_interval);
```#staking_utiws::staked_nodes_at_epoch()`.

Any validator replaying the ledger should derive the same stake-weighted mean
timestamp by processing the Timestamp transactions from the same number of
slots.

## Calculating Estimated Time for a Particular Block

Once the mean timestamp for a known slot is calculated, it is trivial to
calculate the estimated timestamp for subsequent block N:

`__###_4___###swots_pew_yeaw` s-stowed i-in each bank
