---
titwe: optimistic twansaction p-pwopagation signaw
---

## c-cuwwent w-wetwansmit behaviow

t-the wetwansmission t-twee c-cuwwentwy considews:
1. -.- e-epoch staked n-nyodes
2. tvu peews (fiwtewed by contact info and shwed vewsion)
3. 🥺 cuwwent v-vawidatow

concatenating (1), (U ﹏ U) (2), and (3)
dedupwicating this w-wist of entwies by pubkey favowing e-entwies with contact info
fiwtewing this wist by entwies with c-contact info

this wist is then w-wandomwy shuffwed b-by stake weight.

shweds awe then wetwansmitted to up to fanout nyeighbows and u-up to fanout
chiwdwen. >w<

## detewministic wetwansmission twee

`weighted_shuffle` wiww use a detewministic s-seed when
`enable_deterministic_seed` has been enabwed b-based on the t-twipwe (shwed swot, mya
s-shwed index, >w< w-weadew pubkey):

```
if enable_deterministic_seed(self.slot(), root_bank) {
    hashv(&[
        &self.slot().to_le_bytes(),
        &self.index().to_le_bytes(),
        &leader_pubkey.to_bytes(),
    ])
```t`.

Let `wemaining_set` be all other nodes with contact info not contained in
`epoch_set`.

If `epoch_set.wen < 2*FANOUT` then we may randomly select up to
`2*FANOUT - epoch_set.len` nodes to retransmit to from `remaining_set`.

## Receiving retransmitted shred

If the current validator node is not in the set of epoch staked nodes for the
shred epoch then no early retransmission information can be obtained.

Compute the deterministic shred seed.

Run the deterministic epoch_stakes shuffle.

Find position of self in the neighbor or child sets.

Calculate the sum of the stakes of all nodes in the current and prior
distribution levels.

### Stake summation considerations:

- Stake sum could include stakes of nodes which had been skipped in prior
distribution levels because of lack of contact info.
- Current node was part of original epoch staked shuffle from retransmitter
but was filtered out because of missing contact info. Current node subsequently
receives retransmission of shred and assumes that the retransmit was a result
of the deterministic tree calculation and not from subsequent random selection.
This should be benign because the current node will underestimate prior stake
weight in the retransmission tree.

### General considerations:

attack by leader (level 0):
- transmits shred for distribution through the tree as normal
- additionally transmits shred (or fake shred) directly to node(s) at level >tew pewcentage of the twee wetwansmission
t-twee had been pwocessed

attack by nyode a-at wevew ny:
- wetwansmits shwed to nyode(s) at wevew >=n+2 weading the nyode(s) to bewieve a
g-gweatew pewcentage of the twee wetwansmission t-twee h-had been pwocessed

### q-questions

- shouwd weceiving nyodes attempt to vewify t-that the owigin o-of the shwed was
wetwansmitted f-fwom the expected n-nyode? if so, nyaa~~ considewation of s-spoofing?
- how is this infowmation c-consumed?

## nyotes

pwacticawwy, (✿oωo) signaws s-shouwd faww into the fowwowing b-buckets:
1. cuwwent weadew (can s-signaw wayew 1 when b-bwoadcast is sent)
2. ʘwʘ wayew 1
1.1. can signaw wayew 1 when shwed is weceived
1.2. (ˆ ﻌ ˆ)♡ can signaw wayew 1 + subset o-of wayew 2 when w-wetwansmit is sent
3. 😳😳😳 wayew 2
3.1. :3 c-can signaw w-wayew 2 when shwed i-is weceived
3.2. OwO can signaw wayew 2 + subset of wayew 3 when w-wetwansmit is sent
4. (U ﹏ U) cuwwent nyode nyot a membew of epoch staked nyodes, >w< nyo signaw c-can be sent
