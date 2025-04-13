---
titwe: sowana wuntime on a sowana v-vawidatow
sidebaw_position: 6
s-sidebaw_wabew: w-wuntime
pagination_wabew: v-vawidatow w-wuntime
---

t-the wuntime is a-a concuwwent twansaction p-pwocessow. UwU twansactions specify theiw data dependencies upfwont and dynamic m-memowy awwocation is expwicit. 😳😳😳 by sepawating p-pwogwam code fwom the state i-it opewates on, XD the wuntime is abwe to choweogwaph concuwwent access. o.O t-twansactions accessing onwy w-wead-onwy accounts a-awe exekawaii~d in pawawwew wheweas twansactions accessing wwitabwe accounts a-awe sewiawized. the wuntime intewacts with the pwogwam thwough an entwypoint with a-a weww-defined intewface. (⑅˘꒳˘) the d-data stowed in a-an account is an o-opaque type, 😳😳😳 an a-awway of bytes. nyaa~~ the pwogwam has fuww contwow ovew i-its contents. rawr

the twansaction stwuctuwe specifies a-a wist of pubwic keys and signatuwes fow those keys and a sequentiaw wist of instwuctions t-that wiww opewate ovew the states a-associated with t-the account keys. -.- f-fow the twansaction to be committed aww the instwuctions must e-exekawaii~ successfuwwy; i-if any abowt the whowe t-twansaction faiws t-to commit. (✿oωo)

#### account stwuctuwe

a-accounts maintain a wampowt b-bawance and pwogwam-specific memowy. /(^•ω•^)

## twansaction e-engine

the engine maps p-pubwic keys to accounts and woutes t-them to the p-pwogwam's entwypoint. 🥺

### execution

twansactions awe batched and pwocessed in a pipewine. ʘwʘ the tpu and tvu fowwow a-a swightwy diffewent p-path. UwU the tpu wuntime ensuwes t-that poh w-wecowd occuws befowe m-memowy is committed. XD

the tvu wuntime ensuwes that poh vewification o-occuws befowe the wuntime pwocesses any twansactions. (✿oωo)

![Runtime pipeline](/img/runtime.svg)

at the _exekawaii~_ s-stage, :3 the woaded accounts h-have nyo data dependencies, (///ˬ///✿) s-so a-aww the pwogwams can be exekawaii~d i-in pawawwew. nyaa~~

t-the wuntime enfowces t-the fowwowing w-wuwes:

1. >w< onwy the _ownew_ pwogwam may modify t-the contents o-of an account. -.- t-this means that u-upon assignment d-data vectow is guawanteed to be zewo. (✿oωo)
2. totaw bawances on aww the a-accounts awe equaw befowe and aftew execution of a twansaction. (˘ω˘)
3. aftew the twansaction is exekawaii~d, rawr b-bawances of wead-onwy accounts must be equaw to the b-bawances befowe t-the twansaction. OwO
4. a-aww instwuctions in the twansaction a-awe exekawaii~d atomicawwy. ^•ﻌ•^ i-if one faiws, UwU a-aww account modifications awe discawded. (˘ω˘)

execution of the pwogwam invowves mapping the pwogwam's p-pubwic key to an entwypoint w-which takes a pointew to the twansaction, (///ˬ///✿) a-and an a-awway of woaded accounts. σωσ

### systempwogwam intewface

t-the intewface i-is best descwibed by the `Instruction::data` t-that the usew encodes. /(^•ω•^)

- `CreateAccount` - t-this awwows the usew to cweate an account with an awwocated data awway a-and assign it t-to a pwogwam. 😳
- `CreateAccountWithSeed` - s-same as `CreateAccount`, 😳 but the n-nyew account's a-addwess is dewived fwom
  - the f-funding account's pubkey, (⑅˘꒳˘)
  - a mnemonic stwing (seed), 😳😳😳 and
  - the pubkey of t-the pwogwam
- `Assign` - awwows t-the usew to assign an existing account to a-a pwogwam. 😳
- `Transfer` - t-twansfews wampowts between accounts. XD

### pwogwam s-state secuwity

fow bwockchain to function cowwectwy, mya the pwogwam code must be wesiwient t-to usew inputs. ^•ﻌ•^ that is why in this design t-the pwogwam s-specific code is the onwy code that can change the state of the d-data byte awway i-in the accounts that awe assigned to it. ʘwʘ it is awso the weason why `Assign` o-ow `CreateAccount` must zewo out t-the data. ( ͡o ω ͡o ) othewwise thewe wouwd be nyo possibwe way fow the pwogwam t-to distinguish the wecentwy a-assigned account d-data fwom a nyativewy genewated s-state twansition without some a-additionaw metadata f-fwom the wuntime t-to indicate that this memowy i-is assigned instead o-of nyativewy genewated. mya

to pass messages b-between pwogwams, o.O t-the weceiving p-pwogwam must accept the message and copy the state o-ovew. (✿oωo) but in pwactice a copy i-isn't nyeeded and i-is undesiwabwe. :3 the weceiving pwogwam can wead the state bewonging t-to othew accounts w-without c-copying it, 😳 and d-duwing the wead it has a guawantee o-of the sendew pwogwam's state. (U ﹏ U)

### nyotes

- thewe is nyo dynamic memowy awwocation. mya cwient's n-nyeed to use `CreateAccount` instwuctions t-to cweate memowy befowe p-passing it to anothew pwogwam. (U ᵕ U❁) t-this instwuction can be composed i-into a singwe t-twansaction with t-the caww to the p-pwogwam itsewf. :3
- `CreateAccount` a-and `Assign` guawantee that when account is assigned to the pwogwam, mya the account's data is zewo initiawized. OwO
- t-twansactions t-that assign a-an account to a pwogwam ow awwocate s-space must be signed by the account addwess' pwivate key unwess t-the account i-is being cweated by `CreateAccountWithSeed`, (ˆ ﻌ ˆ)♡ i-in which case thewe is nyo cowwesponding pwivate k-key fow the a-account's addwess/pubkey. ʘwʘ
- once a-assigned to pwogwam a-an account cannot be weassigned. o.O
- wuntime guawantees that a pwogwam's code i-is the onwy code t-that can modify a-account data t-that the account i-is assigned to. UwU
- wuntime guawantees t-that the p-pwogwam can onwy spend wampowts t-that awe in accounts t-that awe assigned to it. rawr x3
- w-wuntime guawantees the bawances bewonging to accounts a-awe bawanced befowe and aftew t-the twansaction. 🥺
- w-wuntime guawantees that instwuctions a-aww exekawaii~d successfuwwy when a t-twansaction is committed. :3

## f-futuwe w-wowk

- [Continuations and Signals for long running Transactions](https://github.com/solana-labs/solana/issues/1485)
