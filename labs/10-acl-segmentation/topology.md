# Topology and addressing

| Node | Suggested image |
| --- | --- |
| R1 | IOSv router or compatible IOS XE |
| PC1 | VPCS |
| PC2 | VPCS |

## Exact cabling

| Node A | Port A | Node B | Port B | Segment |
| --- | --- | --- | --- | --- |
| PC1 | eth0 | R1 | GigabitEthernet0/0 | user subnet |
| PC2 | eth0 | R1 | GigabitEthernet0/1 | server subnet |

## Address plan

| Node | Interface | Address | Purpose / gateway |
| --- | --- | --- | --- |
| PC1 | eth0 | 10.10.10.10/24 | 10.10.10.1 |
| PC2 | eth0 | 10.10.20.20/24 | 10.10.20.1 |
| R1 | GigabitEthernet0/0 | 10.10.10.1/24 | physical / logical address |
| R1 | GigabitEthernet0/1 | 10.10.20.1/24 | physical / logical address |

Map interface names to the selected image before loading configurations. The cabling table is authoritative.
