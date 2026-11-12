# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect R1

```text
show ip interface GigabitEthernet0/0
```

## Inspect R2

```text
show ip dhcp pool
show ip dhcp binding
show ip route 10.10.10.0
```

## Acceptance check 1 · PC1

```text
ip dhcp
```

Obtains an address from 10.10.10.21 through 10.10.10.254 and gateway 10.10.10.1.

## Acceptance check 2 · PC1

```text
show ip
```

Shows the lease and gateway.

## Acceptance check 3 · PC1

```text
ping 10.0.12.2
```

Succeeds via R1 and the return route.
