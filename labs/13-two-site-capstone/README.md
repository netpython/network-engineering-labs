# Build a resilient two-site enterprise network

**Capstone · Advanced · approximately 150 minutes**

## Scenario

An enterprise has two VLANs at site A and a small branch at site B. Build the routed core, resilient campus gateways and a shared simulated Internet edge, then measure recovery after a distribution uplink failure.

## Objectives

1. Build site A VLANs 10 and 20 with redundant router-on-a-stick gateways.
2. Run OSPF through EDGE to site B and advertise a default route from EDGE.
3. Provide PAT for all three LANs toward the simulated Internet.
4. Track distribution uplinks to trigger HSRP failover.
5. Record forwarding, NAT and convergence evidence before and after a controlled failure.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

EDGE, SWA, the WAN to site B, and ISP are single points of failure. Redundancy covers site A gateways and their uplinks. EDGE requires four routed Ethernet interfaces. The simulated Internet is ISP Loopback0, not an external cloud.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)

## Extension challenge

Measure packet loss during failover, then propose a design that also removes the EDGE single point of failure.
