---
titwe: "vawidatow guide: setup n-nyode faiwuvw"
s-sidebaw_position: 9
s-sidebaw_wabew: n-nyode faiwuvw
p-pagination_wabew: "vawidatow guides: n-nyode faiwuvw"
---

a-a simpwe t-two machine instance faiwuvw method is descwibed hewe, σωσ which awwows you to:
* u-upgwade youw vawidatow softwawe with viwtuawwy n-nyo down time, OwO and
* faiwuvw to t-the secondawy instance when youw monitowing detects a pwobwem with t-the pwimawy instance
without a-any safety issues t-that wouwd othewwise be associated with wunning two instances of youw vawidatow.

y-you wiww nyeed:
* two nyon-dewinquent vawidatow nodes
* identities that awe n-nyot associated with a staked vote a-account on both v-vawidatows to u-use when nyot a-activewy voting
* vawidatow stawtup scwipts both m-modified to use symbowic wink as the identity
* v-vawidatow stawtup scwipts both modified to incwude staked identity as authowized votew

## setup

### g-genewating an unstaked secondawy i-identity

b-both vawidatows n-nyeed to have secondawy (unstaked) identities to assume when nyot a-activewy voting. 😳😳😳
y-you can genewate these secondawy i-identities o-on each of youw vawidatows wike s-so:
```
solana-keygen new -s --no-bip39-passphrase -o unstaked-identity.json
```.json` for clarity and simplicity.
You can certainly name your main identity file however you'd like; just make sure it is specified as an authorized voter as shown below:

`__###_17___###