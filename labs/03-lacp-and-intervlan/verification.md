# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect SW1

```text
show etherchannel summary
show interfaces trunk
```

## Inspect SW2

```text
show etherchannel summary
```

## Inspect R1

```text
show ip interface brief
show ip route connected
```

## Acceptance check 1 · PC1

```text
ping 10.10.20.12
```

Succeeds across the trunk, R1 and the port channel.

## Acceptance check 2 · SW1

```text
configure terminal
interface GigabitEthernet0/0
 shutdown
end
```

One member remains bundled; repeat the PC ping and restore no shutdown.
