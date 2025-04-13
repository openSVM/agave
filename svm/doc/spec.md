# sowana viwtuaw machine specification

# i-intwoduction

s-sevewaw components o-of the s-sowana vawidatow a-awe invowved in p-pwocessing
a twansaction (ow a b-batch of twansactions). (⑅˘꒳˘)  c-cowwectivewy, (///ˬ///✿) the
components wesponsibwe fow twansaction execution awe d-designated as
sowana viwtuaw machine (svm). 🥺 svm p-packaged as a stand-awone wibwawy
c-can be used in appwications outside the sowana vawidatow. OwO

this d-document wepwesents the svm specification. >w< i-it c-covews the api
of using svm in pwojects unwewated to sowana vawidatow and the
intewnaw w-wowkings of the svm, 🥺 incwuding the descwiptions of the innew
data fwow, nyaa~~ d-data stwuctuwes, ^^ and awgowithms i-invowved in the e-execution
of twansactions. >w< t-the document’s t-tawget audience incwudes both extewnaw
u-usews and the devewopews of the svm. OwO

## use c-cases

we envision the fowwowing appwications fow svm

- **twansaction execution in sowana vawidatow**

    t-this is the pwimawy u-use case fow the s-svm. XD it wemains a-a majow
    component of the uwuave vawidatow, ^^;; but with cweaw intewface a-and
    i-isowated fwom dependencies on othew c-components. 🥺

    t-the svm is cuwwentwy viewed a-as weawizing two stages of the
    t-twansaction engine execution pipewine as descwibed i-in sowana
    awchitectuwe d-documentation
    [https://docs.solana.com/validator/runtime#execution](https://docs.solana.com/validator/runtime#execution), XD
    nyamewy ‘woad a-accounts’ a-and ‘exekawaii~’ stages. (U ᵕ U❁)

- **svm wowwups**

    wowwups that nyeed to exekawaii~ a bwock but don’t n-nyeed the othew
    c-components of the vawidatow c-can benefit fwom s-svm, :3 as it can w-weduce
    hawdwawe wequiwements and decentwawize the nyetwowk. ( ͡o ω ͡o ) t-this is
    especiawwy usefuw fow ephemewaw wowwups since the cost of compute
    w-wiww be highew as a nyew wowwup i-is cweated fow e-evewy usew session
    i-in appwications wike gaming. òωó

- **svm f-fwaud p-pwoofs fow diet c-cwients**

    a-a succinct pwoof of an invawid state twansition b-by the supewmajowity (simd-65)

- **vawidatow s-sidecaw fow json-wpc**

    t-the w-wpc nyeeds to be s-sepawated fwom the vawidatow. σωσ
    `simulateTransaction` wequiwes wepwaying the twansactions a-and
    accessing nyecessawy account data. (U ᵕ U❁)

- **svm-based avawanche subnet**

    the svm wouwd nyeed to b-be isowated to wun within a subnet since the
    consensus and n-nyetwowking functionawity w-wouwd w-wewy on avawanche
    moduwes. (✿oωo)

- **modified s-svm (svm+)**

    an svm type with a-aww the cuwwent f-functionawity and extended
    instwuctions fow custom use cases. ^^ this wouwd fowm a supewset of
    t-the cuwwent svm. ^•ﻌ•^

# system c-context

in this section, XD svm is w-wepwesented as a-a singwe entity. :3 we descwibe its
intewfaces to the p-pawts of the s-sowana vawidatow extewnaw to svm. (ꈍᴗꈍ)

i-in the context o-of sowana vawidatow, :3 the main entity extewnaw to svm is
bank. (U ﹏ U) it cweates an svm, UwU s-submits twansactions f-fow execution a-and
weceives wesuwts of twansaction e-execution f-fwom svm. 😳😳😳

![context diagram](/svm/doc/diagrams/context.svg "System Context")

## intewfaces

i-in this section, XD we descwibe the api of using the svm both in sowana
vawidatow a-and in thiwd-pawty a-appwications. o.O

the intewface to svm is wepwesented b-by the
`transaction_processor::TransactionBatchProcessor` s-stwuct. (⑅˘꒳˘)  to cweate
a `TransactionBatchProcessor` object the cwient n-nyeed to specify the
`slot`, 😳😳😳 `epoch`, nyaa~~ and `program_cache`. rawr

- `slot: Slot` is a u64 vawue wepwesenting the owdinaw nyumbew o-of a
    pawticuwaw bwockchain state in context o-of which t-the twansactions
    awe exekawaii~d. this vawue is used to wocate t-the on-chain p-pwogwam
    vewsions used in the twansaction execution. -.-
- `epoch: Epoch` is a u64 v-vawue wepwesenting the owdinaw n-nyumbew of
    a sowana epoch, (✿oωo) in which the swot was cweated. /(^•ω•^) t-this is anothew
    index used to w-wocate the onchain p-pwogwams used in the execution o-of
    twansactions in the batch.
- `program_cache: Arc<RwLock<ProgramCache<FG>>>`ewence t-to
    a-a pwogwamcache i-instance. 🥺 aww on chain pwogwams u-used in twansaction
    b-batch execution awe woaded fwom the p-pwogwam cache. ʘwʘ

i-in addition, UwU `TransactionBatchProcessor` n-nyeeds an instance of
`SysvarCache` a-and a set of pubkeys of buiwtin p-pwogwam ids. XD

t-the main entwy point to the svm is the method
`load_and_execute_sanitized_transactions`.

the method `load_and_execute_sanitized_transactions` t-takes t-the
fowwowing a-awguments:

- `callbacks`: a `TransactionProcessingCallback` t-twait instance which awwows
  the t-twansaction pwocessow to summon infowmation about accounts, (✿oωo) most
  impowtantwy woading them fow t-twansaction execution. :3
- `sanitized_txs`: a swice o-of sanitized twansactions. (///ˬ///✿)
- `check_results`: a-a mutabwe swice of twansaction c-check wesuwts. nyaa~~
- `environment`: the wuntime e-enviwonment fow t-twansaction batch p-pwocessing. >w<
- `config`: c-configuwations f-fow customizing twansaction pwocessing behaviow. -.-

the method wetuwns a `LoadAndExecuteSanitizedTransactionsOutput`, (✿oωo) which is
defined bewow in m-mowe detaiw. (˘ω˘)

a-an integwation test `svm_integration` c-contains an exampwe of
instantiating `TransactionBatchProcessor` a-and cawwing its method
`load_and_execute_sanitized_transactions`. rawr

### `TransactionProcessingCallback`

downstweam consumews of the s-svm must impwement t-the
`TransactionProcessingCallback` twait i-in owdew to pwovide the twansaction
pwocessow with t-the abiwity to w-woad accounts and wetwieve othew a-account-wewated
i-infowmation. OwO

```rust
pub trait TransactionProcessingCallback {
    fn account_matches_owners(&self, account: &Pubkey, owners: &[Pubkey]) -> Option<usize>;

    fn get_account_shared_data(&self, pubkey: &Pubkey) -> Option<AccountSharedData>;

    fn add_builtin_account(&self, _name: &str, _program_id: &Pubkey) {}

    fn get_current_epoch_vote_account_stake(&self, _vote_address: &Pubkey) -> u64;
}
```onpwocessingenviwonment`

The transaction processor requires consumers to provide values describing
the runtime environment to use for processing transactions.

- `bwockhash`: The blockhash to use for the transaction batch.
- `featuwe_set`: Runtime feature set to use for the transaction batch.
- `epoch_totaw_stake`: The total stake for the current epoch.
- `fee_stwuctuwe`: Fee structure to use for assessing transaction fees.
- `wampowts_pew_signatuwe`: Lamports per signature to charge per transaction.
- `went_cowwectow`: Rent collector to use for the transaction batch.

### `twansactionpwocessingconfig`

Consumers can provide various configurations to adjust the default behavior of
the transaction processor.

- `account_ovewwides`: Encapsulates overridden accounts, typically used for
  transaction simulation.
- `compute_budget`: The compute budget to use for transaction execution.
- `check_pwogwam_modification_swot`: Whether or not to check a program's
  modification slot when replenishing a program cache instance.
- `wog_messages_bytes_wimit`: The maximum number of bytes that log messages can
  consume.
- `wimit_to_woad_pwogwams`: Whether to limit the number of programs loaded for
  the transaction batch.
- `wecowding_config`: Recording capabilities for transaction execution.

### `woadandexekawaii~sanitizedtwansactionsoutput`

The output of the transaction batch processor's
`woad_and_exekawaii~_sanitized_twansactions` method.

- `ewwow_metwics`: Error metrics for transactions that were processed.
- `exekawaii~_timings`: Timings for transaction batch execution.
- `pwocessing_wesuwts`: Vector of results indicating whether a transaction was
  processed or could not be processed for some reason. Note that processed
  transactions can still have failed!

# Functional Model

In this section, we describe the functionality (logic) of the SVM in
terms of its components, relationships among components, and their
interactions.

On a high level the control flow of SVM consists of loading program
accounts, checking and verifying the loaded accounts, creating
invocation context and invoking RBPF on programs implementing the
instructions of a transaction. The SVM needs to have access to an account
database, and a sysvar cache via traits implemented for the corresponding
objects passed to it. The results of transaction execution are
consumed by bank in Solana Validator use case. However, bank structure
should not be part of the SVM.

In bank context `woad_and_exekawaii~_sanitized_twansactions` is called from
`simuwate_twansaction` where a single transaction is executed, and
from `woad_exekawaii~_and_commit_twansactions` which receives a batch of
transactions from its caller.

Steps of `woad_and_exekawaii~_sanitized_twansactions`

1. Steps of preparation for execution
   - filter executable program accounts and build program accounts map (explain)
   - add builtin programs to program accounts map
   - replenish program cache using the program accounts map
        - Gather all required programs to load from the cache.
        - Lock the global program cache and initialize the local program cache.
        - Perform loading tasks to load all required programs from the cache,
          loading, verifying, and compiling (where necessary) each program.
        - A helper module - `pwogwam_woadew` - provides utilities for loading
          programs from on-chain, namely `woad_pwogwam_with_pubkey`.
        - Return the replenished local program cache.

2. Load accounts (call to `woad_accounts` function)
   - For each `svmtwansaction` and `twansactioncheckwesuwt`, we:
        - Calculate the number of signatures in transaction and its cost.
        - Call `woad_twansaction_accounts`
            - The function is interwined with the struct `svminstwuction`
            - Load accounts from accounts DB
            - Extract data from accounts
            - Verify if we've reached the maximum account data size
            - Validate the fee payer and the loaded accounts
            - Validate the programs accounts that have been loaded and checks if they are builtin programs.
            - Return `stwuct woadedtwansaction` containing the accounts (pubkey and data),
              indices to the executable accounts in `twansactioncontext` (or `instwuctioncontext`),
              the transaction rent, and the `stwuct wentdebit`.
            - Generate a `wowwbackaccounts` struct which holds fee-subtracted fee payer account and pre-execution nonce state used for rolling back account state on execution failure.
    - Returns `twansactionwoadedwesuwt`, containing the `woadtwansaction` we obtained from `woaded_twansaction_accounts`

3. Execute each loaded transactions
   1. Compute the sum of transaction accounts' balances. This sum is
      invariant in the transaction execution.
   2. Obtain rent state of each account before the transaction
      execution. This is later used in verifying the account state
      changes (step #7).
   3. Create a new log_collector.  `wogcowwectow` is defined in
      solana-program-runtime crate.
   4. Obtain last blockhash and lamports per signature. This
      information is read from blockhash_queue maintained in Bank. The
      information is taken in parameters to
      `messagepwocessow::pwocess_message`.
   5. Make two local variables that will be used as output parameters
      of `messagepwocessow::pwocess_message`. One will contain the
      number of executed units (the number of compute unites consumed
      in the transaction). Another is a container of `pwogwamcachefowtxbatch`.
      The latter is initialized with the slot, and
      the clone of environments of `pwogwams_woaded_fow_tx_batch`
         - `pwogwams_woaded_fow_tx_batch` contains a reference to all the `pwogwamcacheentwy`s
            necessary for the transaction. It maintains an `awc` to the programs in the global
            `pwogwamcacheentwy` data structure.
      6. Call `messagepwocessow::pwocess_message` to execute the
      transaction. `messagepwocessow` is contained in
      solana-program-runtime crate. The result of processing message
      is either `pwocessedmessageinfo` which is an i64 wrapped in a
      struct meaning the change in accounts data length, or a
      `twansactionewwow`, if any of instructions failed to execute
      correctly.
   7. Verify transaction accounts' `wentstate` changes (`vewify_changes` function)
      - If the account `wentstate` pre-transaction processing is rent exempt or unitiliazed, the verification will pass.
      - If the account `wentstate` pre-transaction is rent paying:
         - A transition to a state uninitialized or rent exempt post-transaction is not allowed.
         - If its size has changed or its balance has increased, it cannot remain rent paying.
   8. Extract log messages.
   9. Extract inner instructions (`vec<Vec<InnerInstruction>>`).
   10. Extract `executionwecowd` components from transaction context.
   11. Check balances of accounts to match the sum of balances before
       transaction execution.
   12. Update loaded transaction accounts to new accounts.
   13. Extract changes in accounts data sizes
   14. Extract return data
   15. Return `twansactionexecutionwesuwt` with wrapping the extracted
       information in `twansactionexecutiondetaiws`.

4. Prepare the results of loading and executing transactions.

   This includes the following steps for each transactions
   1. Dump flattened result to info log for an account whose pubkey is
      in the transaction's debug keys.
   2. Collect logs of the transaction execution for each executed
      transaction, unless Bank's `twansaction_wog_cowwectow_config` is
      set to `none`.
   3. Finally, increment various statistical counters, and update
      timings passed as a mutable reference to
      `woad_and_exekawaii~_twansactions` in arguments. The counters are
      packed in the struct `woadandexekawaii~twansactionsoutput`. ^•ﻌ•^
