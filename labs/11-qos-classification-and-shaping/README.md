# Classify, mark and shape traffic

**QoS · Intermediate · approximately 50 minutes**

## Scenario

An application test flow must leave the edge with a known DSCP marking and a configured 1 Mbps shaping policy. Separate classification evidence from evidence of rate enforcement.

## Objectives

1. Match traffic from PC1 to the R2 loopback.
2. Mark it AF31 on ingress and shape all egress traffic to 1 Mbps.
3. Verify classifier counters and inspect the DSCP field in a capture.

## Start the exercise

1. Read the [setup guide](../../docs/setup.md) and build the [topology and address plan](topology.md).
2. Load [starter-configs](starter-configs/) onto clean nodes. These files establish only the baseline.
3. Complete the objectives without looking at the solution.
4. Run the [acceptance checks](verification.md), record observed output, and explain the forwarding path.

## Platform notes

Requires an image supporting MQC ingress marking and software egress shaping. Use an emulator link capture to inspect AF31 (DSCP 26). A sustained throughput test requires an additional Linux traffic generator, outside the baseline topology.

[Progressive hints](hints.md) · [Solution](solutions/README.md) · [Lab report template](../../docs/lab-report-template.md)

## Extension challenge

Replace the VPCS node with a lab Linux host and demonstrate the configured rate under sustained load.
