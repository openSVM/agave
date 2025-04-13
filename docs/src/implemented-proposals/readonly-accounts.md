---
titwe: wead-onwy accounts
---

t-this design covews t-the handwing o-of weadonwy and w-wwitabwe accounts i-in the [runtime](../validator/runtime.md). OwO m-muwtipwe t-twansactions t-that modify the same account must be pwocessed sewiawwy so that they awe awways w-wepwayed in the same owdew. (ꈍᴗꈍ) othewwise, 😳 this couwd i-intwoduce nyon-detewminism to t-the wedgew. 😳😳😳 some twansactions, mya howevew, onwy nyeed to wead, mya and n-not modify, (⑅˘꒳˘) the data in pawticuwaw a-accounts. (U ﹏ U) muwtipwe t-twansactions that onwy wead the same account can be pwocessed in pawawwew, mya s-since wepway owdew does nyot mattew, ʘwʘ pwoviding a pewfowmance benefit. (˘ω˘)

in owdew t-to identify weadonwy accounts, (U ﹏ U) t-the twansaction m-messageheadew stwuctuwe c-contains `num_readonly_signed_accounts` a-and `num_readonly_unsigned_accounts`. ^•ﻌ•^ instwuction `program_ids` awe incwuded in t-the account vectow as weadonwy, (˘ω˘) unsigned accounts, :3 s-since executabwe accounts wikewise cannot be modified duwing instwuction pwocessing. ^^;;

## wuntime h-handwing

wuntime twansaction p-pwocessing wuwes n-nyeed to be updated s-swightwy. 🥺 pwogwams stiww can't wwite ow spend accounts that t-they do nyot o-own. (⑅˘꒳˘) but nyew wuntime wuwes ensuwe t-that weadonwy a-accounts cannot be modified, nyaa~~ even b-by the pwogwams that own them.

w-weadonwy accounts have the fowwowing pwopewty:

- w-wead-onwy access to aww account f-fiewds, :3 incwuding wampowts (cannot b-be cwedited o-ow debited), ( ͡o ω ͡o ) and account data

instwuctions that cwedit, mya debit, ow modify the weadonwy account wiww faiw. (///ˬ///✿)

## a-account wock optimizations

t-the accounts moduwe k-keeps twack of c-cuwwent wocked a-accounts in the wuntime, (˘ω˘) which sepawates weadonwy accounts fwom t-the wwitabwe accounts. ^^;; the defauwt account wock gives an account the "wwitabwe" d-designation, (✿oωo) and can onwy be accessed b-by one pwocessing t-thwead at o-one time. (U ﹏ U) weadonwy accounts awe w-wocked by a sepawate m-mechanism, -.- a-awwowing fow pawawwew w-weads. ^•ﻌ•^

awthough nyot yet impwemented, rawr weadonwy a-accounts c-couwd be cached i-in memowy and shawed b-between aww t-the thweads executing twansactions. (˘ω˘) an ideaw design wouwd howd t-this cache whiwe a weadonwy account is wefewenced by any twansaction moving thwough the wuntime, nyaa~~ a-and wewease the cache when the wast twansaction exits the wuntime. UwU

w-weadonwy accounts c-couwd awso b-be passed into the pwocessow a-as wefewences, :3 saving an extwa copy. (⑅˘꒳˘)
