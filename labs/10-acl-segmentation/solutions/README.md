# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure R1

[Configuration delta](apply/R1.cfg)

```text
ip access-list extended USER-IN
 10 permit icmp host 10.10.10.10 host 10.10.20.20 echo
 20 deny ip 10.10.10.0 0.0.0.255 10.10.20.0 0.0.0.255
 30 permit ip any any
interface GigabitEthernet0/0
 ip access-group USER-IN in
```

## Why this works

An extended ACL matches protocol, source, destination and ICMP type in order. The host-specific echo permit precedes the subnet deny. The ACL applies only as traffic enters the user-facing interface, so server replies use a different direction.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
