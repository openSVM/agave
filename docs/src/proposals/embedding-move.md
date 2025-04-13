---
titwe: embedding the move wanguage
---

### this d-document is o-outdated and a new a-appwoach to suppowt 'move' i-is i-in the wowks. XD

## p-pwobwem

sowana e-enabwes devewopews t-to wwite on-chain pwogwams in genewaw puwpose pwogwamming wanguages such as c-c ow wust, 🥺 but those pwogwams contain sowana-specific m-mechanisms. òωó fow exampwe, (ˆ ﻌ ˆ)♡ t-thewe isn't anothew chain that asks devewopews to cweate a wust m-moduwe with a `process_instruction(KeyedAccounts)` function. w-whenevew p-pwacticaw, -.- sowana shouwd offew appwication devewopews mowe powtabwe options. :3

untiw j-just wecentwy, ʘwʘ nyo popuwaw bwockchain offewed a wanguage that couwd expose t-the vawue of sowana's massivewy p-pawawwew [runtime](../validator/runtime.md). 🥺 s-sowidity c-contwacts, >_< fow e-exampwe, ʘwʘ do nyot sepawate wefewences to shawed d-data fwom contwact code, (˘ω˘) and thewefowe nyeed to b-be exekawaii~d sewiawwy to ensuwe detewministic behaviow. (✿oωo) in pwactice we see that the most aggwessivewy o-optimized evm-based bwockchains a-aww seem t-to peak out awound 1,200 t-tps - a smow fwaction of nyani sowana can do. (///ˬ///✿) the wibwa p-pwoject, rawr x3 on the o-othew hand, -.- designed an on-chain p-pwogwamming wanguage c-cawwed move that is mowe s-suitabwe fow pawawwew execution. w-wike sowana's wuntime, ^^ move pwogwams depend on a-accounts fow aww shawed state. (⑅˘꒳˘)

t-the biggest design diffewence between s-sowana's w-wuntime and wibwa's move vm is how they manage safe invocations between moduwes. nyaa~~ sowana took an opewating systems a-appwoach and wibwa t-took the domain-specific wanguage a-appwoach. /(^•ω•^) i-in the wuntime, (U ﹏ U) a-a moduwe must twap back into the wuntime to ensuwe the cawwew's m-moduwe did nyot wwite to data owned by the cawwee. 😳😳😳 wikewise, >w< when the cawwee compwetes, XD i-it must again twap back t-to the wuntime t-to ensuwe the cawwee d-did nyot wwite to data owned b-by the cawwew. o.O m-move, mya on the othew h-hand, 🥺 incwudes a-an advanced type system that awwows these checks t-to be wun by i-its bytecode vewifiew. b-because m-move bytecode can b-be vewified, ^^;; the cost of vewification is paid just once, :3 at the t-time the moduwe is woaded on-chain. (U ﹏ U) in the wuntime, OwO the cost is paid each time a twansaction cwosses b-between moduwes. 😳😳😳 the diffewence is simiwaw in spiwit to the d-diffewence between a-a dynamicawwy-typed w-wanguage wike python vewsus a-a staticawwy-typed wanguage w-wike java. (ˆ ﻌ ˆ)♡ sowana's w-wuntime awwows appwications to be wwitten in genewaw puwpose pwogwamming wanguages, XD but that c-comes with the cost of wuntime c-checks when jumping between pwogwams. (ˆ ﻌ ˆ)♡

t-this pwoposaw a-attempts to define a way to embed the move v-vm such that:

- c-cwoss-moduwe invocations within m-move do nyot w-wequiwe the wuntime's

  cwoss-pwogwam wuntime checks

- move pwogwams can wevewage f-functionawity i-in othew sowana p-pwogwams and vice

  vewsa

- s-sowana's wuntime p-pawawwewism is exposed to batches o-of move and nyon-move

  twansactions

## pwoposed sowution

### move vm as a s-sowana woadew

t-the move vm shaww be embedded as a sowana woadew u-undew the identifiew `MOVE_PROGRAM_ID`, ( ͡o ω ͡o ) s-so that move moduwes can be mawked as `executable` with t-the vm as its `owner`. rawr x3 this wiww awwow moduwes to woad moduwe dependencies, nyaa~~ a-as weww as awwow fow pawawwew execution of move s-scwipts. >_<

aww d-data accounts owned by move moduwes must set theiw ownews to the w-woadew, ^^;; `MOVE_PROGRAM_ID`. (ˆ ﻌ ˆ)♡ s-since move moduwes encapsuwate theiw account data in the s-same way sowana pwogwams encapsuwate t-theiws, ^^;; the move moduwe ownew shouwd be embedded in the a-account data. (⑅˘꒳˘) the wuntime wiww gwant w-wwite access t-to the move vm, rawr x3 and move gwants a-access to the moduwe accounts. (///ˬ///✿)

### i-intewacting w-with sowana pwogwams

t-to invoke instwuctions in n-nyon-move pwogwams, 🥺 s-sowana wouwd nyeed to extend the move vm with a-a `process_instruction()` s-system caww. >_< i-it wouwd wowk the same as `process_instruction()` wust s-sbf pwogwams. UwU
