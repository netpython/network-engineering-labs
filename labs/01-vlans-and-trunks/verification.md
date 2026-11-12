# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect SW1

```text
show vlan brief
show interfaces trunk
show mac address-table dynamic
```

## Inspect SW2

```text
show interfaces trunk
```

## Acceptance check 1 · PC1

```text
ping 10.10.10.12
```

Succeeds after ARP resolution.

## Acceptance check 2 · PC3

```text
ping 10.10.20.14
```

Succeeds after ARP resolution.

## Acceptance check 3 · PC1

```text
ping 10.10.20.13
```

Fails because hosts have no gateway and VLANs are isolated.
