# Troubleshooting Notes - Phase 0

## Issue 1: iBGP Routes Not in RIB

Symptom: BGP table shows prefix, but RIB doesn't include it.

Root Cause: iBGP doesn't rewrite next-hop. External next-hop
(e.g. 10.0.2.1) is unreachable by internal peers.

Fix: Apply next-hop-self on border/PE routers.

## Issue 2: Route Not Advertised from CE

Symptom: ISP doesn't have customer prefix.

Root Cause: network command without explicit mask may not inject
route on IOS XE.

Fix:
  CE1(config-router)# no network 192.168.10.0
  CE1(config-router)# network 192.168.10.0 mask 255.255.255.0

## Issue 3: OSPF Neighbor Stuck in EXSTART

Root Cause: MTU mismatch.

Fix: Match MTU on both sides.

## Issue 4: Asymmetric Reachability

Symptom: Outbound ping works, return ping fails.

Root Cause: Return path missing or prefix not advertised.

Fix: Check BGP table on both directions.

## Debugging Workflow

1. Physical: show ip interface brief
2. L3: ping next-hop
3. IGP: show ip route prefix
4. BGP session: show bgp ipv4 unicast summary
5. BGP table: show bgp ipv4 unicast
6. RIB: show ip route bgp
7. Advertised: show bgp ipv4 unicast neighbors IP advertised-routes
