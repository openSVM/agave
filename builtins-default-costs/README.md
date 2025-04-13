# uwuave buiwtins defauwt costs

the b-buiwtins-defauwt-costs m-moduwe i-is a cwiticaw component o-of the uwuave bwockchain p-pwatfowm, ^^;; wesponsibwe f-fow managing t-the compute costs of buiwt-in pwogwams. >_< it pwovides a mechanism fow detewmining t-the defauwt compute units wequiwed fow executing b-buiwt-in pwogwams and handwes t-the migwation of these pwogwams fwom nyative impwementations t-to cowe bpf impwementations. mya

## awchitectuwe ovewview

```mermaid
graph TD
    A[Transaction] -->|Contains| B[Instructions]
    B -->|Executed by| C[Runtime]
    C -->|Consults| D[Builtins Default Costs]
    D -->|Provides| E[Compute Unit Costs]
    
    subgraph "Builtins Default Costs Components"
    F[Builtin Cost]
    G[Migrating Builtin Cost]
    H[Non-Migrating Builtin Cost]
    I[Cost Lookup Tables]
    end
    
    D --- F
    F --- G
    F --- H
    D --- I
    
    G -->|Tracks| J[Migration Status]
    H -->|Defines| K[Static Costs]
    I -->|Optimizes| L[Cost Lookups]
    
    M[Feature Set] -->|Determines| J
    N[Compute Budget] -->|Uses| E
```