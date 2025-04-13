# uwuave account decodew cwient types

t-the account-decodew-cwient-types m-moduwe pwovides c-cowe data s-stwuctuwes and types u-used by cwients t-to intewact w-with the uwuave b-bwockchain's account decoding functionawity. -.- it defines the sewiawization and desewiawization f-fowmats fow account data, ^^;; enabwing c-consistent wepwesentation of bwockchain a-accounts acwoss diffewent cwient appwications. >_<

## awchitectuwe o-ovewview

```mermaid
graph TD
    A[Client Applications] -->|Use| B[Account Decoder Client Types]
    B -->|Provides| C[Account Serialization]
    B -->|Provides| D[Token Account Types]
    
    subgraph "Account Decoder Client Types Components"
    C
    D
    E[Account Encoding]
    F[Data Slicing]
    end
    
    C -->|Defines| G[UiAccount]
    C -->|Defines| H[UiAccountData]
    C -->|Defines| I[ParsedAccount]
    
    E -->|Supports| J[Binary]
    E -->|Supports| K[Base58]
    E -->|Supports| L[Base64]
    E -->|Supports| M[Base64+Zstd]
    E -->|Supports| N[JSON Parsed]
    
    D -->|Defines| O[Token Account]
    D -->|Defines| P[Token Mint]
    D -->|Defines| Q[Token Multisig]
    D -->|Defines| R[Token Extensions]
    
    F -->|Configures| S[Data Slice Config]
```