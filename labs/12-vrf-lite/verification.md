# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect R1

```text
show ip vrf
show ip route vrf BLUE
show ip route vrf RED
show ip arp vrf BLUE
show ip arp vrf RED
show ip route
```

## Acceptance check 1 · R1

```text
ping vrf BLUE 10.10.10.10 repeat 5
```

Resolves and reaches only BLUE-PC.

## Acceptance check 2 · R1

```text
ping vrf RED 10.10.10.10 repeat 5
```

Resolves and reaches only RED-PC.

## Acceptance check 3 · R1

```text
ping 10.10.10.10 repeat 5
```

Fails in the global table. Disconnect BLUE-PC and repeat both VRF pings to prove independent forwarding.
