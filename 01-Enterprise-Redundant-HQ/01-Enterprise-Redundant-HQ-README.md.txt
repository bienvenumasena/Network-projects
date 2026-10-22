
Enterprise Redundant HQ & Centralized Services


📡 Core Infrastructure Architecture

This module documents the deployment of a highly available, redundant two-building corporate campus linked across a simulated high-speed internet WAN backbone.
• Gateway Redundancy (HSRP): Configured two Layer 3 switches to share a single virtual IP gateway. Provides sub-second automatic traffic failover if a primary hardware chassis loses power, maintaining active corporate sessions seamlessly.
• Centralized Security (VLAN 100): Segmented core network services (DHCP, DNS, and HTTP Web Servers) into a hardened server-cluster neighborhood, isolating critical resources from general employee access layers.
• Cross-Boundary Bootstrapping (DHCP Relay): Implemented DHCP Relay Agents (ip helper-address) across distribution boundaries. Intercepts Layer 2 configuration broadcasts from remote subnets, converting them into target unicast frames to fetch dynamic leases from the central server pool.
• Infrastructure Hardening: Enforced enterprise best practices by reserving static IP address blocks outside active dynamic scopes for all switches, routers, and shared network printers.

🛠️ Staging Logs & Troubleshooting Breakthroughs


🔍 Case Study 1: The Core Trunking Isolation Trap

• The Symptom: Remote workstations could successfully ping local switch doorways, but all data transmissions destined for the central server farm timed out completely.
• The Diagnosis: Traced ICMP frames via simulation mode. While the Server VLAN was defined in the local switch databases, the physical 802.1Q trunk links connecting the access switches were explicitly filtered to only pass original user traffic.
• The Resolution: Audited all backbone trunks and appended VLAN 100 to the authorized allowed-transport logs, ensuring new infrastructure blocks were added without disrupting active department networks.

🔍 Case Study 2: The Silent Multi-Layer Switching Block

• The Symptom: Inter-VLAN routing was entirely dead; separate department subnets remained in total isolation despite all Virtual Interfaces (SVIs) registering an active up/up operational status.
• The Diagnosis: Architectural review revealed the distribution switches were running strictly as standard Layer 2 frame-forwarders out of the box, filtering data by MAC addresses while ignoring destination IP fields.
• The Resolution: Activated the global IP routing engine on the switch core, instantly converting the hardware into an intelligent Layer 3 routing node capable of maintaining routing tables and participating in dynamic OSPF neighbor discoveries.

🔍 Case Study 3: The Bidirectional WAN Routing Black Hole

• The Symptom: Workstations across the WAN link failed to pull dynamic DHCP address assignments from the central pool, and all manual pings to the server network dropped instantly.
• The Diagnosis: Traced the packet path layer-by-layer. Inbound configuration requests successfully traversed the WAN to reach the server, but return frames were dropped because the server's local subnet was missing from the edge router's dynamic routing maps, creating a fatal one-way street.
• The Resolution: Corrected the OSPF area network statements to explicitly include the Server VLAN range, forcing the core to dynamically advertise the server path across the WAN backbone and establishing clean bidirectional communication.

🧪 End-to-End Operational Verification

• DHCP Automation: Endpoints across all departments and remote buildings automatically pull accurate IP configurations, default gateways, and DNS settings.
• Name Resolution: Internal DNS server successfully maps friendly corporate URLs straight to underlying server IP matrices.
• Application Delivery: Client web browsers seamlessly pull the custom corporate homepage from the web server across the WAN, verifying that VLAN tags, OSPF routing paths, HSRP failovers, and DHCP relay configurations are working as a single unified system.