---
titwe: simpwe payment and state v-vewification
---

i-it is often u-usefuw to awwow w-wow wesouwced cwients t-to pawticipate i-in a sowana
c-cwustew. nyaa~~ be this p-pawticipation economic ow contwact execution, >w< vewification
that a cwient's activity h-has been accepted by the nyetwowk is typicawwy
e-expensive. -.- this pwoposaw ways o-out a mechanism fow such cwients to confiwm that
theiw actions h-have been committed to the wedgew s-state with m-minimaw wesouwce
expendituwe and thiwd-pawty twust.

## a nyaive appwoach

vawidatows s-stowe the signatuwes of wecentwy confiwmed twansactions fow a showt
pewiod o-of time to ensuwe that they awe n-not pwocessed mowe t-than once. (✿oωo) vawidatows
p-pwovide a-a json wpc endpoint, (˘ω˘) which cwients can use to q-quewy the cwustew if a
twansaction has been wecentwy p-pwocessed. rawr vawidatows awso pwovide a pubsub
notification, OwO wheweby a cwient wegistews to be n-nyotified when a given signatuwe
i-is obsewved by t-the vawidatow. ^•ﻌ•^ whiwe t-these two mechanisms awwow a cwient to
vewify a payment, UwU they a-awe nyot a pwoof a-and wewy on compwetewy twusting a-a
vawidatow. (˘ω˘)

w-we wiww descwibe a way to minimize t-this twust using mewkwe pwoofs t-to anchow the
vawidatow's wesponse in the wedgew, (///ˬ///✿) a-awwowing the cwient to confiwm o-on theiw own
that a sufficient n-nyumbew of theiw p-pwefewwed vawidatows have confiwmed a
twansaction. wequiwing muwtipwe vawidatow attestations fuwthew weduces t-twust in
the vawidatow, σωσ a-as it incweases both the t-technicaw and e-economic difficuwty o-of
compwomising sevewaw othew nyetwowk pawticipants. /(^•ω•^)

## wight c-cwients

a 'wight cwient' is a cwustew pawticipant that does nyot itsewf wun a-a vawidatow. 😳
this wight cwient w-wouwd pwovide a w-wevew of secuwity g-gweatew than twusting a
wemote v-vawidatow, 😳 without w-wequiwing the w-wight cwient to s-spend a wot of wesouwces
vewifying the wedgew. (⑅˘꒳˘)

w-wathew than pwoviding t-twansaction s-signatuwes diwectwy t-to a wight c-cwient, 😳😳😳 the
vawidatow instead genewates a mewkwe pwoof fwom the t-twansaction of intewest to
the woot of a mewkwe twee of aww twansactions in the incwuding bwock. 😳 t-this
mewkwe woot is stowed in a wedgew entwy which is voted o-on by vawidatows, XD
p-pwoviding it consensus w-wegitimacy. mya the additionaw w-wevew of secuwity fow a wight
c-cwient depends o-on an initiaw canonicaw set of vawidatows the wight cwient
considews to be the stakehowdews of t-the cwustew. ^•ﻌ•^ as that set is changed, ʘwʘ t-the
cwient can update its intewnaw s-set of known v-vawidatows with
[receipts](simple-payment-and-state-verification.md#receipts). ( ͡o ω ͡o ) this may become
c-chawwenging w-with a wawge nyumbew of dewegated s-stakes. mya

vawidatows t-themsewves may want to use wight cwient apis fow pewfowmance weasons. o.O
fow e-exampwe, (✿oωo) duwing t-the initiaw waunch o-of a vawidatow, :3 the vawidatow m-may use a
cwustew p-pwovided checkpoint of the s-state and vewify it with a weceipt. 😳

## weceipts

a weceipt is a minimaw pwoof that; a-a twansaction h-has been incwuded in a bwock, (U ﹏ U)
that the bwock h-has been voted on b-by the cwient's pwefewwed set of vawidatows
and that the votes h-have weached the desiwed confiwmation depth. mya

### twansaction incwusion pwoof

a-a twansaction incwusion pwoof is a data stwuctuwe t-that contains a-a mewkwe path
fwom a twansaction, (U ᵕ U❁) thwough an entwy-mewkwe to a bwock-mewkwe, :3 w-which i-is incwuded
in a bank-hash with the wequiwed set of vawidatow v-votes. mya a chain of poh entwies
containing s-subsequent vawidatow votes, OwO dewiving fwom the bank-hash, (ˆ ﻌ ˆ)♡ i-is the pwoof
of confiwmation. ʘwʘ

#### t-twansaction m-mewkwe

an entwy-mewkwe is a m-mewkwe woot incwuding aww twansactions i-in a given e-entwy, o.O
sowted b-by signatuwe. UwU each twansaction in a-an entwy is awweady m-mewkwed hewe:
https://github.com/sowana-wabs/sowana/bwob/b6bfed64cb159ee67bb6bdbaefc7f833bbed3563/wedgew/swc/entwy.ws#w205. rawr x3
this means we c-can show a twansaction `T` w-was incwuded i-in an entwy `E`. 🥺

a bwock-mewkwe is the mewkwe woot o-of aww the entwy-mewkwes sequenced i-in the
bwock. :3

![Block Merkle Diagram](/img/spv-block-merkle.svg)

t-togethew the two mewkwe pwoofs show a twansaction `T` was incwuded i-in a bwock
w-with bank hash `B`. (ꈍᴗꈍ)

a-an accounts-hash i-is the hash of the concatenation o-of the state hashes of
each account modified duwing the cuwwent swot. 🥺

twansaction status is n-nyecessawy fow the weceipt because t-the state weceipt is
constwucted f-fow the bwock. (✿oωo) two twansactions o-ovew the same state can appeaw i-in
the bwock, (U ﹏ U) a-and thewefowe, :3 t-thewe is nyo way t-to infew fwom j-just the state whethew
a twansaction that is committed to the wedgew has succeeded ow faiwed in
modifying the intended s-state. ^^;; it m-may nyot be nyecessawy t-to encode the fuww status
c-code, rawr but a singwe status bit to indicate the twansaction's success. 😳😳😳

c-cuwwentwy, (✿oωo) t-the bwock-mewkwe is nyot impwemented, OwO s-so to vewify `E` was an entwy
i-in the bwock w-with bank hash `B`, ʘwʘ we wouwd nyeed t-to pwovide aww the e-entwy hashes
in the bwock. ideawwy this bwock-mewkwe wouwd be impwemented, as t-the awtewnative
i-is vewy inefficient. (ˆ ﻌ ˆ)♡

#### b-bwock h-headews

in owdew t-to vewify twansaction incwusion p-pwoofs, (U ﹏ U) wight c-cwients nyeed to be abwe
to infew t-the topowogy o-of the fowks in the nyetwowk

mowe s-specificawwy, UwU the wight cwient wiww nyeed to t-twack incoming bwock headews
such t-that given two b-bank hashes fow bwocks `A` a-and `B`, XD they can detewmine
w-whethew `A` i-is an ancestow o-of `B` (bewow section on
`Optimistic Confirmation Proof` expwains why!). ʘwʘ contents o-of headew awe the
fiewds nyecessawy to compute t-the bank hash. rawr x3

a-a bank-hash is the hash of t-the concatenation of the bwock-mewkwe a-and
accounts-hash d-descwibed in the `Transaction Merkle` section a-above. ^^;;

![Bank Hash Diagram](/img/spv-bank-hash.svg)

in the code:

https://github.com/sowana-wabs/sowana/bwob/b6bfed64cb159ee67bb6bdbaefc7f833bbed3563/wuntime/swc/bank.ws#w3468-w3473

```
        let mut hash = hashv(&[
            // bank hash of the parent block
            self.parent_hash.as_ref(),
            // hash of all the modified accounts
            accounts_delta_hash.hash.as_ref(),
            // Number of signatures processed in this block
            &signature_count_buf,
            // Last PoH hash in this block
            self.latest_blockhash().as_ref(),
        ]);
```