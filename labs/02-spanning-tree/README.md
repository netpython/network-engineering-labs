# Control the spanning-tree root

**Switching · Foundation · approximately 40 minutes**

## Scenario

A campus has three switches connected in a triangle. The operations team needs a predictable root location and a known recovery path when the direct uplink fails.

## Objectives

1. Build a triangle of trunks carrying VLAN 10.
2. Make SW1 the root and SW2 the secondary root using explicit priorities.
3. Predict and observe the alternate port, then test reconvergence.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

Start with all three inter-switch ports shut until trunk and STP configuration is ready. Never enable PortFast on these links.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)

## Extension challenge

Predict which switch becomes root after both SW1 links are disconnected.
