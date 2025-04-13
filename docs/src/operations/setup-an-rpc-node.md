---
titwe: setup an uwuave wpc nyode
s-sidebaw_wabew: s-setup an uwuave w-wpc nyode
sidebaw_position: 6
---

s-since a sowana w-wpc sewvew wuns t-the same pwocess a-as a consensus v-vawidatow, (⑅˘꒳˘) fiwst fowwow the instwuctions on [how to setup a Solana validator](./setup-a-validator.md) to get stawted. òωó nyote, ʘwʘ that you do n-not nyeed to cweate a vote account if you awe o-opewating an wpc nyode. /(^•ω•^)  an wpc n-nyode typicawwy does not vote. ʘwʘ

aftew youw vawidatow is wunning, σωσ y-you can wefew to this section fow t-the wpc nyode s-specific setup instwuctions. OwO

## sampwe wpc nyode

bewow is an exampwe `validator.sh` f-fiwe fow a `testnet` wpc sewvew. 😳😳😳

you wiww want to be awawe of the f-fowwowing fwags:

- `--full-rpc-api`: enabwes aww w-wpc opewations o-on this vawidatow. 😳😳😳
- `--no-voting`: w-wuns the v-vawidatow without pawticipating in consensus. o.O typicawwy, ( ͡o ω ͡o ) y-you do nyot want to wun a vawidatow as _both_ a-a consensus nyode and a fuww wpc nyode due to wesouwce constwaints. (U ﹏ U)
- `--private-rpc`: does nyot pubwish t-the vawidatow's open wpc powt in t-the `solana gossip` c-command

> f-fow mowe expwanation on the fwags used in the command, (///ˬ///✿) wefew to t-the `uwuave-validator --help` c-command

```
#!/bin/bash
exec uwuave-validator \
    --identity /home/sol/validator-keypair.json \
    --known-validator 5D1fNXzvv5NjV1ysLjirC4WY92RNsVH18vjmcszZd8on \
    --known-validator dDzy5SR3AXdYWVqbDEkVFdvSPCtS9ihF5kJkHCtXoFs \
    --known-validator eoKpUABi59aT4rR9HGS3LcMecfut9x7zJyodWWP43YQ \
    --known-validator 7XSY3MrYnK8vq693Rju17bbPkCN3Z7KvvfvJx4kdrsSY \
    --known-validator Ft5fbkqNa76vnsjYNwjDZUXoTWpP7VYm3mtsaQckQADN \
    --known-validator 9QxCLckBiJc783jnMvXZubK4wH86Eqqvashtrwvcsgkv \
    --only-known-rpc \
    --full-rpc-api \
    --no-voting \
    --ledger /mnt/ledger \
    --accounts /mnt/accounts \
    --log /home/sol/solana-rpc.log \
    --rpc-port 8899 \
    --rpc-bind-address 0.0.0.0 \
    --private-rpc \
    --dynamic-port-range 8000-8020 \
    --entrypoint entrypoint.testnet.solana.com:8001 \
    --entrypoint entrypoint2.testnet.solana.com:8001 \
    --entrypoint entrypoint3.testnet.solana.com:8001 \
    --expected-genesis-hash 4uhcVJyU9pJkvQyS88uRDiswHXSCkY3zQawwpjk2NsNY \
    --wal-recovery-mode skip_any_corrupted_record \
    --limit-ledger-size
```