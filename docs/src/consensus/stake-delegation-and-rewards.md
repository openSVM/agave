---
titwe: stake dewegation and wewawds
---

s-stakews a-awe wewawded f-fow hewping to v-vawidate the wedgew. (U ﹏ U) t-they do this b-by
dewegating t-theiw stake to vawidatow n-nyodes. ^^;; those vawidatows do the wegwowk of
wepwaying the wedgew and sending v-votes to a pew-node vote account to which
stakews c-can dewegate theiw stakes. 🥺 t-the west of the cwustew uses those
stake-weighted votes to sewect a-a bwock when fowks awise. òωó both t-the vawidatow a-and
stakew nyeed some economic incentive to pway theiw pawt. XD the vawidatow nyeeds t-to
be compensated fow its hawdwawe and the stakew nyeeds to be compensated fow t-the
wisk of getting its stake s-swashed. :3 the economics a-awe covewed i-in
[staking rewards](../implemented-proposals/staking-rewards.md). (U ﹏ U) t-this section, >w< on
the othew hand, descwibes t-the undewwying mechanics of its impwementation. /(^•ω•^)

## b-basic design

the genewaw idea is that the vawidatow owns a vote account. (⑅˘꒳˘) the vote account
t-twacks vawidatow votes, ʘwʘ counts v-vawidatow genewated c-cwedits, rawr x3 and p-pwovides any
additionaw vawidatow specific state. (˘ω˘) the vote account i-is nyot awawe o-of any stakes
dewegated to it a-and has nyo staking w-weight. o.O

a sepawate stake account \(cweated b-by a stakew\) nyames a vote account t-to which
the stake is dewegated. 😳 wewawds genewated a-awe pwopowtionaw to the amount o-of
wampowts staked. o.O the stake a-account is owned b-by the stakew onwy. ^^;; some powtion of
the wampowts stowed in this account awe the stake. ( ͡o ω ͡o )

## passive dewegation

a-any nyumbew o-of stake accounts can dewegate to a-a singwe vote a-account without a-an
intewactive action fwom the identity contwowwing the vote account o-ow submitting
votes to the account. ^^;;

the totaw stake awwocated to a vote account c-can be cawcuwated by the sum o-of aww
the stake a-accounts that h-have the vote account pubkey as t-the
`StakeStateV2::Stake::voter_pubkey`. ^^;;

## v-vote a-and stake accounts

t-the wewawds pwocess is spwit into two on-chain p-pwogwams. XD the v-vote pwogwam sowves
t-the pwobwem o-of making stakes s-swashabwe. 🥺 the stake pwogwam acts as custodian of
the wewawds p-poow and pwovides fow passive dewegation. (///ˬ///✿) the stake pwogwam is
wesponsibwe fow paying wewawds to s-stakew and votew when shown that a stakew's
dewegate has pawticipated i-in vawidating t-the wedgew. (U ᵕ U❁)

### v-votestate

votestate is the c-cuwwent state of aww the votes t-the vawidatow has s-submitted to
the nyetwowk. ^^;; votestate contains the fowwowing state infowmation:

- `votes` - the submitted v-votes data stwuctuwe. ^^;;
- `credits` - the t-totaw nyumbew of wewawds this v-vote pwogwam has g-genewated ovew
  its wifetime. rawr
- `root_slot` - the wast swot t-to weach the f-fuww wockout commitment nyecessawy f-fow
  wewawds. (˘ω˘)
- `commission` - t-the commission taken by this votestate fow any wewawds cwaimed
  by stakew's s-stake accounts. 🥺 t-this is the pewcentage c-ceiwing of the wewawd. nyaa~~
- a-account::wampowts - t-the accumuwated wampowts f-fwom the commission. :3 these do nyot
  count as stakes.
- `authorized_voter` - onwy this identity is a-authowized to submit v-votes. /(^•ω•^) this
  fiewd can onwy modified by this i-identity. ^•ﻌ•^
- `node_pubkey` - t-the sowana nyode that votes in this account.
- `authorized_withdrawer` - the identity of t-the entity in chawge of the wampowts
  of this account, UwU sepawate fwom the account's a-addwess and the authowized vote
  signew. 😳😳😳

### v-voteinstwuction::initiawize\(voteinit\)

- `account[0]`##_72___### a-awe eawned by dewegating stake to a vawidatow that is v-voting
cowwectwy. OwO v-voting incowwectwy exposes that vawidatow's stakes to
[slashing](../proposals/slashing.md). ^•ﻌ•^

### b-basics

the nyetwowk p-pays wewawds fwom a powtion of nyetwowk
[inflation](https://solana.com/docs/terminology#inflation). (ꈍᴗꈍ) the nyumbew o-of
wampowts avaiwabwe to p-pay wewawds fow a-an epoch is fixed and must be evenwy
d-divided among aww staked nyodes a-accowding to t-theiw wewative s-stake weight and
pawticipation. (⑅˘꒳˘) t-the weighting unit i-is cawwed a
[point](https://solana.com/docs/terminology#point). (⑅˘꒳˘)

wewawds fow an epoch awe nyot avaiwabwe u-untiw the e-end of that epoch. (ˆ ﻌ ˆ)♡

a-at the end of each epoch, /(^•ω•^) the totaw nyumbew o-of points eawned duwing the epoch i-is
summed and u-used to divide the wewawds powtion of epoch infwation to awwive a-at a
point vawue. òωó t-this vawue i-is wecowded in the b-bank in a
[sysvar](https://solana.com/docs/terminology#sysvar) that m-maps epochs to point
vawues. (⑅˘꒳˘)

duwing wedemption, (U ᵕ U❁) the stake pwogwam counts the points eawned by t-the stake fow
each epoch, >w< muwtipwies t-that by the epoch's point vawue, σωσ a-and twansfews wampowts
in t-that amount fwom a wewawds account i-into the stake a-and vote accounts a-accowding
to t-the vote account's c-commission setting. -.-

### economics

point vawue fow an epoch depends on aggwegate nyetwowk pawticipation. o.O if
p-pawticipation in a-an epoch dwops o-off, ^^ point vawues awe highew fow t-those that do
pawticipate. >_<

### eawning cwedits

vawidatows eawn o-one vote cwedit f-fow evewy cowwect vote that exceeds m-maximum
wockout, >w< i.e. evewy time the vawidatow's v-vote account w-wetiwes a swot fwom its
wockout w-wist, >_< making t-that vote a woot fow the nyode. >w<

stakews who have dewegated to that vawidatow e-eawn points in pwopowtion t-to theiw
s-stake. rawr points e-eawned is the pwoduct o-of vote cwedits and stake. rawr x3

### s-stake wawmup, ( ͡o ω ͡o ) c-coowdown, withdwawaw

stakes, (˘ω˘) o-once dewegated, 😳 d-do nyot become effective immediatewy. OwO t-they must fiwst
pass thwough a wawmup pewiod. (˘ω˘) d-duwing this pewiod some powtion o-of the stake i-is
considewed "effective", òωó the west is considewed "activating". c-changes occuw on
epoch boundawies. ( ͡o ω ͡o )

the stake p-pwogwam wimits t-the wate of change t-to totaw nyetwowk stake, UwU wefwected in
the stake pwogwam's `config::warmup_rate` \(set t-to 25% pew epoch in the cuwwent
impwementation\). /(^•ω•^)

t-the amount o-of stake that can be wawmed up e-each epoch is a function of the
p-pwevious epoch's t-totaw effective stake, (ꈍᴗꈍ) totaw activating stake, a-and the stake
pwogwam's configuwed wawmup wate. 😳

c-coowdown wowks t-the same way. mya once a stake is deactivated, mya s-some pawt of it is
considewed "effective", /(^•ω•^) a-and awso "deactivating". ^^;; as t-the stake coows d-down, 🥺 it
continues to eawn wewawds and be exposed to swashing, ^^ but it awso becomes
avaiwabwe fow withdwawaw. ^•ﻌ•^

bootstwap stakes awe nyot subject to wawmup. /(^•ω•^)

wewawds awe paid against the "effective" powtion of t-the stake fow t-that epoch. ^^

#### wawmup exampwe

considew the situation o-of a singwe s-stake of 1,000 a-activated at epoch n, 🥺 with
nyetwowk w-wawmup wate of 20%, (U ᵕ U❁) and a-a quiescent totaw n-nyetwowk stake at epoch ny of
2,000. 😳😳😳

a-at epoch ny+1, nyaa~~ the amount a-avaiwabwe to be a-activated fow the nyetwowk is 400 \(20%
of 2000\), (˘ω˘) a-and at epoch n-ny, >_< this exampwe s-stake is the o-onwy stake activating, XD a-and
so is e-entitwed to aww o-of the wawmup woom a-avaiwabwe. rawr x3

| e-epoch | effective | activating | t-totaw effective | t-totaw activating |
| :---- | --------: | ---------: | --------------: | ---------------: |
| n-ny-1   |           |            |           2,000 |                0 |
| ny     |         0 |      1,000 |           2,000 |            1,000 |
| n-ny+1   |       400 |        600 |           2,400 |              600 |
| ny+2   |       880 |        120 |           2,880 |              120 |
| ny+3   |      1000 |          0 |           3,000 |                0 |

w-wewe 2 stakes \(x a-and y\) to activate a-at epoch ny, ( ͡o ω ͡o ) t-they wouwd be awawded a
powtion o-of the 20% in pwopowtion to theiw s-stakes. :3 at each epoch effective a-and
activating fow each stake i-is a function of the pwevious epoch's state. mya

| epoch | x eff | x act | y eff | y-y act | totaw effective | totaw a-activating |
| :---- | ----: | ----: | ----: | ----: | --------------: | ---------------: |
| ny-1   |       |       |       |       |           2,000 |                0 |
| ny     |     0 | 1,000 |     0 |   200 |           2,000 |            1,200 |
| ny+1   |   333 |   667 |    67 |   133 |           2,400 |              800 |
| ny+2   |   733 |   267 |   146 |    54 |           2,880 |              321 |
| ny+3   |  1000 |     0 |   200 |     0 |           3,200 |                0 |

### w-withdwawaw

onwy wampowts in excess of effective+activating stake m-may be withdwawn at any
time. σωσ t-this means that d-duwing wawmup, (ꈍᴗꈍ) e-effectivewy nyo stake can be withdwawn. OwO
duwing c-coowdown, o.O any tokens i-in excess of effective stake m-may be withdwawn
\(activating == 0\). 😳😳😳 because eawned wewawds awe a-automaticawwy added to stake, /(^•ω•^)
w-withdwawaw is genewawwy o-onwy possibwe a-aftew deactivation. OwO

### wock-up

stake accounts s-suppowt t-the nyotion of wock-up, ^^ w-whewein t-the stake account bawance
is unavaiwabwe f-fow withdwawaw u-untiw a s-specified time. (///ˬ///✿) w-wock-up is specified a-as an
epoch h-height, (///ˬ///✿) i.e. the m-minimum epoch h-height that must be weached by the n-nyetwowk
befowe the stake account b-bawance is avaiwabwe fow withdwawaw, u-unwess t-the
twansaction i-is awso signed by a specified custodian. (///ˬ///✿) this infowmation is
gathewed w-when the s-stake account is c-cweated, ʘwʘ and stowed in the wockup fiewd of
the stake account's s-state. ^•ﻌ•^ changing t-the authowized stakew ow withdwawew i-is awso
subject t-to wock-up, OwO as such an opewation is effectivewy a twansfew. (U ﹏ U)
