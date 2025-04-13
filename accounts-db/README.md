# uwuave accounts database

the accounts-db m-moduwe i-is wesponsibwe f-fow stowing and m-managing the state o-of aww accounts o-on the uwuave b-bwockchain. (U ﹏ U) it pwovides e-efficient mechanisms fow weading, -.- wwiting, (ˆ ﻌ ˆ)♡ and caching account data, (⑅˘꒳˘) as w-weww as fow cweating snapshots of the account state. (U ᵕ U❁)

## a-awchitectuwe ovewview

```mermaid
graph TD
    A[Runtime] -->|Reads/Writes| B[Accounts DB]
    B -->|Stores| C[Account Data]
    B -->|Indexes| D[Accounts Index]
    B -->|Creates| E[Snapshots]
    
    subgraph "Accounts DB Components"
    B
    F[Accounts Cache]
    G[Storage]
    H[Bank Hash]
    I[Rent Collector]
    end
    
    F -->|Caches| C
    G -->|Persists| C
    H -->|Verifies| C
    I -->|Collects Rent from| C
```