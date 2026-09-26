
NovaTech SARL — Multi-Site Enterprise Network (Cisco Packet Tracer)
Design and implementation of a complete two-site enterprise network for a fictional IT consulting SMB, built as a networking lab project for the Technicien Supérieur Systèmes et Réseaux (TSSR) training program.

Acting as the external network provider, the project covers full network design from a single IP block down to working device configurations: VLSM subnetting, VLAN segmentation, inter-VLAN routing, dynamic routing between sites, centralized services, and security policy enforcement — all built and validated in Cisco Packet Tracer.

Context
NovaTech SARL is a two-site company:

Head office — Lyon: 30 users across 3 departments
Branch office — Grenoble: 12 users across 2 departments
The client provided a single private block, 172.16.0.0/16, to be subnetted efficiently to cover both sites and their interconnection.

Features implemented
VLSM addressing — the /16 block subnetted by actual host count per VLAN, no wasted address space
VLAN segmentation — separate VLANs per department, per site (Direction, Accounting, Guest Wi-Fi, Servers, Tech)
Inter-VLAN routing — Router-on-a-Stick with 802.1Q sub-interfaces on both site routers
Dynamic routing — OSPF (single area, area 0) between the two site routers
Centralized DHCP — one DHCP server at the head office, reached by the branch office via DHCP relay (ip helper-address)
Internal DNS + Web — an internal www.novatech.local resolved and served from the central server
Security via ACLs — the Guest VLAN is blocked from reaching Direction/Accounting; the Tech VLAN is blocked from reaching Direction, while both retain access to core services and simulated Internet
NAT/PAT — shared simulated Internet access for both sites via the head office router
Port Security — 1 MAC address per access port, violation triggers a shutdown
Repository contents
File	Description
NovaTech.pkt	Complete Cisco Packet Tracer topology and device configurations
Rapport_TP_Bonus1_NovaTech_Afzali.pdf (or .docx)	Full technical report: needs analysis, VLSM addressing plan, architecture, device-by-device CLI configuration, test/validation matrix, troubleshooting log
schema-reseau.jpg / .pdf	Hand-drawn network diagram
Addressing plan (summary)
Site	VLAN	Network	Gateway
Lyon	10 — DIRECTION	172.16.0.48/29	172.16.0.49
Lyon	20 — COMPTA	172.16.0.32/28	172.16.0.33
Lyon	30 — INVITES	172.16.0.0/27	172.16.0.1
Lyon	99 — SERVEURS	172.16.0.56/29	172.16.0.57
Grenoble	10 — DIRECTION	172.16.0.80/29	172.16.0.81
Grenoble	40 — TECH	172.16.0.64/28	172.16.0.65
WAN	Lyon ↔ Grenoble	172.16.0.88/30	—
WAN	Lyon ↔ ISP (simulated)	172.16.0.92/30	—
Full addressing table, including every equipment interface, is in the technical report.

Validation
18 functional tests were run to validate the network end to end, covering DHCP assignment across both sites, inter-site connectivity, OSPF adjacency, DNS resolution, Web access, ACL enforcement (both allow and deny paths), NAT/PAT translation, and Port Security violation behavior. Full results are documented in the report.

Tools used
Cisco Packet Tracer
Cisco IOS CLI (VLANs, sub-interfaces, OSPF, ACLs, NAT, Port Security)
Author
Zabiullah Afzali — TSSR training, 2026/2027


