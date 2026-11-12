# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect R1

```text
show standby brief
show track 1
show ip route ospf
```

## Inspect R2

```text
show standby brief
show ip route ospf
```

## Inspect R3

```text
show ip ospf neighbor
```

## Acceptance check 1 · PC1

```text
ping 203.0.113.10
```

Succeeds through R1 initially.

## Acceptance check 2 · R1

```text
configure terminal
interface GigabitEthernet0/1
 shutdown
end
```

Tracking reduces R1 priority to 80 and R2 preempts. Repeat PC1 ping after convergence, then restore no shutdown.
