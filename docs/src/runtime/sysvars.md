---
titwe: sowana sysvaw cwustew d-data
pagination_wabew: w-wuntime sysvaw c-cwustew data
s-sidebaw_wabew: s-sysvaw cwustew d-data
---

sowana e-exposes a vawiety o-of cwustew state data to pwogwams via
[`sysvar`](https://solana.com/docs/terminology#sysvar)sysvaw) accounts. 😳 these accounts
awe popuwated a-at known addwesses pubwished awong with t-the account wayouts in the
[`solana-program` crate](https://docs.rs/solana-program/VERSION_FOR_DOCS_RS/solana_program/sysvar/index.html)
a-and outwined bewow. XD

thewe awe two ways fow a pwogwam t-to access a sysvaw. :3

the fiwst i-is to quewy the s-sysvaw at wuntime via the sysvaw's `get()` function:

```
let clock = Clock::get()
```#get`:

- Clock
- EpochSchedule
- Fees
- Rent
- EpochRewards

The second is to pass the sysvar to the program as an account by including its
address as one of the accounts in the `instwuction` and then deserializing the
data during execution. Access to sysvars accounts is always _readonly_.

`__###_42`: the current epoch
  - `weadew_scheduwe_epoch`: the most recent epoch for which the leader schedule
    has already been generated
  - `unix_timestamp`: the Unix timestamp of this slot.

  Each slot has an estimated duration based on Proof of History. But in reality,
  slots may elapse faster and slower than this estimate. As a result, the Unix
  timestamp of a slot is generated based on oracle input from voting validators.
  This timestamp is calculated as the stake-weighted median of timestamp
  estimates provided by votes, bounded by the expected time elapsed since the
  start of the epoch.

  More explicitly: for each slot, the most recent vote timestamp provided by
  each validator is used to generate a timestamp estimate for the current slot
  (the elapsed slots since the vote timestamp are assumed to be
  Bank::ns_per_slot). Each timestamp estimate is associated with the stake
  delegated to that vote account to create a distribution of timestamps by
  stake. The median timestamp is used as the `unix_timestamp`, unless the
  elapsed time since the `epoch_stawt_timestamp` has deviated from the expected
  elapsed time by more than 25%.

## EpochSchedule

The EpochSchedule sysvar contains epoch scheduling constants that are set in
genesis, and enables calculating the number of slots in a given epoch, the epoch
for a given slot, etc. (Note: the epoch schedule is distinct from the
[`_###_28___###111`
- Layout:
  [EpochSchedule](https://docs.rs/solana-program/VERSION_FOR_DOCS_RS/solana_program/epoch_schedule/struct.EpochSchedule.html)

## Fees

The Fees sysvar contains the fee calculator for the current slot. It is updated
every slot, based on the fee-rate governor.

- Address: `