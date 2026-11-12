# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure R1

[Configuration delta](apply/R1.cfg)

```text
router ospf 10
 router-id 1.1.1.1
 passive-interface Loopback0
 network 10.0.12.0 0.0.0.3 area 0
 network 192.0.2.1 0.0.0.0 area 0
```

## Configure R2

[Configuration delta](apply/R2.cfg)

```text
router ospf 10
 router-id 2.2.2.2
 network 10.0.12.0 0.0.0.3 area 0
 network 10.0.23.0 0.0.0.3 area 10
```

## Configure R3

[Configuration delta](apply/R3.cfg)

```text
router ospf 10
 router-id 3.3.3.3
 passive-interface Loopback0
 network 10.0.23.0 0.0.0.3 area 10
 network 198.51.100.1 0.0.0.0 area 10
```

## Why this works

R2 participates in area 0 and area 10, so it can advertise inter-area reachability. Loopbacks are advertised but passive, which avoids unnecessary neighbor discovery on them. R1 and R3 learn the remote loopbacks as inter-area routes.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
