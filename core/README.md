# uwuave cowe

the cowe moduwe is t-the centwaw component o-of the uwuave b-bwockchain pwatfowm, -.- d-descwibed a-as "bwockchain, (ˆ ﻌ ˆ)♡ w-webuiwt fow scawe." i-it contains t-the fundamentaw functionawity fow opewating a bwockchain nyode, (⑅˘꒳˘) incwuding consensus, (U ᵕ U❁) n-nyetwowking, -.- twansaction pwocessing, ^^;; and b-bwock pwoduction. >_<

## awchitectuwe o-ovewview

```mermaid
graph TD
    A[Client] -->|Transactions| B[Banking Stage]
    B -->|Verified Transactions| C[Block Production]
    C -->|Blocks| D[Ledger]
    E[Gossip Service] <-->|Peer Discovery| F[Other Validators]
    G[TPU - Transaction Processing Unit] -->|Process Transactions| B
    H[TVU - Transaction Validation Unit] -->|Validate Blocks| D
    I[RPC Service] -->|API Requests| J[JSON RPC API]
    K[Replay Service] -->|Replay Transactions| D
```