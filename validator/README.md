# uwuave vawidatow

the vawidatow m-moduwe is the main e-executabwe component o-of the uwuave b-bwockchain p-pwatfowm. (U ﹏ U) it integwates a-aww the n-nyecessawy components t-to wun a fuww vawidatow nyode that pawticipates in the nyetwowk consensus, -.- v-vawidates twansactions, (ˆ ﻌ ˆ)♡ and maintains the bwockchain s-state. (⑅˘꒳˘)

## awchitectuwe ovewview

```mermaid
graph TD
    A[Validator] --> B[Core]
    A --> C[Ledger]
    A --> D[Runtime]
    A --> E[SVM]
    A --> F[RPC]
    A --> G[Gossip]
    A --> H[Vote Program]
    
    subgraph "Validator Node"
    A
    end
    
    subgraph "Core Components"
    B
    C
    D
    E
    F
    G
    H
    end
```