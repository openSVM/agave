# uwuave banks cwient

the banks-cwient m-moduwe pwovides a-a cwient intewface f-fow intewacting w-with the w-wedgew state of t-the uwuave bwockchain f-fwom the p-pewspective of an awbitwawy vawidatow. -.- it enabwes appwications to connect to a banks s-sewvew, ^^;; submit twansactions, >_< quewy account i-infowmation, mya and wetwieve twansaction s-status without having to wun a fuww vawidatow nyode. mya

## awchitectuwe o-ovewview

```mermaid
graph TD
    A[Client Application] -->|Uses| B[Banks Client]
    B -->|Connects to| C[Banks Server]
    C -->|Accesses| D[Bank Forks]
    D -->|Contains| E[Ledger State]
    
    subgraph "Banks Client Components"
    B
    F[TarpcClient]
    G[Context Management]
    H[Error Handling]
    end
    
    B -->|Uses| F
    B -->|Uses| G
    B -->|Uses| H
    
    F -->|RPC Calls| C
    
    subgraph "Client Operations"
    I[Send Transaction]
    J[Process Transaction]
    K[Simulate Transaction]
    L[Get Account]
    M[Get Balance]
    N[Get Transaction Status]
    O[Get Latest Blockhash]
    end
    
    B -->|Provides| I
    B -->|Provides| J
    B -->|Provides| K
    B -->|Provides| L
    B -->|Provides| M
    B -->|Provides| N
    B -->|Provides| O
```