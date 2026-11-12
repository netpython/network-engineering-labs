# Topology and addressing

| Node | Suggested image |
| --- | --- |
| R1 | IOSv router or compatible IOS XE |
| R2 | IOSv router or compatible IOS XE |

## Exact cabling

| Node A | Port A | Node B | Port B | Segment |
| --- | --- | --- | --- | --- |
| R1 | GigabitEthernet0/0 | R2 | GigabitEthernet0/0 | eBGP AS65001-AS65002 |

## Address plan

| Node | Interface | Address | Purpose / gateway |
| --- | --- | --- | --- |
| R1 | GigabitEthernet0/0 | 10.0.12.1/30 | physical / logical address |
| R1 | Loopback0 | 192.0.2.1/24 | physical / logical address |
| R1 | Loopback1 | 10.99.1.1/24 | physical / logical address |
| R2 | GigabitEthernet0/0 | 10.0.12.2/30 | physical / logical address |
| R2 | Loopback0 | 198.51.100.1/24 | physical / logical address |

Map interface names to the selected image before loading configurations. The cabling table is authoritative.
