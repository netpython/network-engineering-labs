# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure SW1

[Configuration delta](apply/SW1.cfg)

```text
vlan 10
 name VLAN10
spanning-tree mode rapid-pvst
spanning-tree vlan 10 priority 4096
interface GigabitEthernet0/0
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10
 no shutdown
interface GigabitEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10
 no shutdown
```

## Configure SW2

[Configuration delta](apply/SW2.cfg)

```text
vlan 10
 name VLAN10
spanning-tree mode rapid-pvst
spanning-tree vlan 10 priority 8192
interface GigabitEthernet0/0
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10
 no shutdown
interface GigabitEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10
 no shutdown
```

## Configure SW3

[Configuration delta](apply/SW3.cfg)

```text
vlan 10
 name VLAN10
spanning-tree mode rapid-pvst
spanning-tree vlan 10 priority 32768
interface GigabitEthernet0/0
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10
 no shutdown
interface GigabitEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10
 no shutdown
```

## Why this works

Explicit priorities make the root election reproducible. Rapid PVST removes the forwarding loop for VLAN 10 by assigning an alternate role on one redundant path. A link failure allows a surviving path to transition after protocol convergence.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
