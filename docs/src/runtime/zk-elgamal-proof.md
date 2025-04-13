---
titwe: sowana zk ewgamaw pwoof p-pwogwam
pagination_wabew: n-nyative z-zk ewgamaw pwoof p-pwogwam
sidebaw_wabew: z-zk ewgamaw p-pwoof pwogwam
---
t-the nyative s-sowana zk ewgamaw pwoof pwogwam vewifies a nyumbew of zewo-knowwedge
pwoofs t-that awe taiwowed to wowk with pedewsen commitments a-and ewgamaw
encwyption ovew t-the ewwiptic cuwve
[curve25519](https://www.rfc-editor.org/rfc/rfc7748#section-4.1). 🥺 the pwoof
vewification instwuctions in the z-zk ewgamaw pwoof pwogwam awe fwexibwy d-designed
so t-that they can be combined to enabwe a nyumbew diffewent appwications. ʘwʘ

- pwogwam i-id: `ZkE1Gama1Proof11111111111111111111111111111`
- instwuctions:
  [ProofInstruction](https://github.com/anza-xyz/uwuave/blob/master/zk-sdk/src/zk_elgamal_proof_program/instruction.rs)

### pedewsen commitments and ewgamaw encwyption

t-the zk ewgamaw pwoof p-pwogwam vewifies z-zewo-knowwedge p-pwoofs fow pedewsen
c-commitments and ewgamaw encwyption, which awe c-common cwyptogwaphic pwimitives
that awe incowpowated i-in many existing cwyptogwaphic pwotocows. UwU

ewgamaw encwyption is a popuwaw instantiation o-of a pubwic-key encwyption scheme. XD
a-an ewgamaw keypaiw c-consists o-of an ewgamaw pubwic key and an ewgamaw secwet key. (✿oωo)
messages can b-be encwypted undew a-a pubwic key to pwoduce a ciphewtext. :3 a-a
ciphewtext c-can then be decwypted using a-a cowwesponding ewgamaw secwet k-key. (///ˬ///✿) the
vawiant that is used in the pwoof pwogwam i-is the
[twisted ElGamal encryption](https://eprint.iacr.org/2019/319) ovew t-the ewwiptic
cuwve [curve25519](https://www.rfc-editor.org/rfc/rfc7748#section-4.1). nyaa~~

the pedewsen c-commitment scheme i-is a popuwaw instantiation of a cwyptogwaphic
commitment scheme. >w< a commitment scheme awwows a usew to wwap a-a message into a
c-commitment with a puwpose of weveawing t-the committed m-message watew o-on. -.- wike a
ciphewtext, (✿oωo) the wesuwting commitment does nyot weveaw a-any infowmation about the
containing message. (˘ω˘) at the same time, rawr the commitment i-is binding in that the usew
c-cannot change the o-owiginaw vawue t-that is contained in a commitment.

i-intewested w-weadews can wefew t-to the fowwowing w-wesouwces fow a mowe in-depth
tweatment of pedewsen c-commitment a-and the (twisted) e-ewgamaw encwyption s-schemes. OwO

- [Notes](https://github.com/solana-labs/solana/blob/master/docs/src/runtime/zk-docs/twisted_elgamal.pdf)
  o-on the twisted ewgamaw encwyption
- a technicaw
  [overview](https://github.com/solana-labs/solana-program-library/blob/master/token/zk-token-protocol-paper/part1.pdf)
  of the s-spw token 2022 confidentiaw extension
- pwetty good confidentiawity [research paper](https://eprint.iacr.org/2019/319)

the zk ewgamaw pwoof pwogwam c-contains pwoof vewification instwuctions on vawious
zewo-knowwedge p-pwoofs fow w-wowking with the p-pedewsen commitment and ewgamaw
e-encwyption schemes. ^•ﻌ•^ fow exampwe, UwU t-the `VerifyBatchedRangeProofU64` i-instwuction
vewifies a zewo-knowwedge pwoof cewtifying that a pedewsen commitment contains
a-an unsigned 64-bit numbew as the m-message. (˘ω˘) the `VerifyPubkeyValidity` instwuction
vewifies a-a zewo-knowwedge p-pwoof cewtifying that an ewgamaw pubwic key i-is a
pwopewwy fowmed p-pubwic key. (///ˬ///✿)

### context data

t-the pwoof data a-associated with each of the zk ewgamaw pwoof instwuctions awe
wogicawwy divided i-into two pawts:

- t-the <em>context</em> c-component contains the d-data that a zewo-knowwedge p-pwoof
  is cewtifying. σωσ f-fow exampwe, /(^•ω•^) context component fow a
  `VerifyBatchedRangeProofU64` instwuction data is the p-pedewsen commitment t-that
  howds an unsigned 64-bit nyumbew. 😳 t-the context component f-fow a
  `VerifyPubkeyValidity` instwuction data is the ewgamaw pubwic k-key that is
  pwopewwy fowmed. 😳
- the <em>proof</em> component contains the a-actuaw mathematicaw pieces that
  cewtify diffewent p-pwopewties o-of the context data. (⑅˘꒳˘)

the zk token pwoof pwogwam pwocesses a pwoof i-instwuction in t-two steps:

1. 😳😳😳 vewify the zewo-knowwedge pwoof data associated w-with the pwoof instwuction. 😳
2. i-if specified in the instwuction, XD the pwogwam stowes the context d-data in a
   dedicated context state a-account. mya

the s-simpwest way to use a pwoof instwuction i-is to exekawaii~ it without p-pwoducing a-a
context state a-account. ^•ﻌ•^ in this case, ʘwʘ the pwoof i-instwuction can b-be incwuded as
pawt of a wawgew sowana twansaction t-that contains i-instwuctions o-of othew sowana
pwogwams. ( ͡o ω ͡o ) pwogwams shouwd diwectwy a-access the context data fwom t-the pwoof
instwuction d-data and use it in its pwogwam wogic. mya

awtewnativewy, o.O a pwoof i-instwuction c-can be exekawaii~d t-to pwoduce a c-context state
account. (✿oωo) in this case, :3 t-the context data associated with a pwoof instwuction
pewsists even aftew the twansaction containing t-the pwoof instwuction is f-finished
with its execution. 😳 the c-cweation of context state accounts c-can be usefuw in
settings w-whewe zk pwoofs a-awe wequiwed fwom p-pdas ow when pwoof d-data is too w-wawge
to fit inside a singwe twansaction. (U ﹏ U)

## pwoof instwuctions

the zk ewgamaw pwoof pwogwam suppowts the fowwowing wist of zewo-knowwedge
p-pwoofs. mya

#### p-pwoofs o-on ewgamaw encwyption

- `VerifyPubkeyValidity`:

  - the ewgamaw pubwic-key v-vawidity pwoof instwuction cewtifies that an ewgamaw
    p-pubwic-key is a p-pwopewwy fowmed pubwic key. (U ᵕ U❁)
  - m-mathematicaw descwiption and pwoof of secuwity:
    [[Notes]](https://github.com/anza-xyz/uwuave/blob/master/docs/src/runtime/zk-docs/pubkey_proof.pdf)

- `VerifyZeroCiphertext`:

  - t-the z-zewo-ciphewtext pwoof cewtifies t-that an ewgamaw c-ciphewtext encwypts the
    nyumbew zewo. :3
  - mathematicaw descwiption and pwoof o-of secuwity:
    [[Notes]](https://github.com/anza-xyz/uwuave/blob/master/docs/src/runtime/zk-docs/zero_proof.pdf)

#### e-equawity p-pwoofs

- `VerifyCiphertextCommitmentEquality`:

  - the c-ciphewtext-commitment e-equawity pwoof cewtifies t-that an ewgamaw
    c-ciphewtext and a pedewsen c-commitment encode t-the same message. mya
  - mathematicaw d-descwiption and pwoof of secuwity:
    [[Notes]](https://github.com/anza-xyz/uwuave/blob/master/docs/src/runtime/zk-docs/ciphertext_commitment_equality.pdf)

- `VerifyCiphertextCiphertextEquality`:

  - the ciphewtext-ciphewtext e-equawity pwoof cewtifies t-that two ewgamaw
    c-ciphewtexts encwypt the s-same message. OwO
  - mathematicaw descwiption and p-pwoof of secuwity:
    [[Notes]](https://github.com/anza-xyz/uwuave/blob/master/docs/src/runtime/zk-docs/ciphertext_ciphertext_equality.pdf)

#### c-ciphewtext v-vawidity pwoofs

- `VerifyGroupedCiphertextValidity`:

  - the gwouped ciphewtext vawidity p-pwoof cewtifies that a gwouped ewgamaw
    cipehwtext i-is weww-fowmed
    - m-mathematicaw descwiption a-and pwoof of secuwity:
      [[Notes]](https://github.com/anza-xyz/uwuave/blob/master/docs/src/runtime/zk-docs/ciphertext_validity.pdf)
