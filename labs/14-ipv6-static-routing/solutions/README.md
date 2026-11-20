# Solution

Enable IPv6 forwarding, retain the addressed transit link, and install one fully specified /128 static route on each node. The next hop belongs to the directly connected transit subnet.

Apply [R1 delta](deltas/R1.cfg) and [R2 delta](deltas/R2.cfg) to the starter state. Complete reference configurations: [R1](final-configs/R1.cfg), [R2](final-configs/R2.cfg).

With the source set to R1's loopback, an echo request uses R1's route to 2001:db8:2::2/128. R2 needs its own route to 2001:db8:1::1/128 for the reply. A transit-address ping does not exercise that return route.

For task 7, on R2:

```text
configure terminal
no ipv6 route 2001:db8:1::1/128 GigabitEthernet0/0 2001:db8:12::1
end
```

Repeat the sourced test from R1, then restore the route using the R2 delta. To return fully to the starter state, remove the corresponding added route on R1 as well. Do not save the intentionally broken state.

Sources: [Cisco static IPv6 routing](https://www.cisco.com/c/en/us/td/docs/routers/ios/config/17-x/ip-routing/b-ip-routing/m_ip6-route-static-xe.html), [IPv6 ping command reference](https://www.cisco.com/c/en/us/td/docs/ios/ipv6/command/reference/ipv6_book/ipv6_10.html). Expected behavior is explanatory; no device transcript is fabricated.

[Verification](../verification.md) · [Exercise](../README.md)
