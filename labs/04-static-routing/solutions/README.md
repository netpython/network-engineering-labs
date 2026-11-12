# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure R1

[Configuration delta](apply/R1.cfg)

```text
ip route 198.51.100.1 255.255.255.255 10.0.12.2
```

## Configure R2

[Configuration delta](apply/R2.cfg)

```text
ip route 192.0.2.1 255.255.255.255 10.0.12.1
ip route 198.51.100.1 255.255.255.255 10.0.23.2
```

## Configure R3

[Configuration delta](apply/R3.cfg)

```text
ip route 192.0.2.1 255.255.255.255 10.0.23.1
```

## Why this works

Each router needs a route toward the destination of a request and the destination of its reply. Using loopback sources makes the return path visible: it cannot rely on the directly connected transport subnet alone.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
