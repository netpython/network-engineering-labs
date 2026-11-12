# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure R1

[Configuration delta](apply/R1.cfg)

```text
ip prefix-list EXPORT seq 10 permit 192.0.2.0/24
router bgp 65001
 bgp router-id 1.1.1.1
 neighbor 10.0.12.2 remote-as 65002
 neighbor 10.0.12.2 prefix-list EXPORT out
 network 192.0.2.0 mask 255.255.255.0
 network 10.99.1.0 mask 255.255.255.0
```

## Configure R2

[Configuration delta](apply/R2.cfg)

```text
router bgp 65002
 bgp router-id 2.2.2.2
 neighbor 10.0.12.1 remote-as 65001
 network 198.51.100.0 mask 255.255.255.0
```

## Why this works

The network statements originate prefixes whose exact connected routes exist. R1 applies EXPORT outbound, so 192.0.2.0/24 is advertised and the implicit deny suppresses 10.99.1.0/24 toward R2. The session remains established while export policy controls reachability.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
