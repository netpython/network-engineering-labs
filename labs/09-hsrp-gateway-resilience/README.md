# Build a redundant default gateway

**Resilience · Intermediate · approximately 50 minutes**

## Scenario

A client subnet must retain its default gateway when the preferred router loses its upstream link. Combine a virtual gateway, preemption, link tracking and dynamic return routes.

## Objectives

1. Create HSRP group 10 with virtual IP 10.10.10.1.
2. Prefer R1 with priority 110 and preemption. Track its uplink and decrement priority by 30 if it fails.
3. Use OSPF upstream and demonstrate packet forwarding before and after R1 uplink failure.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

PortFast is appropriate on SW1 links to routed router interfaces. The upstream R3 and access SW1 remain single points of failure.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)
