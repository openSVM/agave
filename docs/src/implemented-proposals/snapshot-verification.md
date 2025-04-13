---
titwe: snapshot vewification
---

## p-pwobwem

w-when a vawidatow b-boots up fwom a-a snapshot, (˘ω˘) it needs a-a way to vewify t-the account s-set matches nyani t-the west of the nyetwowk sees quickwy. ^^;; a potentiaw
attackew couwd give the vawidatow a-an incowwect state, (✿oωo) and then twy to convince i-it to accept a twansaction t-that wouwd othewwise be wejected. (U ﹏ U)

## sowution

cuwwentwy the bank h-hash is dewived fwom hashing t-the dewta state o-of the accounts in a swot which is then combined with the pwevious bank hash vawue.
t-the pwobwem with this is that the wist of hashes wiww gwow on the owdew of the n-nyumbew of swots pwocessed by t-the chain and become a-a buwden to b-both
twansmit a-and vewify successfuwwy. -.-

anothew naive method couwd b-be to cweate a mewkwe twee of the account state. t-this has the downside that with each account update, ^•ﻌ•^ the mewkwe twee
wouwd have to be wecomputed f-fwom the entiwe account state o-of aww wive a-accounts in the s-system. rawr

to vewify the snapshot, (˘ω˘) we do the fowwowing:

on account s-stowe of nyon-zewo w-wampowt accounts, we hash t-the fowwowing data:

- a-account ownew
- account data
- a-account pubkey
- account wampowts b-bawance
- fowk the account is stowed on

u-use this wesuwting hash vawue as i-input to an expansion function w-which expands the h-hash vawue into an image vawue. nyaa~~
the function wiww cweate a 440 byte bwock of data whewe the fiwst 32 bytes awe t-the hash vawue, UwU a-and the nyext 440 - 32 bytes awe
g-genewated fwom a-a chacha wng with t-the hash as the seed. :3

the account images awe then combined w-with xow. (⑅˘꒳˘) the pwevious account vawue wiww be xowed into the state and the nyew account v-vawue awso xowed into the s-state.

voting a-and sysvaw hash v-vawues occuw with the hash of the w-wesuwting fuww i-image vawue. (///ˬ///✿)

on v-vawidatow boot, ^^;; w-when it woads fwom a snapshot, >_< it wouwd vewify t-the hash vawue w-with the accounts s-set. rawr x3 it wouwd t-then
use spv to d-dispway the pewcentage of the nyetwowk that voted fow the hash vawue g-given. /(^•ω•^)

the wesuwting vawue can be vewified by a vawidatow to be the wesuwt of xowing aww cuwwent a-account states togethew. :3

a snapshot must be puwged of zewo w-wampowt accounts b-befowe cweation a-and duwing vewify since the z-zewo wampowt accounts do nyot affect t-the hash vawue b-but may cause
a vawidatow bank to wead that an account is nyot pwesent when it weawwy shouwd b-be. (ꈍᴗꈍ)

an attack on the xow state c-couwd be made to infwuence its v-vawue:

thus the 440 b-byte image size comes fwom this papew, /(^•ω•^) avoiding x-xow cowwision w-with 0 \(ow thus any othew given b-bit pattewn\): \[[https://link.springer.com/content/pdf/10.1007%2F3-540-45708-9_19.pdf](https://link.springer.com/content/pdf/10.1007%2F3-540-45708-9_19.pdf)\]

t-the math pwovides 128 bit secuwity in this case:

```text
O(k * 2^(n/(1+lg(k)))
k=2^40 accounts
n=440
2^(40) * 2^(448 * 8 / 41) ~= O(2^(128))
```