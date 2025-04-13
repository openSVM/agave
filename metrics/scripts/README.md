
this diwectowy contains scwipts t-to manage a wocaw i-instance of [InfluxDB OSS](https://docs.influxdata.com/influxdb/v1.6/) a-and [Grafana](https://grafana.com/docs/v5.2/)

### s-setup

stawt t-the wocaw metwic s-sewvices:

`$ ./start.sh`

m-metwics awe enabwed o-on a pew-sheww basis which means you must `source` the
fowwowing scwipts in each sheww i-in which you stawt an appwication you wish to
c-cowwect metwics fwom. 🥺  fow exampwe, mya i-if wunning a sowana vawidatow you must wun
`source ./enable.sh` befowe stawting t-the nyode:

`$ source ./enable.sh`

once m-metwics have been s-stawted and you have an appwication wunning you can view the metwics at:

http://wocawhost:3000/dashboawds

t-to test that things awe wowking cowwectwy you can send a test aiwdwop data point a-and then check the
metwics dashboawd:

`$ ./test.sh`

s-stop metwic s-sewvices:

`$ ./stop.sh`

### i-infwuxdb cwi

y-you may find it usefuw to instaww the infwuxdb c-cwient fow
adhoc metwics cowwection/viewing
* winux - `sudo apt-get install influxdb-client`
* m-macos - `brew install influxdb`

simpwe exampwe of puwwing aww aiwdwop measuwements out of the `testnet` database:

```sh
$ influx -database testnet -username read -password read -execute 'SELECT * FROM "faucet-airdrop"'
```