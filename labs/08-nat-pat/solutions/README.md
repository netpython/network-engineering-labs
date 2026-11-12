# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure R1

[Configuration delta](apply/R1.cfg)

```text
interface GigabitEthernet0/0
 ip nat inside
interface GigabitEthernet0/1
 ip nat outside
ip access-list standard INSIDE-NAT
 permit 10.10.10.0 0.0.0.255
ip nat inside source list INSIDE-NAT interface GigabitEthernet0/1 overload
ip route 0.0.0.0 0.0.0.0 198.51.100.1
```

## Why this works

The source list selects only the inside client subnet. Overload maps client flows to the outside interface address, giving ISP a reachable return destination. R1 uses its default route to forward the translated packets toward the simulated public service.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
