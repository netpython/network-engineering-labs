# Exchange and filter eBGP prefixes

**BGP · Intermediate · approximately 50 minutes**

## Scenario

A customer router peers with a provider. Export the public lab subnet while retaining an internal subnet locally, even though both are present in the local BGP table.

## Objectives

1. Establish eBGP and originate exact connected prefixes.
2. Advertise 192.0.2.0/24 from R1 while suppressing its internal 10.99.1.0/24 prefix.
3. Verify the advertisement and the installed routes.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

Use images that support the named features. Wait for convergence before assessing forwarding.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)
