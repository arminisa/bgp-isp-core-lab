# BGP ISP Core Lab

A production-grade BGP ISP lab simulating a mid-size ISP's core network with multihoming, iBGP full-mesh, and customer edge connectivity.

## Project Scope

Simulates an ISP (AS 65100) with:
- 2 Upstream providers (Tier-2 ISP simulation)
- 2 Customer Edge routers (SMB customer simulation)
- 6 ISP routers (2 Border, 2 Core, 2 PE)

## Design Overview

| Layer | Role | Protocols |
|-------|------|-----------|
| Upstream | Internet providers | eBGP |
| Border | AS edge (R1, R2) | eBGP + iBGP + OSPF |
| Core | Backbone (R3, R4) | iBGP + OSPF |
| PE | Customer edge (R5, R6) | eBGP + iBGP + OSPF |
| CE | Customer routers | eBGP |

## Repository Layout

- configs/base/ - Full device configurations
- configs/scenarios/ - Per-phase variant configs
- docs/ - Design rationale and documentation
- verification/ - Command outputs
- topology/ - GNS3 project file

## Phases

| Phase | Description | Status |
|-------|-------------|--------|
| 0 | Infrastructure: OSPF + eBGP + iBGP | Complete |
| 4 | Route Reflector | Pending |
| 5 | BGP Communities | Pending |
| 6 | Advanced Filtering | Pending |
| 7 | MPLS L3VPN | Pending |
| 8 | BGP Security | Pending |
| 9 | BGP Convergence | Pending |

## Author

Armin Isa - CCNP Enterprise
