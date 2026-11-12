# Bundle uplinks and route between VLANs

**Switching and routing · Intermediate · approximately 50 minutes**

## Scenario

A growing site needs more resilient switch uplinks and communication between its user and server VLANs. Keep the Layer 2 bundle separate from the Layer 3 gateway role.

## Objectives

1. Form Port-channel1 with LACP active on both switches.
2. Route VLANs 10 and 20 through router subinterfaces.
3. Verify inter-VLAN forwarding and survival of one member failure.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

The initial switch links are shut to prevent a temporary Layer 2 loop before LACP is configured.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)
