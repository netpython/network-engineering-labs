# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure R1

[Configuration delta](apply/R1.cfg)

```text
interface GigabitEthernet0/0
 ip helper-address 10.0.12.2
```

## Configure R2

[Configuration delta](apply/R2.cfg)

```text
ip route 10.10.10.0 255.255.255.0 10.0.12.1
ip dhcp excluded-address 10.10.10.1 10.10.10.20
ip dhcp pool CLIENTS
 network 10.10.10.0 255.255.255.0
 default-router 10.10.10.1
 dns-server 192.0.2.53
 lease 0 1
```

## Why this works

R1 relays the client broadcast to R2 with the client-facing address in giaddr. R2 chooses the matching remote subnet pool and returns the offer through its route to R1. The excluded range reserves addresses for infrastructure.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
