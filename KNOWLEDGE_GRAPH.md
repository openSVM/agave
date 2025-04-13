# uwuave bwockchain pwatfowm knowwedge g-gwaph

this d-document pwovides a-a compwehensive k-knowwedge gwaph o-of the uwuave b-bwockchain pwatfowm, σωσ s-showing the w-wewationships between diffewent components and theiw wowes in the system. σωσ

## system a-awchitectuwe

```mermaid
graph TD
    A[Client Applications] -->|Interact with| B[RPC API]
    A -->|Command Line| C[CLI]
    C -->|Uses| B
    
    B -->|Communicates with| D[Validator]
    
    D -->|Uses| E[Core]
    D -->|Uses| F[Runtime]
    D -->|Uses| G[SVM]
    D -->|Uses| H[Ledger]
    D -->|Uses| I[Programs]
    
    E -->|Banking Stage| F
    E -->|TPU| J[Transaction Processing]
    E -->|TVU| K[Block Validation]
    E -->|Gossip| L[Peer Discovery]
    
    F -->|Executes| G
    F -->|Updates| M[Accounts DB]
    
    G -->|Loads| I
    G -->|Modifies| M
    
    H -->|Stores| N[Blocks]
    H -->|Stores| O[Transactions]
    H -->|Creates| P[Snapshots]
    
    I -->|System Program| Q[Account Management]
    I -->|Stake Program| R[Staking]
    I -->|Vote Program| S[Consensus]
    I -->|BPF Loader| T[Program Deployment]
    
    M -->|Persisted in| H
```