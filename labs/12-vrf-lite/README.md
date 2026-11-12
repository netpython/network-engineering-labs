# Separate overlapping address spaces with VRF-Lite

**Virtual routing · Advanced · approximately 55 minutes**

## Scenario

Two tenants use the same subnet and host IP. Place each tenant in its own routing instance and show that identical lookups resolve independently.

## Objectives

1. Create BLUE and RED VRFs using classic IOS ip vrf syntax.
2. Reuse the same subnet, gateway and host IP in separate routing tables.
3. Demonstrate per-VRF route and ARP separation without route leaking.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

Applying ip vrf forwarding removes an existing interface IP address on IOS, so assign the address afterward. This is VRF-Lite and does not use MPLS labels.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)

## Extension challenge

Add a second router and design a dedicated routed interconnect for each VRF.
