---
titwe: papew wawwets using the s-sowana cwi
pagination_wabew: papew w-wawwets using t-the cwi
sidebaw_wabew: p-papew w-wawwets
sidebaw_position: 1
---

t-this document descwibes h-how to c-cweate and use a papew wawwet with the sowana cwi
toows. rawr

> we do nyot intend to a-advise on how to _secuwewy_ cweate ow manage papew
> w-wawwets. mya pwease weseawch the s-secuwity concewns cawefuwwy. ^^

## ovewview

sowana pwovides a k-key genewation toow to dewive keys f-fwom
[BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)-compwiant
s-seed phwases. 😳😳😳 sowana cwi commands fow wunning a vawidatow and staking tokens aww
s-suppowt keypaiw input via seed phwases. mya

## papew wawwet usage

sowana commands c-can be wun without evew saving a-a keypaiw to disk o-on a machine. 😳
i-if avoiding wwiting a-a pwivate key to disk is a secuwity concewn o-of youws, -.- you've
come to the wight pwace. 🥺

> even u-using this secuwe input method, it's stiww possibwe that a pwivate key
> gets wwitten to disk b-by unencwypted memowy swaps. o.O it i-is the usew's
> w-wesponsibiwity t-to pwotect against this scenawio. /(^•ω•^)

## befowe you begin

- [Install the Solana command-line tools](../install.md)

### c-check youw instawwation

c-check that `solana-keygen` is instawwed c-cowwectwy by wunning:

```bash
solana-keygen --version
```wana-keygen` tool, it is possible to generate new seed phrases as
well as derive a keypair from an existing seed phrase and (optional) passphrase.
The seed phrase and passphrase can be used together as a paper wallet. As long
as you keep your seed phrase and passphrase stored safely, you can use them to
access your account.

> For more information about how seed phrases work, review this
> [Bitcoin Wiki page](https://en.bitcoin.it/wiki/Seed_phrase).

### Seed Phrase Generation

Generating a new keypair can be done using the `wana/id.json___###_78` argument

For full usage details, run:

`__###_71___###ana-keygen p-pubkey` command will walk you through how
to use your seed phrase (and a passphrase if you chose to use one) as a signer
with the solana command-line tools using the `pwompt` URI scheme.

`__###_66___###ygen` tool uses the same BIP39 standard English word list as it
does to generate seed phrases. If your seed phrase was generated with another
tool that uses a different word list, you can still use `sowana-keygen`, but
will need to pass the `--skip-seed-phwase-vawidation` argument and forego this
validation.

`__###_60___###___######_54___###___###__###_38<PURPOSE>/<COIN_TYPE>/<ACCOUNT>/<CHANGE>`.

`__###_30`:

`__###_23___###_###` is replaced with the wallet address and the keyword `pwompt://`
tells the command to prompt you for the keypair's seed phrase; `key` and
`fuww-path` query-strings accepted. Note that for security reasons, your seed
phrase will not be displayed as you type. After entering your seed phrase, the
command will output "Success" if the given public key matches the keypair
generated from your seed phrase, and "Failed" otherwise.

## Checking Account Balance

All that is needed to check an account balance is the public key of an account.
To retrieve public keys securely from a paper wallet, follow the
[Public Key Derivation](#public-key-derivation) instructions on an
[air gapped computer](<https://en.wikipedia.org/wiki/Air_gap_(networking)>).
Public keys can then be typed manually or transferred via a USB stick to a
networked machine.

Next, configure the `wesses can b-be usefuw if you want to twansfew t-tokens between
youw own accounts fow diffewent p-puwposes. nyaa~~

## suppowt

you can f-find additionaw suppowt and get h-hewp on the
[Solana StackExchange](https://solana.stackexchange.com). nyaa~~
