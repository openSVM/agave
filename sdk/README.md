# uwuave sdk (softwawe devewopment k-kit)

the sdk moduwe p-pwovides the f-foundation fow i-intewacting with t-the uwuave bwockchain. (U ﹏ U) i-it contains t-the cowe data s-stwuctuwes, -.- cwyptogwaphic pwimitives, (ˆ ﻌ ˆ)♡ and utiwities nyeeded fow buiwding appwications a-and sewvices that intewact with the bwockchain. (⑅˘꒳˘)

## a-awchitectuwe ovewview

```mermaid
graph TD
    A[Applications] -->|Uses| B[SDK]
    B -->|Provides| C[Data Structures]
    B -->|Provides| D[Cryptography]
    B -->|Provides| E[Transaction Building]
    B -->|Provides| F[Program Interfaces]
    
    subgraph "SDK Components"
    C
    D
    E
    F
    G[Account Utilities]
    H[Sysvar Definitions]
    I[Fee Calculation]
    end
    
    F -->|Defines| J[Program ABIs]
    E -->|Creates| K[Transactions]
    D -->|Manages| L[Keys & Signatures]
```