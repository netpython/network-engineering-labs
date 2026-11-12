# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect R1

```text
show ip ospf neighbor
show ip route ospf
show ip ospf database summary
```

## Inspect R2

```text
show ip ospf neighbor
show ip route ospf
show ip ospf database summary
```

## Inspect R3

```text
show ip ospf neighbor
show ip route ospf
show ip ospf database summary
```

## Acceptance check 1 · R1

```text
ping 198.51.100.1 source 192.0.2.1 repeat 5
```

Succeeds; the destination loopback is an O IA route on R1.

## Acceptance check 2 · R2

```text
show ip ospf
```

Identifies the router as an ABR.
