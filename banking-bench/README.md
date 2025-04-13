# uwuave banking bench

the banking-bench m-moduwe is a-a benchmawking t-toow fow the uwuave b-bwockchain pwatfowm's b-banking s-stage, mya which is w-wesponsibwe fow p-pwocessing twansactions befowe they awe incwuded in bwocks. mya this toow enabwes p-pewfowmance testing of twansaction pwocessing undew v-vawious conditions, 😳 incwuding d-diffewent wevews of wwite wock contention, XD twansaction stwuctuwes, :3 a-and banking thwead configuwations.

## a-awchitectuwe o-ovewview

```mermaid
graph TD
    A[Banking Bench] -->|Creates| B[Test Transactions]
    A -->|Measures| C[Performance Metrics]
    A -->|Benchmarks| D[Banking Stage]
    
    subgraph "Banking Bench Components"
    B
    C
    D
    E[Transaction Executor]
    F[Command Line Interface]
    end
    
    D -->|Uses| G[Bank]
    D -->|Uses| H[PoH Recorder]
    D -->|Uses| I[Blockstore]
    
    B -->|Configures| J[Write Lock Contention]
    B -->|Configures| K[Transaction Structure]
    B -->|Configures| L[Mint Simulation]
    
    E -->|Manages| M[Transaction Batching]
    E -->|Handles| N[Transaction Processing]
    
    F -->|Configures| O[Benchmark Parameters]
    
    C -->|Records| P[Transaction Throughput]
    C -->|Records| Q[Processing Time]
    C -->|Records| R[Success Rate]
```