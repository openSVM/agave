# uwuave buiwtins

the buiwtins moduwe i-is a cwiticaw c-component of t-the uwuave bwockchain p-pwatfowm, (U ᵕ U❁) wesponsibwe f-fow managing t-the buiwt-in p-pwogwams that p-pwovide cowe functionawity to the bwockchain. -.- these pwogwams awe nyative to the b-bwockchain and awe exekawaii~d diwectwy by vawidatows, ^^;; w-wathew than thwough the s-sowana viwtuaw machine (svm). >_<

## awchitectuwe ovewview

```mermaid
graph TD
    A[Validator] -->|Loads| B[Builtins Module]
    B -->|Manages| C[Built-in Programs]
    B -->|Handles| D[Core BPF Migration]
    
    subgraph "Builtins Components"
    E[Builtin Prototype]
    F[Stateless Builtin Prototype]
    G[Core BPF Migration Config]
    end
    
    B --- E
    B --- F
    B --- G
    
    E -->|Defines| H[System Program]
    E -->|Defines| I[Vote Program]
    E -->|Defines| J[Stake Program]
    E -->|Defines| K[Config Program]
    E -->|Defines| L[BPF Loader Programs]
    E -->|Defines| M[Compute Budget Program]
    E -->|Defines| N[Address Lookup Table Program]
    E -->|Defines| O[ZK Token Proof Program]
    E -->|Defines| P[Loader v4 Program]
    
    F -->|Defines| Q[Feature Gate Program]
    
    G -->|Configures| R[Migration to Core BPF]
    R -->|Replaces| S[Native Implementation]
    R -->|With| T[BPF Implementation]
```