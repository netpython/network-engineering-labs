# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect R1

```text
show ip nat translations
show ip nat statistics
show ip route 0.0.0.0
```

## Inspect ISP

```text
show ip route
```

## Acceptance check 1 · PC1

```text
ping 203.0.113.10
```

Succeeds and creates an ICMP translation while the traffic is active.

## Acceptance check 2 · R1

```text
show ip nat translations
```

Shows 10.10.10.10 translated to 198.51.100.2; ICMP translations can expire quickly.
