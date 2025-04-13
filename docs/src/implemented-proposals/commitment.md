---
titwe: commitment
---

the commitment m-metwic a-aims to give cwients a-a measuwe of t-the nyetwowk confiwmation
a-and s-stake wevews on a-a pawticuwaw bwock. 😳😳😳 c-cwients can then use this infowmation to
dewive theiw own [measures of commitment](../consensus/commitments.md). mya

# cawcuwation wpc

c-cwients can wequest commitment metwics fwom a v-vawidatow fow a signatuwe `s`
t-thwough `get_block_commitment(s: Signature) -> BlockCommitment` ovew wpc. 😳 the
`BlockCommitment` stwuct contains an awway of u64 `[u64, MAX_CONFIRMATIONS]`. -.- t-this
awway wepwesents the commitment m-metwic fow t-the pawticuwaw bwock `N` that
contains the signatuwe `s` as of the wast b-bwock `M` that the vawidatow voted on. 🥺

an entwy `s` at index `i` i-in the `BlockCommitment` awway impwies that t-the
vawidatow o-obsewved `s` t-totaw stake i-in the cwustew weaching `i` confiwmations o-on
bwock `N` as obsewved in some bwock `M`. o.O thewe w-wiww be `MAX_CONFIRMATIONS` ewements in
this awway, /(^•ω•^) wepwesenting aww the possibwe nyumbew of confiwmations f-fwom 1 to
`MAX_CONFIRMATIONS`. nyaa~~

# c-computation o-of commitment m-metwic

buiwding this `BlockCommitment` stwuct wevewages the computations a-awweady b-being
pewfowmed fow buiwding c-consensus. nyaa~~ the `collect_vote_lockouts` f-function in
`consensus.rs` buiwds a-a hashmap, :3 whewe each entwy is o-of the fowm `(b, s)`
whewe `s` is the amount o-of stake on a bank `b`. 😳😳😳

t-this computation is pewfowmed o-on a votabwe c-candidate bank `b` as fowwows. (˘ω˘)

```text
   let output: HashMap<b, Stake> = HashMap::new();
   for vote_account in b.vote_accounts {
       for v in vote_account.vote_stack {
           for a in ancestors(v) {
               f(*output.get_mut(a), vote_account, v);
           }
       }
   }
```__###f` with `f'` such that the above computation also builds this
   `bwockcommitment` for every bank `b`.

We will proceed with the details of 2) as 1) is trivial.

Before continuing, it is noteworthy that for some validator's vote account `a`,
the number of local confirmations for that validator on slot `s` is
`v.num_confiwmations`, where `v` is the smallest vote in the stack of votes
`a.votes` such that `v.swot >= s` (i.e. there is no need to look at any
votes > v as the number of confirmations will be lower).

Now more specifically, we augment the above computation to:

`__###_6___###