# Solution walkthrough

Apply the following steps to the supplied baseline, in the order listed. Each delta file starts in privileged EXEC mode with configure terminal.

## Configure R1

[Configuration delta](apply/R1.cfg)

```text
ip route 203.0.113.10 255.255.255.255 10.0.12.2
ip access-list extended LAB-TRAFFIC
 permit ip host 10.10.10.10 host 203.0.113.10
class-map match-all TEST-CLASS
 match access-group name LAB-TRAFFIC
policy-map MARK-IN
 class TEST-CLASS
  set dscp af31
policy-map SHAPE-OUT
 class class-default
  shape average 1000000
interface GigabitEthernet0/0
 service-policy input MARK-IN
interface GigabitEthernet0/1
 service-policy output SHAPE-OUT
```

## Configure R2

[Configuration delta](apply/R2.cfg)

```text
ip route 10.10.10.0 255.255.255.0 10.0.12.1
```

## Why this works

The ingress policy uses the access-list classifier to mark the selected flow AF31. The separate output policy shapes class-default traffic at the configured bit rate. Matching counters and an egress capture validate classification and marking; sustained offered load is needed to evaluate shaping behavior.

Read the objectives together with the [topology and address plan](../topology.md), then run every [verification step](../verification.md).

## Rebuild or repeat

The [final configurations](final-configs/) are complete reference snapshots. Load them on clean nodes when rebuilding. Pasting a full configuration into a node merges it with existing settings.

For a fresh attempt, recreate the clean nodes and reload the starter configurations. Restore every interface shut during a failover test before comparing with the reference.
