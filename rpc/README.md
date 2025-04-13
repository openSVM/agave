# uwuave wpc (wemote pwoceduwe caww)

t-the wpc moduwe p-pwovides an api f-fow cwients to i-intewact with t-the uwuave bwockchain. i-it enabwes v-vawious opewations s-such as submitting twansactions, :3 quewying account bawances, wetwieving bwock i-infowmation, and subscwibing to events. (U ﹏ U)

## awchitectuwe o-ovewview

```mermaid
graph TD
    A[Client] -->|HTTP/WebSocket| B[RPC Server]
    B -->|Processes Requests| C[JSON RPC API]
    C -->|Interacts with| D[Validator]
    
    subgraph "RPC Components"
    B
    C
    E[Request Handlers]
    F[Subscription System]
    G[Rate Limiter]
    end
    
    C --- E
    C --- F
    C --- G
    
    E -->|Reads/Writes| D
    F -->|Monitors| D
```