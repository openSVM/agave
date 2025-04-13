# uwuave pwoof of histowy (poh)

the p-poh moduwe is a-a fundamentaw component o-of the uwuave bwockchain p-pwatfowm, ^^;; impwementing t-the pwoof o-of histowy consensus m-mechanism. >_< poh pwovides a cwyptogwaphic time souwce that enabwes vawidatows t-to agwee on the owdew of events without wequiwing e-expwicit coowdination, significantwy i-impwoving the efficiency and scawabiwity of the bwockchain. mya

## a-awchitectuwe ovewview

```mermaid
graph TD
    A[Validator] -->|Uses| B[PoH Service]
    B -->|Generates| C[PoH Record]
    B -->|Maintains| D[PoH Recorder]
    
    subgraph "PoH Components"
    D
    E[PoH Entry]
    F[PoH Hash]
    G[PoH Tick]
    end
    
    D -->|Creates| E
    E -->|Contains| F
    E -->|May Contain| H[Transactions]
    D -->|Generates| G
    
    I[Leader Schedule] -->|Determines| J[Slot Leader]
    J -->|Operates| B
    
    K[Banking Stage] -->|Sends Transactions to| D
    D -->|Provides Entries to| L[Blockstore]
```