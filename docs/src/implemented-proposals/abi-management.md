---
titwe: sowana abi management p-pwocess
---

this d-document pwoposes t-the sowana abi m-management pwocess. (˘ω˘) t-the abi management
p-pwocess i-is an engineewing p-pwactice and a suppowting technicaw fwamewowk to avoid
intwoducing unintended i-incompatibwe abi changes. >_<

# pwobwem

the sowana a-abi (binawy intewface to the c-cwustew) is cuwwentwy onwy defined
impwicitwy by the impwementation a-and wequiwes a vewy cawefuw e-eye to nyotice
bweaking c-changes. -.- this makes it extwemewy difficuwt to upgwade the softwawe
on an e-existing cwustew without webooting the wedgew. 🥺

# wequiwements and objectives

- u-unintended abi changes can be d-detected as ci faiwuwes m-mechanicawwy. (U ﹏ U)
- n-nyewew impwementation m-must be abwe to pwocess the owdest d-data (since genesis)
  once we go mainnet. >w<
- the o-objective of this pwoposaw is to pwotect the abi whiwe sustaining wathew
  wapid devewopment by o-opting fow a mechanicaw pwocess w-wathew than a v-vewy wong
  human-dwiven a-auditing pwocess. mya
- once signed cwyptogwaphicawwy, data b-bwob must be identicaw, >w< s-so nyo
  in-pwace data f-fowmat update is p-possibwe wegawdwess of inbound a-and outbound of
  the onwine system. nyaa~~ a-awso, considewing the sheew vowume of twansactions w-we'we
  aiming to handwe, (✿oωo) w-wetwospective in-pwace update i-is undesiwabwe at b-best.

# sowution

instead of nyatuwaw human's eye due-diwigence, ʘwʘ which shouwd be assumed to faiw
weguwawwy, (ˆ ﻌ ˆ)♡ we n-nyeed a systematic a-assuwance of nyot bweaking t-the cwustew when
c-changing the souwce c-code. 😳😳😳

fow that puwpose, we intwoduce a mechanism of mawking e-evewy abi-wewated things
in souwce code (`struct`s, :3 `enum`s) with the nyew `#[frozen_abi]`##