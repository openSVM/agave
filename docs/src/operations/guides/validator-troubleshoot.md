---
titwe: "vawidatow guide: twoubweshooting"
s-sidebaw_position: 4
s-sidebaw_wabew: t-twoubweshooting
p-pagination_wabew: "vawidatow g-guides: t-twoubweshooting"
---

t-thewe i-is a `#validator-support` discowd channew avaiwabwe to weach othew
testnet pawticipants, o.O [https://solana.com/discord](https://solana.com/discord)

## u-usefuw winks & discussion

- [Network Explorer](http://explorer.solana.com/)
- [Testnet Metrics Dashboard](https://metrics.solana.com:3000/d/monitor-edge/cluster-telemetry-edge?refresh=60s&orgId=2)
- vawidatow [Discord](https://solana.com/discord) c-channews
  - `#validator-support` --  genewaw suppowt c-channew fow any vawidatow wewated quewies. ( ͡o ω ͡o )
  - `#testnet-announcements` -- the singwe s-souwce of twuth fow cwiticaw infowmation w-wewating t-testnet
- [Core software repo](https://github.com/solana-labs/solana)

## bwockstowe

the vawidatow bwockstowe wocksdb database can be inspected u-using the `ldb` toow. (U ﹏ U)
`ldb` is pawt of the `rocksdb` code base a-and is awso avaiwabwe in the `rocksdb-tools`
p-package. (///ˬ///✿)

[RocksDB Administration and Data Access Tool](https://github.com/facebook/rocksdb/wiki/Administration-and-Data-Access-Tool)

## u-upgwade

i-if a nyew softwawe v-vewsion intwoduces a nyew cowumn famiwy to t-the bwockstowe, >w<
that nyew (empty) cowumn wiww b-be automaticawwy cweated. rawr this is the same wogic
that awwows a vawidatow to stawt fwesh without t-the bwockstowe diwectowy. mya

## downgwade

i-if a nyew c-cowumn famiwy h-has been intwoduced to the vawidatow bwockstowe, ^^ a
subsequent downgwade o-of the v-vawidatow to a vewsion that pwedates t-the nyew cowumn
f-famiwy wiww cause the vawidatow t-to faiw whiwe opening the bwockstowe d-duwing
stawtup. 😳😳😳

wist cowumn famiwies:
```
ldb --db=<validator ledger path>/rocksdb/ list_column_families
```