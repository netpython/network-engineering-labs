# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure SWA

[Configuration delta](apply/SWA.cfg)

```text
vlan 10
 name VLAN10
vlan 20
 name VLAN20
interface GigabitEthernet0/0
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20
 no shutdown
interface GigabitEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20
 no shutdown
interface GigabitEthernet0/2
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 no shutdown
interface GigabitEthernet0/3
 switchport mode access
 switchport access vlan 20
 spanning-tree portfast
 no shutdown
```

## Configure D1

[Configuration delta](apply/D1.cfg)

```text
track 1 interface GigabitEthernet0/1 line-protocol
interface GigabitEthernet0/0
 no shutdown
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 10.1.10.2 255.255.255.0
 standby version 2
 standby 10 ip 10.1.10.1
 standby 10 priority 110
 standby 10 preempt
 standby 10 track 1 decrement 40
interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 10.1.20.2 255.255.255.0
 standby version 2
 standby 20 ip 10.1.20.1
 standby 20 priority 110
 standby 20 preempt
 standby 20 track 1 decrement 40
router ospf 10
 router-id 2.2.2.2
 passive-interface default
 no passive-interface GigabitEthernet0/1
 network 10.0.1.0 0.0.0.3 area 0
 network 10.1.10.0 0.0.0.255 area 0
 network 10.1.20.0 0.0.0.255 area 0
```

## Configure D2

[Configuration delta](apply/D2.cfg)

```text
track 1 interface GigabitEthernet0/1 line-protocol
interface GigabitEthernet0/0
 no shutdown
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 10.1.10.3 255.255.255.0
 standby version 2
 standby 10 ip 10.1.10.1
 standby 10 priority 100
 standby 10 preempt
 standby 10 track 1 decrement 40
interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 10.1.20.3 255.255.255.0
 standby version 2
 standby 20 ip 10.1.20.1
 standby 20 priority 100
 standby 20 preempt
 standby 20 track 1 decrement 40
router ospf 10
 router-id 3.3.3.3
 passive-interface default
 no passive-interface GigabitEthernet0/1
 network 10.0.2.0 0.0.0.3 area 0
 network 10.1.10.0 0.0.0.255 area 0
 network 10.1.20.0 0.0.0.255 area 0
```

## Configure EDGE

[Configuration delta](apply/EDGE.cfg)

```text
router ospf 10
 router-id 1.1.1.1
 network 10.0.1.0 0.0.0.3 area 0
 network 10.0.2.0 0.0.0.3 area 0
 network 10.0.3.0 0.0.0.3 area 0
 default-information originate
ip route 0.0.0.0 0.0.0.0 198.51.100.1
interface GigabitEthernet0/0
 ip nat inside
interface GigabitEthernet0/1
 ip nat inside
interface GigabitEthernet0/2
 ip nat inside
interface GigabitEthernet0/3
 ip nat outside
ip access-list standard SITE-NAT
 permit 10.1.10.0 0.0.0.255
 permit 10.1.20.0 0.0.0.255
 permit 10.2.30.0 0.0.0.255
ip nat inside source list SITE-NAT interface GigabitEthernet0/3 overload
```

## Configure BRANCH

[Configuration delta](apply/BRANCH.cfg)

```text
router ospf 10
 router-id 4.4.4.4
 passive-interface GigabitEthernet0/1
 network 10.0.3.0 0.0.0.3 area 0
 network 10.2.30.0 0.0.0.255 area 0
```

## Why this works

VLAN trunks connect the campus hosts to both distribution routers. HSRP tracking chooses a usable campus gateway while OSPF carries internal subnets and the edge default across both sites. PAT is applied only when user traffic crosses EDGE from an inside interface to the simulated Internet interface.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
