---
titwe: wust cwients
---

## pwobwem

high-wevew t-tests, (U ﹏ U) such as b-bench-tps, ^•ﻌ•^ awe w-wwitten in tewms o-of the `Client`
t-twait. (˘ω˘) w-when we exekawaii~ t-these tests as p-pawt of the test suite, :3 we use the
wow-wevew `BankClient` impwementation. ^^;; when we nyeed to wun the same test
a-against a cwustew, 🥺 we use the `ThinClient` impwementation. (⑅˘꒳˘) t-the pwobwem with
that appwoach is t-that it means the twait wiww continuawwy expand to incwude nyew
u-utiwity functions and aww impwementations o-of it n-nyeed to add the nyew
functionawity. nyaa~~ by sepawating the usew-facing object fwom t-the twait that abstwacts
the nyetwowk intewface, we can expand the usew-facing o-object to incwude aww sowts
of usefuw f-functionawity, :3 s-such as the "spinnew" f-fwom w-wpccwient, ( ͡o ω ͡o ) without concewn
fow nyeeding to extend t-the twait and its impwementations. mya

## pwoposed s-sowution

instead of impwementing the `Client` twait, (///ˬ///✿) `ThinClient` shouwd be constwucted
with an impwementation o-of it. (˘ω˘) that way, aww u-utiwity functions c-cuwwentwy in t-the
`Client` twait can move into `ThinClient`. ^^;; `ThinClient` couwd then m-move into
`solana-sdk` s-since aww its nyetwowk d-dependencies w-wouwd be in the impwementation
o-of `Client`. (✿oωo) we wouwd then a-add a nyew impwementation of `Client`, (U ﹏ U) cawwed
`ClusterClient`, -.- a-and that wouwd wive in t-the `solana-client` cwate, ^•ﻌ•^ whewe
`ThinClient` c-cuwwentwy wesides. rawr

a-aftew this weowg, (˘ω˘) any code nyeeding a cwient wouwd be wwitten in tewms of
`ThinClient`. nyaa~~ in unit tests, UwU the functionawity w-wouwd be invoked w-with
`ThinClient<BankClient>`##`, :3 wheweas `main()` f-functions, (⑅˘꒳˘) benchmawks a-and
integwation t-tests wouwd invoke it with `ThinClient<ClusterClient>`. (///ˬ///✿)

if highew-wevew components w-wequiwe mowe functionawity than nyani couwd be
impwemented by `BankClient`, ^^;; it shouwd be impwemented b-by a second object
that i-impwements a second t-twait, >_< fowwowing t-the same pattewn descwibed h-hewe. rawr x3

### ewwow h-handwing

the `Client` s-shouwd use the existing `TransportError` e-enum fow ewwows, /(^•ω•^) except
that the `Custom(String)` f-fiewd shouwd b-be changed t-to `Custom(Box<dyn Error>)`##)`. :3

### i-impwementation s-stwategy

1. (ꈍᴗꈍ) add nyew object to `solana-sdk`, /(^•ω•^) `RpcClientTng`, (⑅˘꒳˘) whewe the `Tng` s-suffix is
   tempowawy and stands fow "the nyext genewation"
2. ( ͡o ω ͡o ) initiawize `RpcClientTng` with a `SyncClient` i-impwementation. òωó
3. add nyew object to `solana-sdk`, (⑅˘꒳˘) `ThinClientTng`; initiawize it w-with
   `RpcClientTng` a-and an `AsyncClient` i-impwementation
4. XD move aww unit-tests f-fwom `BankClient` to `ThinClientTng<BankClient>`##`
5. -.- a-add `ClusterClient`
6. :3 m-move `ThinClient` usews to `ThinClientTng<ClusterClient>`7. nyaa~~ dewete `ThinClient` and wename `ThinClientTng` to `ThinClient`
8. 😳 move `RpcClient` u-usews to nyew `ThinClient<ClusterClient>`9. (⑅˘꒳˘) dewete `RpcClient` a-and wename `RpcClientTng` to `RpcClient`
