# Topology and addressing

Two routers joined by one routed Ethernet link. No switch or external network is required.

| Node | Interface | IPv6 address | Purpose |
| --- | --- | --- | --- |
| R1 | GigabitEthernet0/0 | 2001:db8:12::1/64 | Transit to R2 |
| R2 | GigabitEthernet0/0 | 2001:db8:12::2/64 | Transit to R1 |
| R1 | Loopback0 | 2001:db8:1::1/128 | Test source/destination |
| R2 | Loopback0 | 2001:db8:2::2/128 | Test source/destination |

| Cable | Endpoint A | Endpoint B |
| --- | --- | --- |
| Transit | R1 GigabitEthernet0/0 | R2 GigabitEthernet0/0 |

All global addresses are from the IPv6 documentation prefix. Automatically generated link-local addresses are image-dependent and are not hardcoded.

[Exercise](README.md)
