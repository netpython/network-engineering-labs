# Provide Internet access with PAT

**IP services · Intermediate · approximately 40 minutes**

## Scenario

A private client needs access to a simulated public service. The provider has no route to the private subnet, so translate client traffic at the edge.

## Objectives

1. Identify inside and outside interfaces.
2. Translate the client subnet to the R1 outside address with overload.
3. Reach a simulated Internet endpoint without installing a private LAN route on ISP.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

The ISP loopback simulates a public endpoint. The lab has no real Internet connection.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)
