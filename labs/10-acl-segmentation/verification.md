# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect R1

```text
show ip access-lists USER-IN
show ip interface GigabitEthernet0/0
```

## Acceptance check 1 · PC1

```text
ping 10.10.20.20
```

ICMP echo succeeds; the first permit counter increases.

## Acceptance check 2 · PC1

```text
ping 10.10.20.20 -P 17
```

UDP probes time out and the deny counter increases. Check the VPCS help if the image uses different option syntax.
