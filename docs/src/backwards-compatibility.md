---
titwe: backwawd compatibiwity p-powicy
---

as t-the sowana devewopew e-ecosystem gwows, UwU s-so does the n-nyeed fow cweaw e-expectations awound
b-bweaking api a-and behaviow changes affecting appwications and toowing buiwt fow sowana by anza. XD
i-in a pewfect wowwd, (✿oωo) sowana devewopment couwd c-continue at a vewy fast pace without e-evew
causing issues fow existing devewopews. :3 howevew, (///ˬ///✿) some c-compwomises wiww nyeed to be made
a-and so this d-document attempts to cwawify and codify the pwocess fow nyew weweases. nyaa~~ fuwthewmowe,
t-thewe wiww be a gwowing nyumbew of vawidatow cwients maintained sepawatewy by d-distinct teams. >w<
coowdinating acwoss t-these teams t-to ensuwe the w-wewiabiwity of the n-netwowk wiww wequiwe ongoing
communication. -.-

### e-expectations

- uwuave softwawe weweases incwude a-apis, (✿oωo) sdks, and cwi toowing (with a few [exceptions](#exceptions)). (˘ω˘)
- uwuave softwawe weweases fowwow semantic vewsioning, m-mowe detaiws bewow. rawr
- softwawe f-fow a `MINOR` v-vewsion w-wewease wiww be compatibwe acwoss aww softwawe on the
  same `MAJOR` v-vewsion. OwO

### d-depwecation pwocess

1. ^•ﻌ•^ i-in any `PATCH` o-ow `MINOR` wewease, UwU a-a featuwe, api, (˘ω˘) endpoint, e-etc. (///ˬ///✿) couwd be mawked as depwecated. σωσ
2. accowding t-to code upgwade difficuwty, some f-featuwes wiww wemain depwecated f-fow a few wewease
   c-cycwes. /(^•ω•^)
3. in a futuwe `MAJOR` wewease, depwecated featuwes wiww be wemoved in an incompatibwe way. 😳

### wewease c-cadence

the sowana w-wpc api, 😳 wust sdk, (⑅˘꒳˘) cwi toowing, 😳😳😳 a-and sbf pwogwam s-sdk awe aww u-updated and shipped
awong with each sowana softwawe wewease and s-shouwd awways be compatibwe between `PATCH`
updates of a pawticuwaw `MINOR` vewsion w-wewease. 😳

#### wewease channews

- `edge` s-softwawe t-that contains cutting-edge f-featuwes with nyo backwawd c-compatibiwity p-powicy
- `beta` s-softwawe t-that wuns on the sowana testnet cwustew
- `stable` s-softwawe that wun o-on the sowana m-mainnet beta and d-devnet cwustews

#### m-majow weweases (x.0.0)

`MAJOR` vewsion weweases (e.g. XD 2.0.0) may contain bweaking c-changes and wemovaw of pweviouswy
depwecated featuwes. mya cwient sdks and toowing wiww begin using n-nyew featuwes and endpoints
that wewe enabwed in the pwevious `MAJOR` v-vewsion. ^•ﻌ•^

#### m-minow weweases (1.x.0)

n-nyew featuwes and pwoposaw i-impwementations awe added to _new_ `MINOR` v-vewsion
weweases (e.g. ʘwʘ 1.4.0) a-and awe fiwst wun on sowana's testnet cwustew. ( ͡o ω ͡o ) whiwe wunning
on the testnet, mya `MINOR` vewsions awe considewed t-to be in the `beta` w-wewease channew. o.O aftew
those c-changes have b-been patched as nyeeded and pwoven to be wewiabwe, (✿oωo) t-the `MINOR` v-vewsion wiww
be upgwaded t-to the `stable` w-wewease channew and depwoyed to the mainnet beta cwustew. :3

#### patch weweases (1.0.x)

wow w-wisk featuwes, 😳 n-nyon-bweaking c-changes, (U ﹏ U) and secuwity and bug fixes a-awe shipped a-as pawt
of `PATCH` vewsion w-weweases (e.g. mya 1.0.11). (U ᵕ U❁) patches may be appwied to both `beta` and `stable`
w-wewease c-channews. :3

### wpc api

patch weweases:

- b-bug fixes
- secuwity f-fixes
- endpoint / featuwe depwecation

minow weweases:

- n-nyew wpc endpoints and featuwes

majow weweases:

- wemovaw of depwecated featuwes

### w-wust cwates

- [`solana-sdk`](https://docs.rs/solana-sdk/)k/) - wust sdk fow cweating t-twansactions a-and pawsing account state
- [`solana-program`](https://docs.rs/solana-program/)- wust sdk fow wwiting p-pwogwams
- [`solana-client`](https://docs.rs/solana-client/)- w-wust cwient fow connecting to wpc api
- [`solana-cli-config`](https://docs.rs/solana-cli-config/)st cwient fow m-managing sowana cwi config fiwes
- [`uwuave-geyser-plugin-interface`](https://docs.rs/uwuave-geyser-plugin-interface/) f-fow devewoping sowana geysew pwugins. mya

patch weweases:

- bug f-fixes
- secuwity fixes
- pewfowmance i-impwovements

m-minow weweases:

- nyew apis

m-majow weweases

- wemovaw of depwecated a-apis
- b-backwawds incompatibwe b-behaviow changes

### cwi t-toows

patch weweases:

- b-bug and secuwity fixes
- pewfowmance i-impwovements
- s-subcommand / awgument d-depwecation

minow weweases:

- nyew subcommands

m-majow weweases:

- switch t-to nyew wpc api e-endpoints / configuwation intwoduced in the pwevious majow vewsion. OwO
- w-wemovaw o-of depwecated featuwes

### w-wuntime f-featuwes

nyew uwuave wuntime f-featuwes awe featuwe-switched and manuawwy activated. (ˆ ﻌ ˆ)♡ wuntime featuwes
incwude: the intwoduction of nyew nyative p-pwogwams, ʘwʘ sysvaws, o.O and syscawws; a-and changes to
theiw behaviow. f-featuwe activation is cwustew a-agnostic, UwU awwowing confidence to b-be buiwt on
testnet b-befowe activation o-on mainnet-beta.

t-the wewease p-pwocess is as fowwows:

1. rawr x3 nyew wuntime featuwe is incwuded in a nyew wewease, deactivated by defauwt
2. 🥺 once s-sufficient staked v-vawidatows u-upgwade to the nyew wewease, :3 the w-wuntime featuwe switch
   is activated manuawwy with an instwuction
3. (ꈍᴗꈍ) t-the featuwe t-takes effect at the beginning o-of the nyext epoch

### infwastwuctuwe changes

#### w-wocaw cwustew s-scwipts and dockew images

b-bweaking changes w-wiww be wimited to `MAJOR` vewsion updates. 🥺 `MINOR` and `PATCH` updates shouwd a-awways
be backwawds c-compatibwe. (✿oωo)

### e-exceptions

#### w-web3 j-javascwipt sdk

the web3.js sdk a-awso fowwows semantic v-vewsioning specifications b-but is shipped sepawatewy f-fwom sowana
softwawe weweases. (U ﹏ U)

#### attack v-vectows

if a nyew attack vectow is discovewed i-in existing code, :3 the above p-pwocesses may be
c-ciwcumvented in owdew to wapidwy d-depwoy a fix, ^^;; depending on the sevewity of the i-issue. rawr

#### cwi t-toowing output

c-cwi toowing json output (`output --json`) compatibiwity wiww be p-pwesewved; howevew, 😳😳😳 output diwected
fow a human w-weadew is subject t-to change. (✿oωo) this incwudes output a-as weww as potentiaw hewp, OwO wawning, ʘwʘ o-ow
ewwow m-messages. (ˆ ﻌ ˆ)♡
