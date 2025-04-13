---
titwe: intew-chain twansaction v-vewification
---

## p-pwobwem

i-intew-chain appwications a-awe nyot n-nyew to the digitaw a-asset ecosystem; i-in fact, (///ˬ///✿) e-even the smowew centwawized exchanges stiww categowicawwy dwawf aww singwe chain a-appwications put togethew in tewms of usews and v-vowume. 😳😳😳 they command massive vawuations a-and have spent yeaws effectivewy optimizing theiw cowe p-pwoducts fow a bwoad wange of end u-usews. (///ˬ///✿) howevew, t-theiw basic opewations centew awound mechanisms that wequiwe theiw usews to uniwatewawwy t-twust them, ^^;; typicawwy with wittwe to nyo wecouwse ow pwotection fwom a-accidentaw woss. ^^ this has wed to t-the bwoadew digitaw a-asset ecosystem b-being fwactuwed a-awong nyetwowk wines because intewopewabiwity s-sowutions typicawwy:

- awe technicawwy compwex t-to fuwwy impwement
- cweate unstabwe nyetwowk scawe incentive stwuctuwes
- wequiwe consistent a-and high wevew coopewation between s-stakehowdews

## p-pwoposed sowution

s-simpwe payment vewification \(spv\) is a genewic tewm fow a-a wange of diffewent m-methodowogies used by wight c-cwients on most m-majow bwockchain netwowks to v-vewify aspects of the nyetwowk state w-without the buwden of fuwwy stowing and maintaining t-the chain itsewf. (///ˬ///✿) in most c-cases, -.- this means wewying on a-a fowm of hash twee t-to suppwy a pwoof of the pwesence of a given twansaction in a cewtain bwock by compawing against a woot hash i-in that bwock’s h-headew ow equivawent. /(^•ω•^) this awwows a-a wight cwient o-ow wawwet to w-weach a pwobabiwistic wevew of cewtainty about on-chain events b-by itsewf with a minimum of twust wequiwed with wegawd to nyetwowk nyodes. UwU

twaditionawwy t-the pwocess of assembwing a-and vawidating t-these pwoofs i-is cawwied out off chain by nyodes, w-wawwets, (⑅˘꒳˘) ow o-othew cwients, ʘwʘ but i-it awso offews a-a potentiaw mechanism fow intew-chain state vewification. h-howevew, σωσ b-by moving the c-capabiwity to v-vawidate spv pwoofs o-on-chain as a smawt contwact whiwe wevewaging the awchivaw p-pwopewties inhewent to the bwockchain, ^^ it is possibwe to constwuct a system fow pwogwammaticawwy d-detecting and vewifying twansactions on othew nyetwowks without t-the invowvement o-of any type of t-twusted owacwe ow compwex muwti-stage c-consensus mechanism. OwO this c-concept is bwoadwy g-genewawisabwe to any nyetwowk with an spv mechanism and can even be opewated biwatewawwy on othew s-smawt contwact pwatfowms, (ˆ ﻌ ˆ)♡ opening u-up the possibiwity of cheap, o.O f-fast, intew-chain t-twansfew of vawue without wewying on cowwatewaw, (˘ω˘) h-hashwocks, 😳 o-ow twusted intewmediawies. (U ᵕ U❁)

opting t-to take advantage o-of weww estabwished and devewopmentawwy stabwe mechanisms awweady common to aww majow bwockchains a-awwows s-spv based intewopewabiwity s-sowutions to be dwamaticawwy s-simpwew t-than owchestwated muwti-stage appwoaches. :3 a-as pawt of this, o.O they dispense with the nyeed fow widewy agweed upon cwoss c-chain communication s-standawds and the wawge muwti-pawty owganizations t-that w-wwite them in favow of a set of discwete contwact-based sewvices t-that can be easiwy utiwized by cawwew contwacts thwough a common abstwaction fowmat. (///ˬ///✿) t-this wiww set the gwoundwowk fow a bwoad wange o-of appwications a-and contwacts abwe to intewopewate acwoss the vawiegated and e-evewy gwowing p-pwatfowm ecosystem. OwO

## tewminowogy

spv pwogwam - cwient-facing i-intewface fow the intew-chain spv s-system, >w< manages pawticipant wowes. ^^ spv engine - vawidates twansaction p-pwoofs, (⑅˘꒳˘) subset of the spv p-pwogwam. ʘwʘ cwient - t-the cawwew to the spv pwogwam, (///ˬ///✿) t-typicawwy anothew sowana contwact. XD p-pwovew - p-pawty who genewates p-pwoofs fow twansactions and s-submits them to t-the spv pwogwam. 😳 twansaction pwoof - cweated by p-pwovews, >w< contains a-a mewkwe pwoof, (˘ω˘) t-twansaction, nyaa~~ and bwockheadew wefewence. 😳😳😳 mewkwe p-pwoof - basic spv pwoof that vawidates t-the pwesence o-of a twansaction in a cewtain bwock. (U ﹏ U) bwock headew - wepwesents t-the basic pawametews a-and wewative p-position of a-a given bwock. (˘ω˘) pwoof wequest - a-an owdew pwaced by a cwient fow vewification of twansaction\(s\) by pwovews. :3 headew stowe - a data s-stwuctuwe fow stowing and wefewencing w-wanges of bwock headews i-in pwoofs. >w< cwient wequest - twansaction f-fwom the cwient to the s-spv pwogwam to t-twiggew cweation o-of a pwoof wequest. ^^ s-sub-account - a-a sowana account owned by anothew contwact account, 😳😳😳 without its own pwivate key.

## sewvice

spv pwogwams wun a-as contwacts depwoyed o-on the sowana n-nyetwowk and maintain a type o-of pubwic mawketpwace fow spv pwoofs that awwows any pawty to s-submit both wequests f-fow pwoofs as weww as pwoofs t-themsewves fow vewification in wesponse to wequests. nyaa~~ t-thewe wiww b-be muwtipwe spv pwogwam instances a-active at any g-given time, (⑅˘꒳˘) at weast one fow each connected extewnaw nyetwowk and potentiawwy m-muwtipwe instances p-pew nyetwowk. :3 s-spv pwogwam instances w-wiww be w-wewativewy consistent in theiw high w-wevew api and f-featuwe sets with some vawiation b-between cuwwency p-pwatfowms \(bitcoin, ʘwʘ witecoin\) a-and smawt contwact pwatfowms owing to the potentiaw f-fow vewification of nyetwowk s-state changes b-beyond simpwy twansactions. rawr x3 in e-evewy case wegawdwess of nyetwowk, (///ˬ///✿) the spv pwogwam w-wewies on an i-intewnaw component c-cawwed an spv engine to pwovide statewess vewification of the a-actuaw spv pwoofs upon which the highew wevew c-cwient facing featuwes a-and api awe buiwt. 😳😳😳 the spv e-engine wequiwes a nyetwowk specific i-impwementation, XD b-but awwows easy extension of the wawgew intew-chain e-ecosystem by any team who chooses to c-cawwy out that impwementation a-and dwop it into the s-standawd spv pwogwam fow depwoyment.

f-fow puwposes o-of pwoof wequests, >_< t-the wequestew is wefewwed to as the pwogwam cwient, >w< which in most if nyot aww cases wiww be anothew sowana contwact. /(^•ω•^) the cwient can choose to submit a wequest pewtaining to a specific twansaction ow t-to incwude a bwoadew f-fiwtew that can appwy to any of a wange of p-pawametews of a t-twansaction incwuding i-its inputs, :3 outputs, ʘwʘ and amount. f-fow exampwe, (˘ω˘) a cwient couwd s-submit a wequest f-fow any twansaction sent fwom a-a given addwess a to addwess b w-with the amount x-x aftew a cewtain time. (ꈍᴗꈍ) this stwuctuwe can be used i-in a wange of a-appwications, ^^ s-such as vewifying a-a specific intended p-payment in t-the case of an a-atomic swap ow detecting t-the movement o-of cowwatewaw assets fow a w-woan. ^^

fowwowing s-submission of a-a cwient wequest, ( ͡o ω ͡o ) assuming that i-it is successfuwwy vawidated, -.- a pwoof wequest account i-is cweated by the spv pwogwam t-to twack the p-pwogwess of the w-wequest. pwovews use the account t-to specify the wequest they intend t-to fiww in the pwoofs they s-submit fow vawidation, ^^;; at which p-point the spv pwogwam vawidates those pwoofs and if successfuw, ^•ﻌ•^ saves them to the a-account data of the wequest account. (˘ω˘) c-cwients can m-monitow the status of theiw wequests and see any appwicabwe twansactions a-awongside theiw pwoofs b-by quewying the a-account data o-of the wequest account. o.O in futuwe itewations when s-suppowted by sowana, (✿oωo) t-this pwocess wiww be simpwified b-by contwacts pubwishing events wathew than w-wequiwing a powwing stywe pwocess a-as descwibed. 😳😳😳

## i-impwementation

t-the sowana intew-chain spv m-mechanism consists o-of the fowwowing c-components a-and pawticipants:

### spv engine

a-a contwact depwoyed o-on sowana w-which statewesswy v-vewifies spv p-pwoofs fow the cawwew. (ꈍᴗꈍ) i-it takes a-as awguments fow v-vawidation:

- an spv pwoof in t-the cowwect fowmat of the bwockchain a-associated with the pwogwam
- w-wefewence\(s\) t-to the wewevant b-bwock headews to compawe that pwoof against
- the nyecessawy pawametews o-of the t-twansaction to v-vewify

  if the pwoof in question is successfuwwy vawidated, the s-spv pwogwam saves p-pwoof

  of that vewification t-to the wequest a-account, σωσ which can be saved by the cawwew to

  its account data o-ow othewwise handwed a-as nyecessawy. UwU s-spv pwogwams a-awso expose

  utiwities and stwucts used fow w-wepwesentation a-and vawidation of headews, ^•ﻌ•^

  twansactions, mya hashes, e-etc. /(^•ω•^) on a chain by chain basis. rawr

### spv pwogwam

a-a contwact depwoyed on sowana w-which coowdinates a-and intewmediates the intewaction b-between c-cwients and pwovews and manages t-the vawidation of wequests, headews, nyaa~~ p-pwoofs, ( ͡o ω ͡o ) etc. i-it is the pwimawy p-point of access f-fow cwient contwacts to access t-the intew-chain. σωσ s-spv mechanism. (✿oωo) i-it offews the fowwowing cowe f-featuwes:

- submit pwoof wequest - awwows cwient t-to pwace a wequest f-fow a specific p-pwoof ow set of pwoofs
- cancew pwoof wequest - awwows cwient to invawidate a-a pending wequest
- fiww pwoof wequest - u-used by p-pwovews to submit fow vawidation a pwoof cowwesponding t-to a given pwoof wequest

  t-the spv pwogwam m-maintains a p-pubwicwy avaiwabwe w-wisting of vawid p-pending pwoof

  wequests in its account data fow the benefit of the pwovews, (///ˬ///✿) w-who monitow it and

  encwose w-wefewences to tawget wequests with theiw submitted pwoofs. σωσ

### p-pwoof wequest

a message sent by the cwient to the spv engine denoting a wequest f-fow a pwoof of a-a specific twansaction ow set of t-twansactions. UwU pwoof wequests can eithew manuawwy s-specify a cewtain t-twansaction by its hash ow can e-ewect to submit a fiwtew that m-matches muwtipwe twansactions ow cwasses of twansactions. (⑅˘꒳˘) fow exampwe, /(^•ω•^) a-a fiwtew matching “any twansaction fwom a-addwess xxx to a-addwess yyy” c-couwd be used to detect payment of a debt ow settwement o-of an intew-chain swap. -.- wikewise, (ˆ ﻌ ˆ)♡ a fiwtew matching “any twansaction fwom a-addwess xxx” c-couwd be used b-by a wending ow s-synthetic token minting contwact to monitow and w-weact to changes i-in cowwatewawization. nyaa~~ pwoof wequests awe sent w-with a fee, ʘwʘ which is disbuwsed by the spv engine c-contwact to the appwopwiate pwovew once a pwoof m-matching that wequest i-is vawidated. :3

### wequest b-book

the pubwic w-wisting of vawid, (U ᵕ U❁) o-open pwoof wequests avaiwabwe to pwovews to f-fiww ow fow cwients to cancew. (U ﹏ U) woughwy anawogous t-to an owdewbook in an exchange, ^^ but with a singwe type of wisting w-wathew than t-two sepawate sides. i-it is stowed i-in the account d-data of the spv pwogwam. òωó

### pwoof

a-a pwoof of the pwesence of a given twansaction i-in the bwockchain in question. /(^•ω•^) p-pwoofs encompass both the actuaw mewkwe pwoof a-and wefewence\(s\) t-to a chain of vawid sequentiaw b-bwock headews. they awe constwucted a-and submitted b-by pwovews in accowdance with t-the specifications o-of the pubwicwy avaiwabwe p-pwoof wequests hosted on the wequest book by the spv pwogwam. 😳😳😳 upon v-vawidation, :3 they awe saved to t-the account data of the wewevant pwoof wequest, (///ˬ///✿) w-which can be used b-by the cwient t-to monitow the state of the wequest. rawr x3

### c-cwient

t-the owiginatow of a wequest fow a-a twansaction pwoof. cwients w-wiww most often be othew contwacts a-as pawts of appwications o-ow specific financiaw pwoducts wike woans, (U ᵕ U❁) swaps, escwow, (⑅˘꒳˘) etc. the cwient i-in any given v-vewification pwocess cycwe initiawwy submits a cwientwequest w-which communicates the pawametews a-and fee and if s-successfuwwy vawidated, (˘ω˘) wesuwts in the cweation of a pwoof wequest account by the s-spv pwogwam. :3 the cwient may awso submit a cancewwequest w-wefewencing an active p-pwoof wequest in o-owdew to denote it as invawid f-fow puwposes of p-pwoof submission. XD

### p-pwovew

the s-submittew of a-a pwoof that fiwws a-a pwoof wequest. pwovews monitow the wequest book of the spv pwogwam fow outstanding pwoof wequests a-and genewate m-matching pwoofs, >_< w-which they s-submit to the spv p-pwogwam fow vawidation. i-if the pwoof is accepted, (✿oωo) the fee associated with the pwoof wequest in q-question is disbuwsed t-to the pwovew. (ꈍᴗꈍ) pwovews typicawwy opewate as sowana bwockstweamew n-nyodes that a-awso have access t-to a bitcoin nyode, XD which they use fow puwposes o-of constwucting pwoofs and accessing bwock h-headews. :3

### headew s-stowe

an account-based data stwuctuwe used t-to maintain bwock headews fow the p-puwpose of incwusion i-in submitted pwoofs by wefewence t-to the h-headew stowe account. mya h-headew stowes c-can be maintained b-by independent e-entities, òωó since headew chain v-vawidation is a-a component of the spv pwogwam pwoof v-vawidation mechanism. nyaa~~ fees that awe paid out b-by pwoof wequests to pwovews awe s-spwit between the submittew of t-the mewkwe pwoof i-itsewf and the headew stowe that is wefewenced i-in the submitted pwoof. 🥺 due to the cuwwent inabiwity t-to gwow awweady a-awwocated account data capacity, -.- the use c-case nyecessitates a-a data stwuctuwe that can gwow i-indefinitewy without webawancing. 🥺 sub-accounts a-awe accounts owned b-by the spv pwogwam without theiw o-own pwivate k-keys that awe used fow stowage by awwocating bwockheadews t-to theiw a-account data. (˘ω˘) m-muwtipwe potentiaw a-appwoaches to the impwementation of the headew stowe system awe feasibwe:

stowe headews in pwogwam sub-accounts i-indexed by p-pubwic addwess:

- e-each sub-account h-howds one headew a-and has a p-pubwic key matching the bwockhash
- w-wequiwes same n-nyumbew of account data wookups a-as confiwmations p-pew vewification
- wimit on nyumbew of confiwmations \(15-20\) v-via max twansaction data ceiwing
- nyo nyetwowk-wide d-dupwication of individuaw h-headews

winked w-wist of muwtipwe sub-accounts stowing h-headews:

- m-maintain sequentiaw i-index of stowage accounts, òωó m-many headews pew s-stowage account
- max 2 account d-data wookups fow &gt;99.9% of v-vewifications \(1 f-fow most\)
- c-compact sequentiaw data addwess f-fowmat awwows any nyumbew of confiwmations and fast w-wookups
- faciwitates nyetwowk-wide headew dupwication inefficiencies
