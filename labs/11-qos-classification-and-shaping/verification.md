# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect R1

```text
show class-map
show policy-map interface GigabitEthernet0/0
show policy-map interface GigabitEthernet0/1
```

## Acceptance check 1 · PC1

```text
ping 203.0.113.10
```

Succeeds and increases the TEST-CLASS matched packet count.

## Acceptance check 2 · R1

```text
show policy-map interface GigabitEthernet0/1
```

Shows the 1000000 bps shaping target and egress packets. Idle or light traffic does not prove rate enforcement.
