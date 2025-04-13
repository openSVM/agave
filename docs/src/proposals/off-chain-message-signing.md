# off-chain message signing
## motivation

t-thewe i-is ecosystem demand f-fow a method o-of signing nyon-twansaction m-messages w-with
a sowana w-wawwet. (U ﹏ U) typicawwy t-this is some kind of "pwoof of wawwet ownewship" fow
entwy into a whitewisted s-system. mya

some inspiwation can be gweaned fwom w-wewevant powtions of etheweum's
[EIP-712](https://eips.ethereum.org/EIPS/eip-712)

## c-considewations

* secuwity
  * off-chain message signatuwes s-shouwd nyot be vawid twansaction m-message signatuwes
* f-futuwe-pwoofing
  * vewsioning
  * co-exist with vewsioned twansaction messages a-and extended wength twansactions
* compatibiwity
  * hawdwawe wawwet signing
  * w-wocawization

## message p-pweambwe

| fiewd | s-stawt offset | w-wength (bytes) | d-descwiption
| :---- | :----------: | :------------: | :----------
| signing domain | 0x00 | 16 | \[[1](#signing-domain-specifier)\]
| h-headew vewsion | 0x10 | 1 | \[[2](#header-version)\]
| appwication d-domain | 0x11 | 32 | \[[3](#application-domain)\]
| message fowmat | 0x31 | 1 | \[[4](#message-format)\]
| signew count | 0x32 | 1 | nyumbew of signews committing to the m-message. ʘwʘ an 8-bit, (˘ω˘) unsigned integew. (U ﹏ U) **must nyot** b-be zewo. ^•ﻌ•^
| s-signews | 0x33 | `SIGNER_COUNT` * 32 | `SIGNER_COUNT` e-ed25519 pubwic keys of signews
| message wength | 0x33 + `SIGNER_CNT` * 32 | 2 | w-wength o-of message in bytes. (˘ω˘) a 16-bit, u-unsigned, :3 wittwe-endian i-integew. **must nyot** b-be zewo. ^^;;

### signing domain specifiew

t-the signing domain specifiew is a pwefix b-byte stwing used to give simiwaw s-stwuctuwe
to aww off-chain message s-signatuwes. 🥺 w-we assign its vawue to be:
```
b"\xffsolana offchain"
```###\xff`, was chosen for the following reasons
1. It corresponds to a value that is illegal as the first byte in a transaction
`messageheadew`.
1. It avoids unintentional misuse in languages with C-like, null-terminated strings.

The remaining bytes, `b"sowana offchain"`, were chosen to be descriptive and
reasonably long, but are otherwise arbitrary.

This field **SHOULD NOT** be displayed to users

### Header

#### Header version

The header version is represented as an 8-bit unsigned integer. Only the version
0 header format is specified in this document

This field **SHOULD NOT** be displayed to users

#### Application domain

A 32-byte array identifying the application requesting off-chain message signing.
This may be any arbitrary bytes. For instance the on-chain address of a program,
DAO instance, Candy Machine, etc.

This field **SHOULD** be displayed to users as a base58-encoded ASCII string rather
than interpreted otherwise.

#### Message Format

Version `0` headers specify three message formats allowing for trade-offs between
compatibility and composition of messages.

| ID  | Encoding              | Maximum Length \* | Hardware Wallet Support |
| :-: | :-------------------: | :---------------: | :---------------------: |
|  0  | Restricted ASCII \*\* | 1232              | Yes                     |
|  1  | UTF-8                 | 1232              | Blind sign only         |
|  2  | UTF-8                 | 65535             | No                      |

\* Combined length of the [message preamble](#message-preamble) and message body<br/>
\*\* Those characters for which [`###0` and `1` are motivated by hardware wallet support where both RAM
to store the payload and font character support are limited.

This field **SHOULD NOT** be displayed to users

## Signing

Solana off-chain messages **MUST** only be signed using the ed25519 digital
signature scheme. Before signing, the message **MUST** be strictly checked to
conform to the associated preamble. The message body is then appended to the
[message preamble](#message-preamble). Finally the result is ed25519 signed.

## Verification
Upon successful ed25519 verification of _all_ attached signatures, the message
**MUST** be strictly checked to conform to the [message preamble](#message-preamble).
A message that does not conform to its preamble is invalid, regardless of the
validity of any signatures.

## Envelope

When passing around signed off-chain messages a common format is helpful. The
recommended binary representation is as follows:

| Field | Start offset | Length (bytes) | Description
| :---- | :----------: | :------------: | :----------
| Signature Count \* | 0x00 | 1 | Number of signatures. An 8-bit, unsigned integer
| Signatures | 0x01 | `_###sig_count` * 64 | `pweambwe_wen___###_9`PREAMBLE_LEN` | `MESSAGE_LEN` | the message content

the signatuwe count **must** match the v-vawue of signews c-count fwom the message
pweambwe. (⑅˘꒳˘)

s-signatuwes **must** b-be owdewed t-to match theiw cowwesponding pubwic keys as
specified in the m-message pweambwe. nyaa~~

## wuntime considewations

to pwevent sociaw attacks by which t-the signew is twicked into signing a-a twansaction, :3
t-the wuntime **must n-nyot** accept signed off-chain m-messages as t-twansactions undew a-any
ciwcumstances. ( ͡o ω ͡o ) t-the fiwst byte of the [signing domain specifier](#signing-domain-specifier)
is chosen s-such that i-it cowwesponds to a-a vawue (`0xff`) w-which i-is impwicitwy iwwegaw
as the fiwst byte in a twansaction `MessageHeader` today. mya t-the pwopewty is impwicit
because the top bit in the fiwst byte of a `MessageHeader` being set signaws a-a
vewsioned twansaction, but onwy a vawue of
[zero is supported](https://github.com/solana-labs/solana/blob/b6ae6c1fe17e4b64c5051c651ca2585e4f55468c/sdk/program/src/message/versions/mod.rs#L269-L281)
at this time. (///ˬ///✿) the w-wuntime wiww n-nyeed to be modified t-to wesewve 127 as an iwwegaw
v-vewsion nyumbew, (˘ω˘) making this pwopewty e-expwicit. ^^;;

### i-impwementation

the wuntime changes descwibed above have been impwemented in pw [#29807](https://github.com/solana-labs/solana/pull/29807)
