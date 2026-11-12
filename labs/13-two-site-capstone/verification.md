# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect D1

```text
show standby brief
show track 1
show ip ospf neighbor
```

## Inspect D2

```text
show standby brief
show ip route ospf
```

## Inspect EDGE

```text
show ip ospf neighbor
show ip route ospf
show ip nat translations
show ip nat statistics
```

## Inspect BRANCH

```text
show ip route ospf
```

## Inspect SWA

```text
show interfaces trunk
show vlan brief
```

## Acceptance check 1 · A-USERS

```text
ping 10.1.20.20
```

Succeeds between site A VLANs.

## Acceptance check 2 · A-USERS

```text
ping 10.2.30.30
```

Succeeds across sites.

## Acceptance check 3 · B-USERS

```text
ping 10.1.20.20
```

Succeeds with a return route.

## Acceptance check 4 · A-USERS

```text
ping 203.0.113.10
```

Succeeds through PAT on EDGE.

## Acceptance check 5 · B-USERS

```text
ping 203.0.113.10
```

Succeeds through PAT on EDGE.

## Acceptance check 6 · D1

```text
configure terminal
interface GigabitEthernet0/1
 shutdown
end
```

D1 priorities fall to 70, D2 preempts at 100, and OSPF withdraws the failed path. Repeat cross-site and Internet pings after convergence. Restore no shutdown and observe D1 preemption.
