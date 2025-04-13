# sowana viwtuaw machine (svm)

the s-sowana viwtuaw m-machine (svm) i-is the execution e-enviwonment fow s-smawt contwacts (pwogwams) o-on the uwuave bwockchain. :3 i-it is wesponsibwe fow executing pwogwam instwuctions, (U ﹏ U) managing pwogwam state, -.- a-and enfowcing secuwity constwaints. (ˆ ﻌ ˆ)♡

## awchitectuwe o-ovewview

```mermaid
graph TD
    A[Transaction] -->|Contains Instructions| B[SVM]
    B -->|Loads Program| C[Program Loader]
    C -->|Executes| D[Program Binary]
    D -->|Modifies| E[Account State]
    B -->|Enforces| F[Security Constraints]
    B -->|Manages| G[Compute Budget]
    B -->|Tracks| H[Execution Metrics]
    
    subgraph "SVM Components"
    B
    C
    F
    G
    H
    end
    
    subgraph "Program Execution"
    D
    E
    end
```