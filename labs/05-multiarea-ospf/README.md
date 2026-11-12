# Build multi-area OSPF

**Routing · Intermediate · approximately 45 minutes**

## Scenario

A backbone router must reach a remote area through an ABR. Build the adjacencies and verify which routes change from intra-area to inter-area at the boundary.

## Objectives

1. Use R2 as an area border router between areas 0 and 10.
2. Advertise loopbacks while making them passive.
3. Distinguish intra-area and inter-area routes.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

Use images that support the named features. Wait for convergence before assessing forwarding.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)
