# Serve a remote subnet with DHCP relay

**IP services · Intermediate · approximately 40 minutes**

## Scenario

A new client segment uses a centralized DHCP service on another router. Configure the pool, relay and return routing so the client can boot without a static address.

## Objectives

1. Create a DHCP pool on R2 for the remote client subnet.
2. Relay broadcasts from R1 and route replies back to the client LAN.
3. Exclude infrastructure addresses and validate the acquired lease.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

192.0.2.53 is a documented sample DNS option. A DNS server is not deployed in this exercise.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)

## Extension challenge

Explain the role of giaddr in choosing the remote pool.
