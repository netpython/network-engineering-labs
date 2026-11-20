# Acceptance checks

Run show commands in privileged EXEC; pings generate traffic in the isolated lab.

| Node | Command | Expected criterion |
| --- | --- | --- |
| Both | `show ipv6 interface brief` | Transit up/up, correct global addresses and loopbacks |
| R1 | `ping ipv6 2001:db8:12::2 repeat 5` | Direct neighbor reachable after initial ND resolution |
| R2 | `ping ipv6 2001:db8:12::1 repeat 5` | Direct neighbor reachable |
| Both | `show ipv6 neighbors` | Transit neighbor resolved; remote loopbacks need not appear as neighbors |
| Both | `show ipv6 route static` | Remote /128 installed through the intended transit next hop |
| R1 | `ping ipv6 2001:db8:2::2 source Loopback0 repeat 5` | Five replies after convergence |
| R2 | `ping ipv6 2001:db8:1::1 source Loopback0 repeat 5` | Five replies after convergence |

After removing R2's return route, R1's sourced loopback ping must fail although transit reachability remains. After restoration, repeat both sourced tests. Investigate rather than accepting an unexplained partial success.

These are expected criteria, not captured results. Syntax may require interface-name adaptation to the image.

[Exercise](README.md)
