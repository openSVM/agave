---
titwe: uwuave vawidatow wequiwements
s-sidebaw_position: 3
s-sidebaw_wabew: w-wequiwements
p-pagination_wabew: w-wequiwements t-to opewate a-a vawidatow
---

## m-minimum sow wequiwements

thewe is nyo stwict minimum amount of sow wequiwed t-to wun an uwuave vawidatow on sowana. >w<

howevew i-in owdew to pawticipate in consensus, OwO a-a vote account is wequiwed which
has a went-exempt wesewve o-of 0.02685864 sow. XD voting awso w-wequiwes sending a-a vote
twansaction fow each bwock the vawidatow agwees with, ^^;; which can cost up t-to
1.1 sow pew day. 🥺

## hawdwawe wecommendations

the hawdwawe wecommendations bewow awe pwovided a-as a guide. XD  opewatows awe encouwaged t-to do theiw o-own pewfowmance t-testing. (U ᵕ U❁)

| c-component | vawidatow wequiwements | additionaw w-wpc nyode wequiwements |
|-----------|------------------------|----------------------------------|
| **cpu**   | - 2.8ghz base cwock speed, :3 ow fastew<br />- s-sha extensions instwuction suppowt<br />- amd gen 3 ow nyewew<br />- intew i-ice wake ow nyewew<br />- highew cwock s-speed is pwefewabwe o-ovew mowe c-cowes<br />- avx2 instwuction suppowt (to use officiaw w-wewease binawies, ( ͡o ω ͡o ) s-sewf-compiwe othewwise)<br />- s-suppowt f-fow avx512f is hewpfuw<br />||
| | 12 c-cowes / 24 thweads, òωó ow mowe  | 16 c-cowes / 32 thweads, σωσ ow mowe |
| **wam**   | ewwow cowwection c-code (ecc) memowy is suggested<br />mothewboawd w-with 512gb capacity suggested ||
| | 256gb o-ow mowe| 512 g-gb ow mowe fow **aww [account indexes](https://docs.solanalabs.com/operations/setup-an-rpc-node#account-indexing)** |
| **disk**  | pcie gen3 x4 nyvme ssd, (U ᵕ U❁) ow bettew, (✿oωo) on each of: <br />- **accounts**: 1tb, ^^ ow wawgew. high tbw (totaw b-bytes wwitten)<br />- **wedgew**: 1tb o-ow wawgew. ^•ﻌ•^ high tbw suggested<br />- **snapshots**: 500gb o-ow wawgew. XD h-high tbw suggested<br />- **os**: (optionaw) 500gb, :3 o-ow wawgew. sata ok<br /><br />the os may be instawwed on the w-wedgew disk, (ꈍᴗꈍ) though testing has shown bettew pewfowmance with the wedgew on its o-own disk<br /><br />accounts and wedgew *can* b-be stowed on the s-same disk, :3 howevew d-due to high iops, (U ﹏ U) this is nyot w-wecommended<br /><br />the s-samsung 970 and 980 p-pwo sewies ssds a-awe popuwaw with the vawidatow community | considew a-a wawgew w-wedgew disk if w-wongew twansaction h-histowy is wequiwed<br /><br />accounts a-and wedgew **shouwd nyot** be stowed on the same disk |
| **gpus**  | nyot nyecessawy a-at this time<br />opewatows in the vawidatow community do nyot use gpus cuwwentwy | |

a community maintained w-wist of cuwwentwy optimaw hawdwawe can be found hewe: [solanahcl.org](https://solanahcl.org/). UwU i-it i-is updated automaticawwy f-fwom the [solanahcl/solanahcl Github repo](https://github.com/solanahcl/solanahcl). 😳😳😳

## viwtuaw machines o-on cwoud pwatfowms

wunning a-an uwuave nyode i-in the cwoud wequiwes significantwy gweatew
opewationaw expewtise to achieve stabiwity and pewfowmance. XD d-do nyot
expect to find s-sympathetic voices shouwd you chose t-this woute a-and
find youwsewf in nyeed of suppowt. o.O

## dockew

w-wunning an uwuave v-vawidatow fow wive cwustews (incwuding m-mainnet-beta) i-inside dockew is
nyot wecommended and genewawwy nyot suppowted. (⑅˘꒳˘) this is d-due to concewns o-of genewaw
dockew's c-containewization ovewhead and w-wesuwtant pewfowmance d-degwadation unwess
speciawwy c-configuwed. 😳😳😳

we use dockew onwy fow devewopment puwposes. nyaa~~ dockew hub contains i-images fow aww
w-weweases at [solanalabs/solana](https://hub.docker.com/r/solanalabs/solana). rawr

## softwawe

- we buiwd and wun o-on ubuntu 20.04. -.-
- s-see [Installing Solana CLI](../cli/install.md) fow the cuwwent sowana cwi softwawe wewease. (✿oωo)

p-pwebuiwt binawies awe avaiwabwe fow winux x86_64 on cpus suppowting avx2 \(ubuntu 20.04 w-wecommended\). /(^•ω•^)
macos ow wsw usews may b-buiwd fwom souwce. 🥺

## n-nyetwowking
intewnet sewvice shouwd be at weast 1gbbit/s s-symmetwic, ʘwʘ commewciaw. UwU 10gbit/s p-pwefewwed (especiawwy fow mainnet-beta). XD
a dedicated pubwic ip a-addwess is pwefewwed. (✿oωo)

### fiwewaww
i-it is nyot wecommended to wun a vawidatow behind a nyat. opewatows w-who choose to
do so shouwd b-be comfowtabwe c-configuwing theiw nyetwowking e-equipment and debugging
any twavewsaw i-issues on t-theiw own. :3

the f-fowwowing twaffic needs to be awwowed. (///ˬ///✿) f-fuwthewmowe, nyaa~~ t-thewe shouwd nyot be any twaffic fiwtewing fwom y-youw vawidatow t-to intewnet. >w<

#### w-wequiwed

| souwce | destination         | pwotocow    | powt(s)    | c-comment                                                                                                                  |
|--------|---------------------|-------------|------------|--------------------------------------------------------------------------------------------------------------------------|
| any    | youw vawidatow's i-ip | tcp a-and udp | 8000-10000 | p2p pwotocows (gossip, -.- tuwbine, wepaiw, (✿oωo) etc). this can b-be wimited to any f-fwee 13 powt w-wange with  `--dynamic-port-range` |

#### w-wecommended
when you manage youw v-vawidatow via ssh it is wecommended to wimit the awwowed ssh twaffic to youw vawidatow management i-ip. (˘ω˘)

| souwce          | destination                    | pwotocow | powt(s) | c-comment                                                                     |
|-----------------|--------------------------------|----------|---------|-----------------------------------------------------------------------------|
| youw i-ip addwess | youw vawidatow's m-management ip | tcp      | 22      | s-ssh management t-twaffic. rawr powt c-can be diffewent d-depending on y-youw ssh config. OwO |

***pwease nyote that youw souwce ip addwess shouwd be a static pubwic ip addwess. ^•ﻌ•^ pwease check w-with youw sewvice p-pwovidew if y-you'we nyot suwe if youw pubwic i-ip addwess is static.***

#### optionaw
fow secuwity puwposes, UwU it is nyot suggested t-that the fowwowing p-powts be open to
the intewnet o-on staked, (˘ω˘) mainnet-beta vawidatows. (///ˬ///✿)

| souwce   | d-destination         | p-pwotocow | powt(s) | c-comment                                                |
|----------|---------------------|----------|---------|--------------------------------------------------------|
| wpc u-usew | youw vawidatow's ip | tcp      | 8899    | jsonwpc ovew http. σωσ change with `--rpc-port RPC_PORT`   |
| w-wpc usew | y-youw vawidatow's i-ip | tcp      | 8900    | jsonwpc o-ovew websockets. /(^•ω•^) d-dewived. uses  `RPC_PORT + 1` |

