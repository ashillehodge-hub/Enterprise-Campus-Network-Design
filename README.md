# Enterprise Campus Network Architecture & Routing Design

## Overview
This project models an enterprise campus network infrastructure designed and simulated in Cisco Packet Tracer. The architecture addresses scalability, departmental segmentation, and high-availability routing for an academic institution connecting administrative offices, faculty departments, student residential housing, research library facilities, and a dedicated core server cluster.

---

## Network Architecture & Departmental Zoning

The campus infrastructure is divided into distinct operational zones connected to a central distribution/core Layer 3 routing engine:

* **Administration Zone (`10.2.2.0/27`):** Workstations and administrative management systems (`Server0`, `Server2`) operating on isolated access switching.
* **Faculty & Staff Zone (`10.2.2.64/27`):** Staff computing endpoints and curriculum resources (`Server1`).
* **Residential Housing Zone (`10.2.2.128/27`):** High-density student residential connections (`PC8`, `PC9`, `Server3`).
* **Campus Library Zone (`10.2.2.160/27`):** Public research terminals and institutional access switches.
* **Wireless Mobility Cell:** Linksys WAP integration providing dynamic host mobility for wireless laptops and tablets (`Tablet PC0`–`PC2`).
* **Core Data Center / Server Farm (`192.168.0.0/24`):** Centralized resource farm hosting institutional applications, intranet portals, and databases (`192.168.0.100` – `192.168.0.103`).

---

## Technical Specifications

| Parameter | Configuration / Specification |
| :--- | :--- |
| **Addressing Method** | Variable-Length Subnet Masking (VLSM) on `10.2.2.0/24` & `192.168.0.0/24` |
| **Routing Layer** | Layer 3 Inter-VLAN Routing via sub-interfaces (`Gi0/0.1` through `Gi0/0.161`) |
| **Switching Infrastructure** | Cisco Catalyst 2960 Series Switches with 802.1Q trunking |
| **Wireless Protocols** | 802.11 b/g/n dual-band integration with WAP cells |
| **Simulation Tool** | Cisco Packet Tracer v9.0 |

---

## Verification & Latency Telemetry

All inter-subnet routing paths, default gateways, and server links were systematically validated using ICMP telemetry:
* **Host-to-Server Reachability:** Verified 100% round-trip transmission across departmental zones to core servers (`192.168.0.100`–`192.168.0.103`) with average RTT latency between **1ms and 24ms**.
* **Inter-Departmental Communication:** Successfully routed traffic between subnets (`10.2.2.30`, `10.2.2.62`, `10.2.2.94`, `10.2.2.126`, `10.2.2.158`) with zero packet loss post-ARP learning.
* **Convergence:** Verified ARP cache resolution and routing convergence across multi-switch trunks following topology reloads.

---

## Repository Contents
* `Network Design Cisco Project .pkt` — Complete Cisco Packet Tracer simulation topology.
* `Network Design Project Ashille Hodge.docx` — Full project documentation, network diagram, and ping verification captures.
