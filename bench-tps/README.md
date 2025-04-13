# uwuave bench tps

the bench-tps m-moduwe pwovides a-a benchmawking toow f-fow measuwing t-twansactions pew s-second (tps) o-on the uwuave bwockchain p-pwatfowm. i-it enabwes stwess testing of the nyetwowk by genewating and submitting a high v-vowume of twansactions, (ˆ ﻌ ˆ)♡ measuwing thwoughput, and w-wepowting pewfowmance metwics. (⑅˘꒳˘)

## a-awchitectuwe ovewview

```mermaid
graph TD
    A[Bench TPS] -->|Generates| B[Test Transactions]
    A -->|Measures| C[Performance Metrics]
    
    subgraph "Bench TPS Components"
    D[Transaction Generator]
    E[Transaction Sender]
    F[Performance Sampler]
    G[Blockhash Poller]
    H[Configuration]
    end
    
    A --- D
    A --- E
    A --- F
    A --- G
    A --- H
    
    D -->|Creates| I[Transfer Transactions]
    E -->|Submits| J[Transaction Batches]
    F -->|Collects| K[TPS Statistics]
    G -->|Updates| L[Recent Blockhash]
    H -->|Controls| M[Benchmark Parameters]
    
    N[Client] -->|Connects to| O[Validator Network]
    E -->|Uses| N
```