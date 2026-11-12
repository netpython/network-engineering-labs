# Emulator setup

## Image requirements

| Role | Suggested template | Required features |
| --- | --- | --- |
| Router | IOSv router, or compatible IOS XE router | IPv4 routing and the feature named by the lab |
| Switch | IOSvL2 | VLANs, dot1q trunks, Rapid PVST and LACP |
| Client | VPCS | Static IPv4 and DHCP client |

Bring your own licensed images. Set CPU and RAM according to the installed emulator template and the release of the image. Run one exercise at a time.

The configs use GigabitEthernet0/0-style names. Before loading them, map the names to the interfaces exposed by your image. Ensure the node has enough NICs. EDGE in the capstone needs four routed interfaces; the largest switch topology also uses four Ethernet ports.

On fixed-dot1q platforms, omit only the rejected `switchport trunk encapsulation dot1q` lines. Preserve trunk mode, VLAN membership and allowed lists. QoS lab 11 requires an image that implements the specified MQC marking and shaping actions.

## Build the topology

1. Create a separate isolated project for the selected exercise.
2. Place the nodes and connect exactly the ports in its topology table.
3. On a clean Cisco node, decline the setup dialog, enter `enable`, then `configure terminal`. Paste the corresponding starter config. The file ends with `end`.
4. Paste the `.vpc` files at the VPCS console.
5. Review all console errors before attempting the objectives.

Switch interfaces in the starter configs are shut. Configure trunks, VLANs, STP and port channels before bringing them up. Each solution delta enables the relevant ports. Router baselines bring up addressed interfaces but do not implement the exercise's routing protocols or services.

Client IP settings are supplied so you can concentrate on the network feature. In DHCP lab 07, rerun `ip dhcp` after completing relay and server configuration.

## Use the solution

Try the objectives before opening `solutions/`. Delta files in `solutions/apply/` include `configure terminal` and `end`; paste them from privileged EXEC mode on the named node. The solution walkthrough shows the required order.

The complete files in `solutions/final-configs/` are reference configurations to apply to clean nodes. Configuration loading merges commands on an existing node. For a clean reset, recreate the nodes and load the starter configs again.

Wait for convergence before judging an acceptance check. A first ping may lose packets during ARP resolution. Capture the actual output and image version in your lab report.

## Project files and validation

Topologies are documented as diagrams and exact cabling tables. Create them manually in GNS3, PNETLab or EVE-NG. Native emulator projects are not included because image IDs and templates vary.

The repository has been reviewed offline for addresses, links, required files and configuration consistency. Licensed device images are not available in the authoring environment, so live execution remains to be validated. Expected results are described explicitly as acceptance criteria.
