# Network Engineering Labs

**Build a network, explain its behavior, and prove it works.**

Thirteen progressive Cisco IOS / IOS XE labs lead into a two-site enterprise capstone. The exercises cover switching, routing, BGP, DHCP, NAT, HSRP, ACLs, QoS and VRF-Lite.

`13 guided labs` · `1 capstone` · `Starter and final configs` · `Acceptance checks`

## Follow the learning path

| Lab | Discipline | Level | Time |
| --- | --- | --- | ---: |
| [01 · Build VLANs and an 802.1Q trunk](labs/01-vlans-and-trunks/README.md) | Switching | Foundation | 35 min |
| [02 · Control the spanning-tree root](labs/02-spanning-tree/README.md) | Switching | Foundation | 40 min |
| [03 · Bundle uplinks and route between VLANs](labs/03-lacp-and-intervlan/README.md) | Switching and routing | Intermediate | 50 min |
| [04 · Build a routed path with static routes](labs/04-static-routing/README.md) | Routing | Foundation | 35 min |
| [05 · Build multi-area OSPF](labs/05-multiarea-ospf/README.md) | Routing | Intermediate | 45 min |
| [06 · Exchange and filter eBGP prefixes](labs/06-ebgp-prefix-filtering/README.md) | BGP | Intermediate | 50 min |
| [07 · Serve a remote subnet with DHCP relay](labs/07-dhcp-relay/README.md) | IP services | Intermediate | 40 min |
| [08 · Provide Internet access with PAT](labs/08-nat-pat/README.md) | IP services | Intermediate | 40 min |
| [09 · Build a redundant default gateway](labs/09-hsrp-gateway-resilience/README.md) | Resilience | Intermediate | 50 min |
| [10 · Enforce a small segmentation policy](labs/10-acl-segmentation/README.md) | Security | Intermediate | 40 min |
| [11 · Classify, mark and shape traffic](labs/11-qos-classification-and-shaping/README.md) | QoS | Intermediate | 50 min |
| [12 · Separate overlapping address spaces with VRF-Lite](labs/12-vrf-lite/README.md) | Virtual routing | Advanced | 55 min |
| [13 · Build a resilient two-site enterprise network](labs/13-two-site-capstone/README.md) | Capstone | Advanced | 150 min |
| [14 · Route IPv6 between two loopbacks](labs/14-ipv6-static-routing/README.md) | IPv6 routing | Foundation | 30 min |

## What each lab includes

- Objectives and a concrete scenario.
- Node requirements, exact cabling, address tables, and diagrams for branching or redundant topologies.
- Per-node starter configurations and three progressive hints.
- A solution walkthrough with configuration deltas and complete reference configurations.
- Acceptance checks covering protocol state and packet forwarding.

## Start a lab

Read the [setup guide](docs/setup.md), choose an exercise, and build the topology in your emulator. Load its starter configs onto clean nodes, complete the objectives, and record the results with the [lab report template](docs/lab-report-template.md).

## The capstone

The final exercise connects a two-VLAN campus to a branch through OSPF. Two distribution routers provide tracked HSRP gateways at site A. An edge router originates a default route and provides PAT toward a simulated Internet endpoint.

Validate cross-VLAN and cross-site forwarding, then disconnect a distribution uplink and observe gateway failover. The reference also identifies remaining single points of failure.

## Platform scope and validation

The first release targets Cisco IOS / IOS XE routing and IOSvL2 switching. You need licensed images with the required features. The address plans, cabling, configuration files and local documentation links have been reviewed offline. Live emulator testing is pending.

MPLS L3VPN, VXLAN/EVPN, iBGP route reflectors and redistribution are candidates for later releases. They are outside the current curriculum.

The exercise format is inspired by objective-driven lab collections such as GNS3Vault. The scenarios, configurations and solutions here are original. See [references](docs/references.md).
