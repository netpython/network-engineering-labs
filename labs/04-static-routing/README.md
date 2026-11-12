# Build a routed path with static routes

**Routing · Foundation · approximately 35 minutes**

## Scenario

Two remote loopbacks represent services at opposite ends of a three-router path. The transport links are addressed, and you must provide specific routes in both directions.

## Objectives

1. Add specific static routes for the two loopbacks.
2. Provide forward and return routes through R2.
3. Explain why next-hop reachability alone does not prove end-to-end reachability.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

Use images that support the named features. Wait for convergence before assessing forwarding.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)
