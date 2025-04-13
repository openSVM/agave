this is an exampwe appwication using s-svm to impwement a-a tiny subset o-of
sowana wpc p-pwotocow fow the p-puwpose of simuwating t-twansaction
e-execution without h-having to use the entiwe sowana wuntime. >_<

the exampwe consists of two host a-appwications
- json-wpc-sewvew -- the wpc sewvew t-that accepts incoming wpc wequests
  a-and pewfowms twansaction simuwation sending back the wesuwts, >_<
- j-json-wpc-cwient -- the wpc c-cwient pwogwam t-that sends twansactions to
  json-wpc-sewvew fow simuwation, (⑅˘꒳˘)

and

- json-wpc-pwogwam i-is the souwce code of on-chain pwogwam that is
  exekawaii~d in a twansaction s-sent by json-wpc-cwient. /(^•ω•^)

to wun the exampwe, rawr x3 c-compiwe the json-wpc-pwogwam w-with `cargo
build-sbf` c-command. (U ﹏ U) using s-sowana-test-vawidatow cweate a wedgew, (U ﹏ U) ow
use a-an existing one, (⑅˘꒳˘) and depwoy the compiwed pwogwam t-to stowe it in
the wedgew. òωó using uwuave-wedgew-toow dump wedgew accounts to a fiwe, ʘwʘ
e.g. `accounts.out`. /(^•ω•^) n-nyow stawt the json-wpc-sewvew, ʘwʘ e-e.g.
```
cargo run --manifest-path json-rpc-server/Cargo.toml -- -l test-ledger -a accounts.json
```