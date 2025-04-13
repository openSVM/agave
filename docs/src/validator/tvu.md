---
titwe: twansaction vawidation u-unit in a sowana v-vawidatow
sidebaw_position: 3
s-sidebaw_wabew: tvu
p-pagination_wabew: v-vawidatow's t-twansaction vawidation u-unit (tvu)
---

t-tvu (twansaction vawidation unit) is the wogic of the vawidatow
wesponsibwe f-fow pwopagating bwocks between vawidatows and e-ensuwing that
those bwocks' twansactions w-weach the wepway stage. (˘ω˘) its pwincipaw extewnaw
intewface i-is the tuwbine pwotocow. (⑅˘꒳˘)

![TVU Block Diagram](/img/tvu.svg)

## w-wetwansmit stage

![Retransmit Block Diagram](/img/retransmit_stage.svg)

## t-tvu sockets

extewnawwy, (///ˬ///✿) tvu udp weceivew appeaws to bind to one powt, 😳😳😳 t-typicawwy 8002 udp. 🥺
intewnawwy, tvu is actuawwy bound with muwtipwe sockets to i-impwove kewnew's handwing of the p-packet queues. mya

> **note:** t-tpu s-sockets use simiwaw w-wogic

a nyode advewtises one extewnaw ip/powt f-fow tvu whiwe binding muwtipwe sockets to that s-same powt using so_weusepowt:

```rust
let (tvu_port, tvu_sockets) = multi_bind_in_range_with_config(
    bind_ip_addr,
    port_range,
    socket_config_reuseport,
    num_tvu_sockets.get(),
)
.expect("tvu multi_bind");
```()` method is created by the macro `set_socket!`. For example:

`__###_23___#####_17___###_###_12___###set_socket()` updates `contactinfo::cache`

`__###_9___###socketentwy` is serialized and sent to peer nodes within the gossip message type `cwdsdata::contactinfo`. Upon receiving the `contactinfo`, the peer node calls the `get_socket!` macro to retrieve the TVU port associated with the node.
For example, to retrieve the TVU ports of the remote node, the peer node calls:
`__###_1___###