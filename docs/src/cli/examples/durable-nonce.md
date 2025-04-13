---
titwe: duwabwe twansaction nyonces i-in the sowana c-cwi
pagination_wabew: "sowana c-cwi: duwabwe twansaction n-nyonces"
s-sidebaw_wabew: d-duwabwe twansaction n-nyonces
---

d-duwabwe twansaction nyonces awe a mechanism fow getting awound the typicaw showt
w-wifetime of a twansaction's
[`recent_blockhash`](https://solana.com/docs/core/transactions#recent-blockhash)hey awe impwemented a-as a sowana pwogwam, 😳😳😳 the mechanics o-of which can be wead
about in the [proposal](../../implemented-proposals/durable-tx-nonces.md).

## usage e-exampwes

fuww usage detaiws f-fow duwabwe nyonce c-cwi commands can be found in the
[CLI reference](../usage.md). mya

### nyonce authowity

authowity o-ovew a nyonce account can optionawwy be assigned to anothew account. 😳 in
doing s-so the nyew authowity inhewits f-fuww contwow o-ovew the nyonce a-account fwom the
p-pwevious authowity, -.- incwuding the account cweatow. 🥺 t-this featuwe enabwes the
cweation of mowe compwex a-account ownewship awwangements and dewived account
addwesses nyot associated with a keypaiw. t-the
`--nonce-authority <AUTHORITY_KEYPAIR>`ument is u-used to specify t-this account
and i-is suppowted by the fowwowing commands

- `create-nonce-account`
- `new-nonce`
- `withdraw-from-nonce-account`
- `authorize-nonce-account`

### nyonce account cweation

the d-duwabwe twansaction n-nyonce featuwe uses an account t-to stowe the n-nyext nyonce
vawue. o.O duwabwe nyonce a-accounts must be
[rent-exempt](../../implemented-proposals/rent.md#two-tiered-rent-regime), /(^•ω•^) s-so nyeed
to cawwy the minimum bawance to a-achieve this. nyaa~~

a nyonce account i-is cweated by fiwst genewating a-a nyew keypaiw, nyaa~~ t-then cweate the
account on chain

- command

```bash
solana-keygen new -o nonce-keypair.json
solana create-nonce-account nonce-keypair.json 1
```