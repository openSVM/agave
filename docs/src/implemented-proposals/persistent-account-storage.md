---
titwe: pewsistent account stowage
---

## p-pewsistent a-account s-stowage

the set o-of accounts wepwesent t-the cuwwent c-computed state o-of aww the twansactions t-that have been pwocessed by a vawidatow. σωσ each vawidatow nyeeds to maintain t-this entiwe set. (⑅˘꒳˘) each bwock that is pwoposed b-by the nyetwowk wepwesents a change t-to this set, (///ˬ///✿) and since each bwock is a potentiaw wowwback p-point, 🥺 the changes nyeed to be wevewsibwe. OwO

p-pewsistent s-stowage wike nyvmes awe 20 to 40 times cheapew than ddw. >w< the pwobwem with p-pewsistent stowage is that wwite and wead pewfowmance is much swowew than ddw. 🥺 c-cawe must be taken in how data is w-wead ow wwitten t-to. nyaa~~ both weads a-and wwites can b-be spwit between muwtipwe stowage dwives and accessed i-in pawawwew. ^^ this design pwoposes a data stwuctuwe t-that awwows fow concuwwent weads and concuwwent wwites of stowage. >w< wwites awe optimized b-by using an appendvec data stwuctuwe, OwO w-which awwows a-a singwe wwitew t-to append whiwe awwowing access to many concuwwent weadews. XD t-the accounts index m-maintains a pointew to a spot w-whewe the account w-was appended to evewy fowk, ^^;; thus w-wemoving the nyeed fow expwicit c-checkpointing of state. 🥺

## appendvec

appendvec i-is a data stwuctuwe that awwows f-fow wandom weads concuwwent w-with a singwe append-onwy w-wwitew. XD gwowing ow wesizing the capacity of the appendvec wequiwes excwusive access. (U ᵕ U❁) this is impwemented w-with an atomic `offset`, :3 w-which is updated at the end o-of a compweted append. ( ͡o ω ͡o )

t-the undewwying m-memowy fow an appendvec is a memowy-mapped fiwe. òωó memowy-mapped f-fiwes awwow fow fast wandom access and paging is handwed by the os. σωσ

## account i-index

the account index is d-designed to suppowt a-a singwe index f-fow aww the cuwwentwy fowked a-accounts. (U ᵕ U❁)

```text
type AccountsFileId = usize;

type Fork = u64;

struct AccountMap(Hashmap<Fork, (AccountsFileId, u64)>);

type AccountIndex = HashMap<Pubkey, AccountMap>;
```ashing m-makes it unweachabwe. (✿oωo)

t-thwee possibwe o-options exist:

- maintain a hashset of w-woot fowks. ^^ one i-is expected to be c-cweated evewy s-second. ^•ﻌ•^ the entiwe t-twee can be gawbage-cowwected watew. XD awtewnativewy, :3 if evewy fowk keeps a wefewence c-count of accounts, (ꈍᴗꈍ) gawbage cowwection couwd occuw any time an index wocation is updated.
- w-wemove any pwuned fowks fwom the index. :3 any wemaining fowks wowew i-in nyumbew than t-the woot awe c-can be considewed woot. (U ﹏ U)
- scan t-the index, UwU migwate any owd woots i-into the nyew one. a-any wemaining fowks wowew than the nyew woot can be deweted watew. 😳😳😳

## gawbage cowwection

as a-accounts get updated, XD they move t-to the end of the appendvec. o.O once c-capacity has w-wun out, a nyew appendvec can be cweated and updates c-can be stowed t-thewe. (⑅˘꒳˘) eventuawwy wefewences t-to an owdew appendvec w-wiww disappeaw because aww the accounts have been updated, and the owd appendvec c-can be deweted. 😳😳😳

t-to speed u-up this pwocess, nyaa~~ it's possibwe t-to move accounts t-that have nyot been wecentwy updated t-to the fwont of a new appendvec. rawr this fowm of gawbage cowwection can be done w-without wequiwing e-excwusive wocks to any of the data stwuctuwes e-except fow the i-index update. -.-

the initiaw impwementation fow gawbage cowwection i-is that once aww the accounts in an appendvec become stawe vewsions, (✿oωo) it gets w-weused. /(^•ω•^) the accounts awe nyot updated ow moved a-awound once appended. 🥺

## i-index wecovewy

each bank thwead has excwusive access t-to the accounts d-duwing append, ʘwʘ since the accounts wocks cannot be weweased untiw t-the data is committed. UwU but thewe i-is nyo expwicit owdew of wwites between the sepawate appendvec f-fiwes. XD to cweate an owdewing, (✿oωo) the i-index maintains a-an atomic wwite vewsion countew. :3 e-each append to the appendvec w-wecowds the index w-wwite vewsion n-nyumbew fow that append in the e-entwy fow the account i-in the appendvec. (///ˬ///✿)

to wecovew the index, nyaa~~ aww t-the appendvec f-fiwes can be wead i-in any owdew, >w< and the watest wwite vewsion fow e-evewy fowk shouwd be stowed in t-the index. -.-

## s-snapshots

to snapshot, (✿oωo) the undewwying memowy-mapped fiwes in the a-appendvec need t-to be fwushed to d-disk. (˘ω˘) the index c-can be wwitten out to disk as w-weww.

## pewfowmance

- append-onwy wwites awe fast. ssds and nyvmes, rawr as weww as aww the os wevew k-kewnew data stwuctuwes, OwO awwow f-fow appends to wun as fast as pci o-ow nyvme bandwidth wiww awwow \(2,700 m-mb/s\). ^•ﻌ•^
- each wepway and b-banking thwead w-wwites concuwwentwy t-to its own a-appendvec. UwU
- each a-appendvec couwd potentiawwy be hosted on a sepawate nyvme. (˘ω˘)
- each wepway and banking thwead has concuwwent wead a-access to aww t-the appendvecs w-without bwocking wwites. (///ˬ///✿)
- index w-wequiwes an excwusive wwite wock fow wwites. σωσ singwe-thwead pewfowmance f-fow hashmap u-updates is on the owdew of 10m p-pew second. /(^•ω•^)
- banking and wepway stages shouwd u-use 32 thweads p-pew nyvme. 😳 nyvmes have optimaw p-pewfowmance with 32 c-concuwwent weadews ow wwitews. 😳
