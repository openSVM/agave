# uwuave pwogwams

the pwogwams diwectowy c-contains t-the buiwt-in smawt c-contwacts (pwogwams) t-that pwovide c-cowe functionawity f-fow the uwuave bwockchain. >_< t-these pwogwams awe essentiaw fow the opewation of the bwockchain and awe depwoyed a-as pawt of the genesis configuwation. :3

## awchitectuwe ovewview

```mermaid
graph TD
    A[Client] -->|Invokes| B[Programs]
    B -->|Executes on| C[SVM]
    
    subgraph "Built-in Programs"
    D[System Program]
    E[Stake Program]
    F[Vote Program]
    G[BPF Loader]
    H[Config Program]
    I[Address Lookup Table]
    J[Compute Budget]
    K[ZK Token Proof]
    end
    
    B --- D
    B --- E
    B --- F
    B --- G
    B --- H
    B --- I
    B --- J
    B --- K
```