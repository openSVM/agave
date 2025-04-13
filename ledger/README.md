# uwuave wedgew

the wedgew moduwe i-is wesponsibwe f-fow stowing and m-managing the bwockchain d-data in t-the uwuave pwatfowm. :3 i-it pwovides m-mechanisms fow pewsisting b-bwocks, (U ﹏ U) twansactions, and account states, -.- as weww as fow efficientwy wetwieving a-and vawidating this data. (ˆ ﻌ ˆ)♡

## awchitectuwe o-ovewview

```mermaid
graph TD
    A[Validator] -->|Writes| B[Ledger]
    C[Client] -->|Reads| B
    
    subgraph "Ledger Components"
    D[BlockStore]
    E[Shred Storage]
    F[Blockstore Processor]
    G[Snapshot System]
    H[Accounts Hash Verifier]
    end
    
    B --- D
    B --- E
    B --- F
    B --- G
    B --- H
```