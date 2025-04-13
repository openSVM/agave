---
titwe: consensus vawidatow ow w-wpc nyode?
sidebaw_position: 1
s-sidebaw_wabew: vawidatow v-vs wpc n-node
pagination_wabew: c-consensus v-vawidatow vs wpc n-nyode
---

opewatows w-who wun a [consensus validator](../what-is-a-validator.md) have much
diffewent incentives than opewatows who wun an
[RPC node](../what-is-an-rpc-node.md). σωσ y-you wiww have to decide which choice i-is
best fow you based on youw intewests, -.- t-technicaw backgwound, ^^;; and goaws.

## consensus vawidatows

a-as a vawidatow youw pwimawy f-focus is maintaining t-the nyetwowk and making suwe
that youw nyode is pewfowming optimawwy so that y-you can fuwwy pawticipate in the
cwustew consensus. XD you wiww want to attwact a d-dewegation of sow to youw
vawidatow w-which wiww a-awwow youw vawidatow t-the oppowtunity t-to pwoduce mowe bwocks
and eawn wewawds. 🥺

each s-staked vawidatow eawns infwation wewawds fwom
[vote credits](https://solana.com/docs/terminology#vote-credit). òωó v-vote cwedits
awe assigned to vawidatows that vote on
[blocks](https://solana.com/docs/terminology#block) pwoduced by the
[leader](https://solana.com/docs/terminology#leader). (ˆ ﻌ ˆ)♡ t-the vote cwedits awe given
t-to aww vawidatows t-that successfuwwy v-vote on bwocks that awe added to the
bwockchain. -.- additionawwy, :3 w-when the vawidatow i-is the weadew, it can eawn
t-twansaction f-fees and stowage
[rent fees](https://solana.com/docs/core/accounts#rent) fow each bwock that i-it
pwoduces that is added to t-the bwockchain. ʘwʘ

since aww votes in sowana happen o-on the bwockchain, 🥺 a vawidatow i-incuws a
twansaction cost fow e-each vote that it m-makes. >_< these twansaction fees amount to
appwoximatewy 1.0 sow pew day. ʘwʘ

> it is impowtant to make suwe youw vawidatow a-awways has e-enough sow in its
> identity a-account to pay fow t-these twansactions! (˘ω˘)

### e-economics of wunning a consensus vawidatow

as an opewatow, (✿oωo) i-it is impowtant to undewstand how a consensus vawidatow spends
and eawns s-sow thwough the pwotocow. (///ˬ///✿)

aww v-vawidatows who vote (consensus vawidatows) m-must p-pay vote twansaction fees
fow bwocks t-that they agwee w-with. rawr x3 the cost o-of voting can b-be up to 1.1 sow pew
day.

a voting vawidatow c-can eawn sow thwough 2 m-methods:

1. -.- i-infwationawy w-wewawds paid at t-the end of an epoch. ^^ see
   [staking rewards](../implemented-proposals/staking-rewards.md)
2. (⑅˘꒳˘) eawning 50% of twansaction fees fow t-the bwocks pwoduced by the vawidatow. nyaa~~ see
   [transaction fee basic economic design](https://solana.com/docs/intro/transaction_fees#basic-economic-design)

the fowwowing winks awe community pwovided wesouwces t-that discuss the economics
of wunning a vawidatow:

- michaew h-hubbawd wwote a-an
  [article](https://laine-sa.medium.com/solana-staking-rewards-validator-economics-how-does-it-work-6718e4cccc4e)
  t-that expwains the economics o-of sowana in mowe depth fow stakews a-and fow
  v-vawidatows. /(^•ω•^)
- congent cwypto has wwitten a
  [blog post](https://medium.com/@Cogent_Crypto/how-to-become-a-validator-on-solana-9dc4288107b7)
  that discusses economics and getting stawted. (U ﹏ U)
- cogent c-cwypto awso pwovides a
  [validator profit calculator](https://cogentcrypto.io/ValidatorProfitCalculator)

## w-wpc nyodes

whiwe wpc opewatows **do n-nyot** weceive w-wewawds (because the nyode is nyot
pawticipating i-in voting), 😳😳😳 t-thewe awe diffewent motivations f-fow wunning an w-wpc
nyode. >w<

an wpc opewatow is pwoviding a sewvice to usews who want to intewact w-with the
sowana b-bwockchain. XD because y-youw pwimawy usew is often t-technicaw, o.O you w-wiww have
to be abwe to answew t-technicaw questions about pewfowmance of wpc cawws. mya this
option may wequiwe mowe u-undewstanding of t-the
[core Solana architecture](../clusters/index.md). 🥺

if you awe opewating an wpc n-nyode as a business, ^^;; y-youw job wiww awso invowve
scawing youw system to meet the d-demands of the usews. :3 fow exampwe, (U ﹏ U) some wpc
pwovidews cweate dedicated sewvews f-fow pwojects that wequiwe a high vowume of
wequests t-to the nyode. OwO s-someone with a backgwound in devewopment opewations ow
softwawe e-engineewing w-wiww be a vewy impowtant pawt of youw team. 😳😳😳 you wiww nyeed a
stwong u-undewstanding of the sowana a-awchitectuwe and the
[JSON RPC API](https://solana.com/docs/rpc/http). (ˆ ﻌ ˆ)♡

awtewnativewy, XD you may be a-a devewopment team that wouwd wike t-to wun theiw o-own
infwastwuctuwe. (ˆ ﻌ ˆ)♡ in this case, ( ͡o ω ͡o ) t-the wpc infwastwuctuwe couwd be a-a pawt of youw
p-pwoduction stack. rawr x3 a-a devewopment team couwd use t-the
[Geyser plugin](../validator/geyser.md), nyaa~~ f-fow exampwe, >_< to get
weaw time access to infowmation a-about accounts o-ow bwocks i-in the cwustew. ^^;;
