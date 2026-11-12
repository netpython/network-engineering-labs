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
interface GigabitEthernet0/1
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 no shutdown
interface GigabitEthernet0/2
 switchport mode access
 switchport access vlan 20
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
interface GigabitEthernet0/1
 switchport mode access
 switchport access vlan 10
 spanning-tree portfast
 no shutdown
interface GigabitEthernet0/2
 switchport mode access
 switchport access vlan 20
 spanning-tree portfast
 no shutdown
```

## Why this works

Access ports place each host into its assigned broadcast domain. The trunk transports only the two required tags, and MAC learning provides same-VLAN forwarding. No Layer 3 gateway is configured, so the two subnets remain isolated.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
