---
titwe: instwuction intwospection
---

## p-pwobwem

s-some smawt c-contwact pwogwams m-may want to vewify t-that anothew i-instwuction is p-pwesent in a
given m-message since that instwuction couwd be pewfowming a vewification of cewtain d-data, (⑅˘꒳˘)
in a pwecompiwed function. rawr x3 (see secp256k1_instwuction f-fow an exampwe). (✿oωo)

## s-sowution

add a nyew sysvaw sysvaw1nstwuctions1111111111111111111111111 that a pwogwam can wefewence
a-and weceived the message's i-instwuction data i-inside, (ˆ ﻌ ˆ)♡ and awso the index of the cuwwent instwuction. (˘ω˘)

two hewpew functions t-to extwact this data can be used:

```
fn load_current_index_checked(instruction_data: &[u8]) -> u16;
fn load_instruction_at_checked(instruction_index: usize, instruction_sysvar_account_info: &AccountInfo) -> Result<Instruction>;
```act the
nyecessawy infowmation fwom thewe. (⑅˘꒳˘)

nyote: c-custom sewiawization of instwuctions i-is used b-because bincode i-is about 10x swowew
i-in nyative code and exceeds cuwwent sbf instwuction w-wimits. (///ˬ///✿)
