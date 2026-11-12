# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure SW1

[Configuration delta](apply/SW1.cfg)

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
interface GigabitEthernet0/0
 channel-group 1 mode active
interface GigabitEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20
 no shutdown
interface GigabitEthernet0/1
 channel-group 1 mode active
interface Port-channel1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20
 no shutdown
interface GigabitEthernet0/2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20
 no shutdown
interface GigabitEthernet0/3
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 no shutdown
```

## Configure SW2

[Configuration delta](apply/SW2.cfg)

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
interface GigabitEthernet0/0
 channel-group 1 mode active
interface GigabitEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20
 no shutdown
interface GigabitEthernet0/1
 channel-group 1 mode active
interface Port-channel1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20
 no shutdown
interface GigabitEthernet0/2
 switchport mode access
 switchport access vlan 20
 spanning-tree portfast
 no shutdown
```

## Configure R1

[Configuration delta](apply/R1.cfg)

```text
interface GigabitEthernet0/0
 no shutdown
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 10.10.10.1 255.255.255.0
interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 10.10.20.1 255.255.255.0
```

## Why this works

LACP negotiates a logical link from compatible physical members. The port channel carries VLAN tags toward R1, whose dot1q subinterfaces terminate each subnet. R1 routes between the two connected networks and rewrites the Layer 2 header for the destination VLAN.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
