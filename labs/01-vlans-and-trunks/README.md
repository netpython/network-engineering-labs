# Build VLANs and an 802.1Q trunk

**Switching · Foundation · approximately 35 minutes**

## Scenario

Two small access switches must carry separate user groups across one uplink. The hosts already have IP addresses, and the site does not require communication between the groups.

## Objectives

1. Create VLANs 10 and 20 on both switches.
2. Assign access ports and allow only VLANs 10 and 20 across the trunk.
3. Demonstrate same-VLAN reachability and absence of inter-VLAN routing.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

Use images that support the named features. Wait for convergence before assessing forwarding.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)

## Extension challenge

Remove VLAN 20 from one allowed list, observe the impact, then restore it.
