# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect R1

```text
show ip bgp summary
show ip bgp
show ip bgp neighbors 10.0.12.2 advertised-routes
show ip prefix-list EXPORT
```

## Inspect R2

```text
show ip route bgp
show ip bgp
```

## Acceptance check 1 · R1

```text
ping 198.51.100.1 source 192.0.2.1 repeat 5
```

Succeeds.

## Acceptance check 2 · R2

```text
show ip route 10.99.1.0
```

No matching route exists. R2 learns 192.0.2.0/24 instead.
