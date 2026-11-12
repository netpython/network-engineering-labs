# Topology and addressing

| Node | Suggested image |
| --- | --- |
| R1 | IOSv router or compatible IOS XE |
| BLUE-PC | VPCS |
| RED-PC | VPCS |

## Exact cabling

| Node A | Port A | Node B | Port B | Segment |
| --- | --- | --- | --- | --- |
| BLUE-PC | eth0 | R1 | GigabitEthernet0/0 | BLUE tenant |
| RED-PC | eth0 | R1 | GigabitEthernet0/1 | RED tenant |

## Address plan

| Node | Interface | Address | Purpose / gateway |
| --- | --- | --- | --- |
| BLUE-PC | eth0 | 10.10.10.10/24 | 10.10.10.1 |
| R1 | GigabitEthernet0/0 | 10.10.10.1/24 | physical / logical address |
| R1 | GigabitEthernet0/1 | 10.10.10.1/24 | physical / logical address |
| RED-PC | eth0 | 10.10.10.10/24 | 10.10.10.1 |

Map interface names to the selected image before loading configurations. The cabling table is authoritative.
