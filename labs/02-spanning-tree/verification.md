# Verification

Record your image version and the observed result for each check. The criteria below are expected behavior, not captured device output.

## Inspect SW1

```text
show spanning-tree vlan 10
show spanning-tree vlan 10 detail
```

## Inspect SW2

```text
show spanning-tree vlan 10
show spanning-tree vlan 10 detail
```

## Inspect SW3

```text
show spanning-tree vlan 10
show spanning-tree vlan 10 detail
```

## Acceptance check 1 · SW1

```text
show spanning-tree vlan 10
```

Identifies SW1 as root. Displayed priority includes the VLAN system ID extension.

## Acceptance check 2 · SW2

```text
configure terminal
interface GigabitEthernet0/0
 shutdown
end
```

The surviving topology reconverges. Observe the SW2-SW3 link, then restore with no shutdown.
