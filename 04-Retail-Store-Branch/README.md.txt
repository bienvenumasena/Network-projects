
Project 5 (On going project)
Fused Telecom MSP Campus Core. 

📡 Core Infrastructure Architecture
This project documents the culmination of the enterprise portfolio: fusing all preceding standalone branch modules into a single, unified Managed Service Provider (MSP) network campus engineered entirely from the ground up.
• Centralized Cloud Core Architecture: Reorganized Building B to act as a Tier-3 Data Center and Network Operations Center (NOC) controlling the multi-tenant OSPF routing backbone.
• Identity & Service Consolidation: Deployed centralized Windows Server Active Directory Domain Controllers, global enterprise DNS maps, and centralized corporate web assets inside the server core network.
• Distributed Architecture Tracking: Routed separated storefront tenants from the Building A retail park back to the central server farm across Layer 3 boundaries using distributed DHCP Relay configurations.
• Enterprise Competency Validated: Proved advanced proficiency across multi-VLAN segmentation, HSRP gateway failover, LACP EtherChannel link convergence, dynamic multi-area OSPF routing, NAT/PAT translation engine staging, and end-to-end packet path analysis via the OSI model.
🛠️ Staging Logs & Troubleshooting Breakthroughs
🔍 Case Study 1: The Multi-Tenant Dynamic Allocation Collision
• The Symptom: When fusing the branches together, client machines across different storefront buildings began pulling conflicting IP ranges or failing to find their designated DHCP directories completely.
• The Diagnosis: Traced the relational mappings across the centralized switch. Because multiple distinct store subnets were now passing through a consolidated core, the original localized DHCP boundaries were overlapping. Routers were misinterpreting helper-addresses because the central server lacked specialized scopes matching each tenant's unique network interface.
• The Resolution: Re-architected the central server's allocation pool using strict multi-scope subdivisions. Verified that every routed sub-interface on the distribution core possessed a corresponding, isolated helper-address link pointing precisely to the central server node.
🔍 Case Study 2: The Core Routing Asymmetric Path Drop
• The Symptom: Workstations in newly integrated branch wings could cleanly send upload metrics out to the centralized server core, but all return confirmations timed out despite both edge endpoints showing a healthy link layer status.
• The Diagnosis: Evaluated transit parameters using hop-by-hop packet path simulations. Packets were navigating up smoothly, but because OSPF dynamic network configurations were updated during live fusion tests, core gateways were computing mismatched asymmetric return paths, causing routers to reject incoming acknowledgment frames as out-of-sequence anomalies.
• The Resolution: Executed global routing state updates across all multilayer switches and flushed cached translation registers, forcing the dynamic neighbor topology maps to cleanly converge on synchronized bidirectional routes.
🔍 Case Study 3: The Broken ISP Internet Return-Highway Typo
• The Symptom: After successfully routing internal branch networks back to the core data center, endpoints across the entire shopping park completely lost their ability to ping the public payment server, turning red right at the ISP core.
• The Diagnosis: Conducted a comprehensive routing table audit across the edge. While the local retail edge router possessed a perfect default gateway pointer and a summarized 192.168.0.0/16 path statement pointing to the switch fabric, a single-digit typo existed in the static return route statement (192.160.0.0/16). Because the summary was misconfigured with a 0 instead of an 8, the return packets arriving at the WAN edge were instantly dropped.
• The Resolution: Entered the edge router CLI, pulled the invalid static configuration string, and injected the mathematically correct ip route 192.168.0.0 255.255.0.0 10.0.0.2 summary statement, immediately restoring flawless internet connectivity to all active tenants.
🧪 End-to-End Operational Verification
• Unified Network Function: A client workstation connected anywhere inside the retail complex automatically boots up, receives its network identity from the central data center, and resolves corporate domain directories.
• Complete Routing Path Mesh: Core routers dynamically calculate and optimize network paths using dynamic OSPF states, automatically adapting if a redundant backbone highway link is severed.
• Enterprise Readiness: The entire infrastructure operates as a robust, fully documented, production-grade Managed Service Provider architecture ready for corporate deployment.