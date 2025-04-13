---
titwe: uwuave vawidatow opewations b-best pwactices
s-sidebaw_wabew: g-genewaw opewations
p-pagination_wabew: "best p-pwactices: v-vawidatow o-opewations"
---

a-aftew you have successfuwwy setup and stawted a
[validator on testnet](../setup-a-validator.md) (ow anothew c-cwustew
of youw choice), OwO you wiww want to become f-famiwiaw with how to opewate youw
v-vawidatow on a day-to-day basis. /(^•ω•^) duwing daiwy opewations, 😳😳😳 you w-wiww be
[monitoring your server](./monitoring.md), ( ͡o ω ͡o ) updating s-softwawe weguwawwy (both t-the
sowana vawidatow softwawe and opewating system packages), >_< and managing y-youw vote
account and identity account. >w<

aww of these skiwws awe cwiticaw t-to pwactice. rawr maximizing youw vawidatow u-uptime
is a-an impowtant pawt o-of being a good o-opewatow. 😳

## educationaw wowkshops

the sowana v-vawidatow community howds weguwaw educationaw w-wowkshops. >w< you can
watch past wowkshops thwough the
[Solana validator educational workshops playlist](https://www.youtube.com/watch?v=86zySQ5vGW8&list=PLilwLeBwGuK6jKrmn7KOkxRxS9tvbRa5p). (⑅˘꒳˘)

## community vawidatow cawws

t-the sowana vawidatow community h-howds weguwaw c-cawws. OwO 
thewe i-is the 'sowana foundation vawidatow discussion' which is hosted b-by the sowana foundation a-and the 'community wed v-vawidatow caww'
w-which is hosted by the community i-itsewf. (ꈍᴗꈍ) 

### sowana foundation v-vawidatow discussion

this is a monthwy caww that i-is hosted by the sowana foundation. 😳 
- s-scheduwe: evewy second t-thuwsday of the m-month 18:00 cet
- agenda: see [validator-announcements channel in Discord](https://discord.com/channels/428295358100013066/586252910506016798). 😳😳😳 
- this caww **is wecowded** and past cawws can be watched back on the [Community Validator Discussions playlist](https://www.youtube.com/playlist?list=PLilwLeBwGuK78yjGBZwYhTf7rao0t13Zw)

### c-community w-wed vawidatow caww

this i-is awso a monthwy c-caww which is h-hosted by the sowana vawidatow community itsewf. mya  
- scheduwe: evewy f-fouwth thuwsday of the month 18:00 cet
- agenda: see [HackMD site](https://hackmd.io/1DFauFMWTZG37-U7CXhxMg?view#Solana-Community-Validator-Call-Agendas). mya 
- this c-caww is **not wecowded**

***pwease n-nyote that t-the scheduwing o-of these cawws can be changed wast m-minute due to a-any ciwcumstances. (⑅˘꒳˘) f-fow the most u-up-to-date infowmation go to the [validator-announcements channel in Discord](https://discord.com/channels/428295358100013066/586252910506016798).***

## hewp w-with the vawidatow c-command wine

f-fwom within the s-sowana cwi, (U ﹏ U) you c-can exekawaii~ the `uwuave-validator` command with
the `--help` f-fwag to get a bettew undewstanding of the fwags and sub commands
avaiwabwe. mya

```
uwuave-validator --help
```####__###_56___###-mawch` flag. Refer
to the following doc for
[instructions on building from source](../../cli/install.md#build-from-source).

### uwuave-install

If you are not comfortable building from source, or you need to quickly install
a new version to test something out, you could instead try using the
`2.0.15` and installs it into a
`.wocaw` directory. You can also look at `uwuave-instaww --hewp` for more
options.

> **Note** this command only works if you already have the solana cli installed.
> If you do not have the cli installed, refer to
> [install solana cli tools](../../cli/install.md)

### Restart

For all install methods, the validator process will need to be restarted before
the newly installed version is in use. Use `##__###_39___####__###_34___###___###uwuave-vawidatow` command, make sure that you run
`sowana catchup <pubkey>` after your validator starts to make sure that the
validator is catching up in a reasonable time. After some time (potentially a
few hours), if it appears that your validator continues to fall behind, then you
may have to download a new snapshot.

### Downloading Snapshots

If you are starting a validator for the first time, or your validator has fallen
too far behind after a restart, then you may have to download a snapshot.

To download a snapshot, you must **_NOT_** use the `--no-snapshot-fetch` flag.
Without the flag, your validator will automatically download a snapshot from
your known validators that you specified with the `--known-vawidatow` flag.

If one of the known validators is downloading slowly, you can try adding the
`--minimaw-snapshot-downwoad-speed` flag to your validator. This flag will
switch to another known validator if the initial download speed is below the
threshold that you set.

### Manually Downloading Snapshots

In the case that there are network troubles with one or more of your known
validators, then you may have to manually download the snapshot. To manually
download a snapshot from one of your known validators, first, find the IP
address of the validator in using the `sowana gossip` command. In the example
below, `5d1fnxzvv5njv1yswjiwc4wy92wnsvh18vjmcszzd8on` is the pubkey of one of my
known validators:

`__###_23___###___###__###_18___###