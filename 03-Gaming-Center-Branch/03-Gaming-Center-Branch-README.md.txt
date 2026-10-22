
Project 3: 
High-Density Link Aggregation LAN (The Gaming Center)

📡 Core Infrastructure Architecture
This module documents the engineering and deployment of a high-throughput local area network layer managed by an active Layer 3 Multilayer Switch core.
• Trunk Capacity Optimization: Combined separate physical copper uplinks connecting access-layer switches into high-bandwidth logical pipelines using Link Aggregation Control Protocol (LACP) to maximize data transport capabilities.
• VLAN Subnet Matrix: Segmented the facility into specialized high-performance neighborhoods including Workstations (VLAN 14), Front Desk Staff (VLAN 15), Gamer Guest Wi-Fi (VLAN 16), Common Services (VLAN 17), and Out-of-Band Management (VLAN 209).
• STP Determinism: Configured manual Spanning Tree Protocol (STP) Primary Root Bridge properties on the multilayer switch core, overriding standard priority election lotteries to assert clean loop-mitigation path maps.
• Switch Virtual Interfaces (SVIs): Activated local routing doorways directly on the Core Switch chassis, removing the reliance on a single external router link for local inter-department data delivery.
🛠️ Staging Logs & Troubleshooting Breakthroughs
🔍 Case Study 1: The EtherChannel Loop Storm Failure
• The Symptom: The moment redundant copper cables were plugged in to connect the access switch stack to the core switch, link lights began flashing erratically, switch processing spiked to maximum capacity, and all workstation communications locked up.
• The Diagnosis: The physical links were transmitting traffic before the logical aggregation handshake could form. Because the ports were running in unnegotiated states, Spanning Tree failed to group them cleanly, treating the redundant links as separate parallel paths and triggering an active Layer 2 switching loop broadcast storm.
• The Resolution: Temporarily shut down the active interface ranges, configured the channel-group parameters using active LACP negotiation mode, and verified that 802.1Q trunk encapsulations were locked on the resulting Port-Channel interface before re-enabling the lines.
🔍 Case Study 2: The SVI Static Routing Dead-End
• The Symptom: Workstations could successfully ping their local Layer 3 switch gateways and communicate across internal VLANs, but all data transmissions attempting to exit out to the public internet core failed completely.
• The Diagnosis: Traced the packet paths down from the workstation to the core switch. Although the switch was cleanly routing traffic between internal departments, it was completely missing a default route instruction pointing up to the Edge Router, causing it to discard all unknown destination frames.
• The Resolution: Entered the global configuration mode on the Layer 3 switch and injected a static default route pointing directly to the Edge Router's transit link interface, establishing an outbound exit highway for all store subnets.
🔍 Case Study 3: The Missing Router-Side Return Path Summary
• The Symptom: After adding the default route to the core switch, public internet packets would successfully leave the workstations and reach the Edge Router, but return ping confirmation responses timed out completely on the bounce back.
• The Diagnosis: Inspected the routing table of the Edge Router. While the router knew how to communicate with its immediate point-of-point transit link, it possessed zero knowledge of the underlying 192.168.14.x or 192.168.16.x gaming center subnets sitting down behind the core switch, causing it to drop the return frames.
• The Resolution: Configured a comprehensive static summary route on the Edge Router pointing back to the core switch transit IP. This clean, single-line summary instruction immediately restored perfect bidirectional path communication for all internal subnets.
🧪 End-to-End Operational Verification
• Bandwidth Aggregation Success: Access switches successfully share high-throughput bundled uplinks to prevent backbone link saturation during concurrent high-volume game data requests.
• Resilient Link Failover: Unplugging a single physical copper link within the active LACP bundle causes absolutely zero loss of packet connectivity, as the remaining link dynamically handles the active traffic weight in milliseconds.
• Inter-VLAN Core Routing: The multilayer switch successfully routes internal traffic between the workstation subnets, local servers, and out-of-band management zones via its active Switch Virtual Interfaces (SVIs).