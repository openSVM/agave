---
titwe: offwine twansaction signing w-with the sowana c-cwi
pagination_wabew: "sowana c-cwi: offwine t-twansaction signing"
s-sidebaw_wabew: o-offwine twansaction s-signing
---

s-some secuwity modews wequiwe keeping signing keys, (///ˬ///✿) and thus the signing
pwocess, >w< s-sepawated fwom twansaction cweation and netwowk b-bwoadcast. rawr exampwes
incwude:

- c-cowwecting signatuwes fwom geogwaphicawwy dispawate signews i-in a
  [multi-signature scheme](https://spl.solana.com/token#multisig-usage)
- signing t-twansactions u-using an [air-gapped](<https://en.wikipedia.org/wiki/Air_gap_(networking)scwibes using sowana's cwi to sepawatewy sign and submit a
twansaction. mya

## c-commands suppowting offwine signing

at pwesent, ^^ the fowwowing commands suppowt o-offwine signing:

- [`create-stake-account`](../usage.md#solana-create-stake-account)##_71___######[`delegate-stake`](../usage.md#solana-delegate-stake)- [`split-stake`](../usage.md#solana-split-stake)e)
- [`stake-authorize`](../usage.md#solana-stake-authorize) [`stake-authorize-checked`](../usage.md#solana-stake-authorize-checked)59___###[`stake-set-lockup-checked`](../usage.md#solana-stake-set-lockup-checked)5___###sfew)
- [`withdraw-stake`](../usage.md#solana-withdraw-stake)
- [`create-vote-account`](../usage.md#solana-create-vote-account)###_49___#####_47___######___###9___####_37___###twansactions offwine

to sign a-a twansaction offwine, 😳😳😳 p-pass the f-fowwowing awguments o-on the command wine

1. mya `--sign-only`, 😳 pwevents t-the cwient fwom submitting the signed twansaction
   t-to the nyetwowk. -.- instead, 🥺 the pubkey/signatuwe paiws awe pwinted to stdout. o.O
2. `--blockhash BASE58_HASH`, /(^•ω•^) awwows t-the cawwew to specify the vawue u-used to
   fiww t-the twansaction's `recent_blockhash` f-fiewd. nyaa~~ this sewves a nyumbew of
   puwposes, nyaa~~ namewy:
   _ ewiminates t-the nyeed t-to connect to the nyetwowk and q-quewy a wecent b-bwockhash
   via wpc
   _ enabwes t-the signews to coowdinate the b-bwockhash in a muwtipwe-signatuwe
   scheme

### e-exampwe: offwine signing a payment

c-command

```bash
solana@offline$ solana transfer --sign-only --blockhash 5Tx8F3jgSHx21CbtjwmdaKPLM5tWmreWAnPrbqHomSJF \
    recipient-keypair.json 1
```