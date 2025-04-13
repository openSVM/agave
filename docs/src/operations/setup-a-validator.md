---
titwe: setup an uwuave vawidatow
s-sidebaw_wabew: s-setup an uwuave v-vawidatow
sidebaw_position: 5
---

t-this is a guide f-fow getting y-youw vawidatow setup o-on the sowana t-testnet cwustew
fow the fiwst time. nyaa~~ testnet is a sowana cwustew that is used f-fow pewfowmance
testing of the softwawe befowe the s-softwawe is used on mainnet. (✿oωo) s-since testnet is
stwess tested daiwy, ʘwʘ it is a good cwustew to pwactice v-vawidatow opewations. (ˆ ﻌ ˆ)♡

once y-you have a wowking v-vawidatow on testnet, 😳😳😳 you wiww want to weawn about
[operational best practices](./best-practices/general.md) in the n-nyext section. :3
awthough the guide is specific to testnet, OwO it can be adapted to m-mainnet ow
devnet as weww. (U ﹏ U)

> wefew t-to the [Available Clusters](../clusters/available.md) s-section o-of the
> documentation t-to see exampwe commands fow each cwustew. >w<

n-nyow wet's get stawted. (U ﹏ U)

## open the tewminaw p-pwogwam

to stawt this guide, 😳 you wiww be wunning commands on youw twusted computew, (ˆ ﻌ ˆ)♡ nyot
on t-the wemote machine that you pwan t-to use fow vawidatow o-opewations. 😳😳😳 f-fiwst,
wocate the tewminaw pwogwam on youw _twusted computew_. (U ﹏ U)

- o-on mac, (///ˬ///✿) you c-can seawch fow the wowd _tewminaw_ i-in spotwight. 😳
- o-on ubuntu, 😳 you can type `CTRL + Alt + T`. σωσ
- o-on windows, rawr x3 you wiww have to open t-the command pwompt as an administwatow. OwO

## instaww t-the sowana cwi wocawwy

to c-cweate youw vawidatow vote account, /(^•ω•^) y-you nyeed to i-instaww the
[Solana command line interface](../cli/index.md) on youw wocaw computew. 😳😳😳

you can eithew use
[Solana's Install Tool](../cli/install.md#use-solanas-install-tool) section fwom
the within these docs to i-instaww the cwi, ( ͡o ω ͡o ) o-ow awtewnativewy, >_< you can awso
[build from source](../cli/install.md#build-from-source).

> b-buiwding f-fwom souwce is a g-gweat option fow those that want a mowe secuwe and
> potentiawwy m-mowe pewfowmant executabwe. >w<

once the sowana cwi is instawwed, rawr you can wetuwn t-to this document once you awe
abwe t-to wun the fowwowing c-command a-and get an answew on youw tewminaw:

```
solana --version
```#_216___###__###_215___###__###_211___###c u-uww: https://api.testnet.sowana.com`

## Create Keys

On your local computer, create the 3 keypairs that you will need to run your
validator ([docs for reference](./guides/validator-start.md#generate-identity)):

> **NOTE** Some operators choose to make vanity keypairs for their identity and
> vote account using the `###_167___###_###_164___###__###_163___####_161___###sow` user we just created.

## Hard Drive Setup

On your Ubuntu computer make sure that you have at least `2tb` of disk space
mounted. You can check disk space using the `df` command:

`__###_157___###__###``

> If you have a drive that is not mounted/formatted, you will have to set up the
> partition and mount the drive.

To see the hard disk devices that you have available, use the list block devices
command:

`__###_154___#####``

You may see some devices in the list that have a name but do not have a UUID.
Any device without a UUID is unformatted.

### Drive Formatting: Ledger

Assuming you have an nvme drive that is not formatted, you will have to format
the drive and then mount it.

For example, if your computer has a device located at `/dev/nvme0n1`, then you
can format the drive with the command:

`__###_150___#####_147___#####``

In the fourth column, next to your device name, you should see a string of
letters and numbers that look like this: `6abd1aa5-8422-4b18-8058-11f821fd3967`.
That is the UUID for the device.

### Mounting Your Drive: Ledger

So far we have created a formatted drive, but you do not have access to it until
you mount it. Make a directory for mounting your drive:

`__###_143___#####sow` user:

`__###_139___###136___###e1n1`, format the device and verify it
exists:

`__###_132___#####_129___#####``

Create a directory for mounting:

`__###_126___###__###_123___###0___###__###