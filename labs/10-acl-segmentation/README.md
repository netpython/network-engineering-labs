# Enforce a small segmentation policy

**Security · Intermediate · approximately 40 minutes**

## Scenario

A user subnet may send ICMP echo requests to a server, while its other traffic toward that subnet must be denied. Implement the rule at the user ingress and prove both outcomes.

## Objectives

1. Permit only ICMP echo requests from PC1 to PC2 across the user ingress interface.
2. Deny other user-to-server traffic while allowing other routed user traffic.
3. Prove the permitted and denied cases using VPCS packet protocols and ACL counters.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

The policy is directional and stateless. Traffic initiated from PC2 is not blocked by this ingress ACL. Do not describe this as a full stateful firewall policy.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)

## Extension challenge

Design a separate policy for server-initiated traffic without breaking replies.
