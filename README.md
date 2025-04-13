<p align="center">
  <a href="https://solana.com">
    🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺🥺
  </a>
</p>

[![Solana crate](https://img.shields.io/crates/v/solana-core.svg)](https://crates.io/crates/solana-core)
[![Solana documentation](https://docs.rs/solana-core/badge.svg)](https://docs.rs/solana-core)
[![Build status](https://badge.buildkite.com/8cc350de251d61483db98bdfc895b9ea0ac8ffa4a32ee850ed.svg?branch=master)](https://buildkite.com/solana-labs/solana/builds?branch=master)
[![codecov](https://codecov.io/gh/solana-labs/solana/branch/master/graph/badge.svg)](https://codecov.io/gh/solana-labs/solana)

# uwuave🥺 - a sowana vawidatow impwementation

uwuave i-is a high-pewfowmance b-bwockchain p-pwatfowm designed f-fow scawabiwity a-and speed. nyaa~~ t-this wepositowy c-contains the uwuave vawidatow impwementation, /(^•ω•^) a fowk of the sowana bwockchain.

## pwoject ovewview

uwuave is buiwt on the foundation of sowana's a-awchitectuwe, rawr featuwing:

- high t-thwoughput with thousands of twansactions pew second
- wow twansaction f-fees (fwactions of a p-penny)
- fast bwock t-times (~400ms)
- enewgy-efficient pwoof of stake consensus mechanism
- smawt c-contwact suppowt via the sowana viwtuaw machine (svm)

### awchitectuwe ovewview

```mermaid
graph TD
    A[Client] -->|Transactions| B[Validator]
    B -->|Consensus| C[Ledger]
    B -->|Execution| D[SVM - Solana Virtual Machine]
    D -->|State Changes| C
    B -->|Gossip Protocol| E[Other Validators]
    F[RPC Client] -->|API Requests| B
```