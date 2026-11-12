# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure R1

[Configuration delta](apply/R1.cfg)

```text
ip vrf BLUE
 rd 65000:10
ip vrf RED
 rd 65000:20
interface GigabitEthernet0/0
 ip vrf forwarding BLUE
 ip address 10.10.10.1 255.255.255.0
 no shutdown
interface GigabitEthernet0/1
 ip vrf forwarding RED
 ip address 10.10.10.1 255.255.255.0
 no shutdown
```

## Why this works

Each interface belongs to a separate VRF before its IP is assigned. Connected routes and ARP entries therefore belong to different forwarding contexts despite identical addresses. The global table has neither tenant route.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
