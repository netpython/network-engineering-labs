# Topology and addressing

| Node | Suggested image |
| --- | --- |
| SW1 | IOSvL2 switch |
| SW2 | IOSvL2 switch |
| R1 | IOSv router or compatible IOS XE |
| PC1 | VPCS |
| PC2 | VPCS |

## Logical connections

```mermaid
flowchart TD
  N0["SW1"]
  N1["SW2"]
  N2["R1"]
  N3["PC1"]
  N4["PC2"]
  N0 ---|"LACP members"| N1
  N0 ---|"802.1Q"| N2
  N3 ---|"VLAN 10"| N0
  N4 ---|"VLAN 20"| N1
```

## Exact cabling

| Node A | Port A | Node B | Port B | Segment |
| --- | --- | --- | --- | --- |
| SW1 | GigabitEthernet0/0 | SW2 | GigabitEthernet0/0 | LACP 1 |
| SW1 | GigabitEthernet0/1 | SW2 | GigabitEthernet0/1 | LACP 2 |
| SW1 | GigabitEthernet0/2 | R1 | GigabitEthernet0/0 | 802.1Q |
| PC1 | eth0 | SW1 | GigabitEthernet0/3 | VLAN 10 |
| PC2 | eth0 | SW2 | GigabitEthernet0/2 | VLAN 20 |

## Address plan

| Node | Interface | Address | Purpose / gateway |
| --- | --- | --- | --- |
| PC1 | eth0 | 10.10.10.11/24 | 10.10.10.1 |
| PC2 | eth0 | 10.10.20.12/24 | 10.10.20.1 |
| R1 | GigabitEthernet0/0.10 | 10.10.10.1/24 | physical / logical address |
| R1 | GigabitEthernet0/0.20 | 10.10.20.1/24 | physical / logical address |

Map interface names to the selected image before loading configurations. The cabling table is authoritative.
