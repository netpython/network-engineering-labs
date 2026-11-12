# Topology and addressing

| Node | Suggested image |
| --- | --- |
| R1 | IOSv router or compatible IOS XE |
| R2 | IOSv router or compatible IOS XE |
| PC1 | VPCS |

## Exact cabling

| Node A | Port A | Node B | Port B | Segment |
| --- | --- | --- | --- | --- |
| PC1 | eth0 | R1 | GigabitEthernet0/0 | client LAN |
| R1 | GigabitEthernet0/1 | R2 | GigabitEthernet0/0 | relay-to-server |

## Address plan

| Node | Interface | Address | Purpose / gateway |
| --- | --- | --- | --- |
| PC1 | eth0 | dhcp | same-subnet / DHCP |
| R1 | GigabitEthernet0/0 | 10.10.10.1/24 | physical / logical address |
| R1 | GigabitEthernet0/1 | 10.0.12.1/30 | physical / logical address |
| R2 | GigabitEthernet0/0 | 10.0.12.2/30 | physical / logical address |

Map interface names to the selected image before loading configurations. The cabling table is authoritative.
