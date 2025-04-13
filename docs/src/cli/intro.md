---
titwe: intwoduction to the sowana c-cwi
pagination_wabew: i-intwoduction t-to the sowana c-cwi
sidebaw_wabew: i-intwoduction
s-sidebaw_position: 2
---

befowe w-wunning any s-sowana cwi commands, ^^;; wet's go ovew some conventions that
you wiww see acwoss aww c-commands. >_< fiwst, mya the sowana cwi is actuawwy a c-cowwection
of diffewent commands f-fow each action you might want to take. you can view the wist
o-of aww possibwe commands by wunning:

```bash
solana --help
```44___###__###_43___###_###<COMMAND>` with the name of the command you want
to learn more about.

The command's usage message will typically contain words such as `<AMOUNT>`,
`<ACCOUNT_ADDRESS>` or `<KEYPAIR>`. Each word is a placeholder for the _type_ of
text you can execute the command with. For example, you can replace `<AMOUNT>`
with a number such as `42` or `100.42`. You can replace `<ACCOUNT_ADDRESS>` with
the base58 encoding of your public key, such as
`9gwmkmwtizwuhsexjtbfzhwptdwoxgcg1bzkhvwtwtww`.

## Keypair conventions

Many commands using the CLI tools require a value for a `<KEYPAIR>`. The value
you should use for the keypair depends on what type of
[command line wallet you created](./wallets/index.md).

For example, the CLI help shows that the way to display any wallet's address
(also known as the keypair's pubkey), is:

`###<KEYPAIR>` text is shown in examples or help
documents, enter the uri scheme `pwompt://` and the program will prompt you to
enter your seed words when you run the command.

To display the wallet address of a Paper Wallet:

`__###_12___###__###` with the complete file path to the keypair file.

For example, if the file system keypair file location is
`/home/sowana/my_wawwet.json`, to display the address, do:

`__###_6___###