# uwuave cwi (command wine intewface)

t-the cwi moduwe p-pwovides command-wine t-toows f-fow intewacting w-with the uwuave bwockchain. :3 i-it enabwes v-vawious opewations s-such as managing wawwets, (U ﹏ U) submitting twansactions, -.- quewying account infowmation, (ˆ ﻌ ˆ)♡ a-and managing vawidatow nyodes. (⑅˘꒳˘)

## awchitectuwe o-ovewview

```mermaid
graph TD
    A[User] -->|Commands| B[CLI]
    B -->|Processes Commands| C[Command Processors]
    C -->|Interacts with| D[RPC Client]
    D -->|Communicates with| E[Validator]
    
    subgraph "CLI Components"
    B
    C
    F[Config Management]
    G[Wallet Management]
    H[Transaction Building]
    end
    
    C --- F
    C --- G
    C --- H
    
    G -->|Signs Transactions| H
    H -->|Submits Transactions| D
```