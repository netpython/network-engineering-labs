# 14 · Route IPv6 between two loopbacks

[Catalogue](../../README.md) · [Topology](topology.md) · [Hints](hints.md) · [Verification](verification.md) · [Solution](solutions/README.md)

**Foundation · 30 minutes · IPv6 routing**

Build a two-router IPv6 path using explicit static routes. Explain why a successful ping of the transit neighbor does not prove reachability between loopbacks.

## Prerequisites and environment

Use two licensed IOSv routers supporting IPv6 or compatible IOS XE routers with at least one routed Ethernet interface each. Build the nodes manually in PNETLab, EVE-NG or GNS3 using that emulator's supported image template; see [setup](../../docs/setup.md). No image or pre-imported project is supplied. Replace GigabitEthernet0/0 consistently if your template uses another name. Feature and interface compatibility must be checked on your image; emulator execution has not been performed.

## Tasks

1. Cable the link in the topology table and load the starter configurations on clean, isolated lab nodes.
2. Verify that both transit interfaces are up/up and have the intended global IPv6 addresses.
3. Test the directly connected neighbor. Inspect IPv6 neighbor discovery.
4. Add a route on each router for the other router's loopback /128, using the adjacent global address and outgoing interface.
5. Ping each remote loopback with the local Loopback0 as source.
6. Explain the forward and return routes used by that test.
7. Remove only R2's added static route, repeat the R1 sourced ping, and explain the failure. Restore the exact route and recheck.

Global configuration is intentionally changed in this isolated lab. Never paste these configurations into an existing production router.

## Deliverable

Record the image/release, interface mapping, both routes and sourced-ping results in the [report template](../../docs/lab-report-template.md). Follow every [acceptance check](verification.md). Use the solution only after attempting the tasks.

Documentation-reviewed and checked offline; live IOS/emulator validation pending.
