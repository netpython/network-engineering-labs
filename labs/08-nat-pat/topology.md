# Topology and addressing

| Node | Suggested image |
| --- | --- |
| R1 | IOSv router or compatible IOS XE |
| ISP | IOSv router or compatible IOS XE |
| PC1 | VPCS |

## Exact cabling

| Node A | Port A | Node B | Port B | Segment |
| --- | --- | --- | --- | --- |
| PC1 | eth0 | R1 | GigabitEthernet0/0 | inside LAN |
| R1 | GigabitEthernet0/1 | ISP | GigabitEthernet0/0 | outside link |

## Address plan

| Node | Interface | Address | Purpose / gateway |
| --- | --- | --- | --- |
| ISP | GigabitEthernet0/0 | 198.51.100.1/30 | physical / logical address |
| ISP | Loopback0 | 203.0.113.10/32 | physical / logical address |
| PC1 | eth0 | 10.10.10.10/24 | 10.10.10.1 |
| R1 | GigabitEthernet0/0 | 10.10.10.1/24 | physical / logical address |
| R1 | GigabitEthernet0/1 | 198.51.100.2/30 | physical / logical address |

Map interface names to the selected image before loading configurations. The cabling table is authoritative.
