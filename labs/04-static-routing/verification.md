# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect R1

```text
show ip route static
show ip cef
```

## Inspect R2

```text
show ip route static
show ip cef
```

## Inspect R3

```text
show ip route static
show ip cef
```

## Acceptance check 1 · R1

```text
ping 198.51.100.1 source 192.0.2.1 repeat 5
```

Succeeds with both forward and return routes.

## Acceptance check 2 · R3

```text
ping 192.0.2.1 source 198.51.100.1 repeat 5
```

Succeeds in the reverse direction.
