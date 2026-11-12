# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure SW1

[Configuration delta](apply/SW1.cfg)

```text
vlan 10
 name VLAN10
interface GigabitEthernet0/0
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 no shutdown
interface GigabitEthernet0/1
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 no shutdown
interface GigabitEthernet0/2
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 no shutdown
```

## Configure R1

[Configuration delta](apply/R1.cfg)

```text
track 1 interface GigabitEthernet0/1 line-protocol
interface GigabitEthernet0/0
 standby version 2
 standby 10 ip 10.10.10.1
 standby 10 priority 110
 standby 10 preempt
 standby 10 track 1 decrement 30
router ospf 10
 router-id 1.1.1.1
 passive-interface GigabitEthernet0/0
 network 10.10.10.0 0.0.0.255 area 0
 network 10.0.13.0 0.0.0.3 area 0
```

## Configure R2

[Configuration delta](apply/R2.cfg)

```text
interface GigabitEthernet0/0
 standby version 2
 standby 10 ip 10.10.10.1
 standby 10 priority 100
 standby 10 preempt
router ospf 10
 router-id 2.2.2.2
 passive-interface GigabitEthernet0/0
 network 10.10.10.0 0.0.0.255 area 0
 network 10.0.23.0 0.0.0.3 area 0
```

## Configure R3

[Configuration delta](apply/R3.cfg)

```text
router ospf 10
 router-id 3.3.3.3
 passive-interface Loopback0
 network 10.0.13.0 0.0.0.3 area 0
 network 10.0.23.0 0.0.0.3 area 0
 network 203.0.113.10 0.0.0.0 area 0
```

## Why this works

HSRP gives the client a gateway independent of either router address. R1 starts at 110, but the tracked uplink failure reduces its priority to 80. R2 at priority 100 can then preempt and use its own OSPF uplink; the upstream also removes the failed path.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
