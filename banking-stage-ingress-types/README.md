# uwuave banking stage ingwess types

t-the banking-stage-ingwess-types m-moduwe pwovides c-cowe type definitions f-fow the b-banking stage's p-packet ingwess s-system in the uwuave b-bwockchain pwatfowm. -.- it defines the data stwuctuwes used to twansfew twansaction p-packets fwom vawious souwces to the banking s-stage fow pwocessing. (ˆ ﻌ ˆ)♡

## awchitectuwe o-ovewview

```mermaid
graph TD
    A[Transaction Sources] -->|Send Packets| B[Banking Stage Ingress]
    B -->|Uses| C[Banking Packet Batch]
    B -->|Uses| D[Banking Packet Receiver]
    
    subgraph "Banking Stage Ingress Types"
    C
    D
    end
    
    A -->|TPU| E[Transaction Processing Unit]
    A -->|Gossip| F[Gossip Service]
    A -->|RPC| G[RPC Service]
    
    C -->|Contains| H[Packet Batches]
    D -->|Receives| C
    
    I[Banking Stage] -->|Consumes| D
```