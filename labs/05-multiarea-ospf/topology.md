# Topology and addressing

| Node | Suggested image |
| --- | --- |
| R1 | IOSv router or compatible IOS XE |
| R2 | IOSv router or compatible IOS XE |
| R3 | IOSv router or compatible IOS XE |

## Exact cabling

| Node A | Port A | Node B | Port B | Segment |
| --- | --- | --- | --- | --- |
| R1 | GigabitEthernet0/0 | R2 | GigabitEthernet0/0 | area 0 |
| R2 | GigabitEthernet0/1 | R3 | GigabitEthernet0/0 | area 10 |

## Address plan

| Node | Interface | Address | Purpose / gateway |
| --- | --- | --- | --- |
| R1 | GigabitEthernet0/0 | 10.0.12.1/30 | physical / logical address |
| R1 | Loopback0 | 192.0.2.1/32 | physical / logical address |
| R2 | GigabitEthernet0/0 | 10.0.12.2/30 | physical / logical address |
| R2 | GigabitEthernet0/1 | 10.0.23.1/30 | physical / logical address |
| R3 | GigabitEthernet0/0 | 10.0.23.2/30 | physical / logical address |
| R3 | Loopback0 | 198.51.100.1/32 | physical / logical address |

Map interface names to the selected image before loading configurations. The cabling table is authoritative.
