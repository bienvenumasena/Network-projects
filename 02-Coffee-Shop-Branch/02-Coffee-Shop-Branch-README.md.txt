
Project 2: 
Small Business Edge Isolation (The Coffee Shop)

📡 Core Infrastructure Architecture
This project documents the deployment of a single-site retail storefront network cabled over a lightweight, secure Router-on-a-Stick edge design.
• VLAN Segmentation: Mapped out an 802.1Q sub-interface framework on the edge router to cleanly segment trusted corporate payment traffic from untrusted public customer connections.
• VLAN 12 (Staff & POS Data): Allocated to the private operational subnet 192.168.12.0/24 with an explicit default gateway anchor pinned to the local sub-interface.
• VLAN 13 (Public Guest Wi-Fi): Allocated to the isolated public internet access network 192.168.13.0/24 with an explicit default gateway anchor pinned to the local sub-interface.
• Edge Access Hardening: Bound a strict Inbound Extended Access Control List directly to the public Wi-Fi sub-interface gateway, establishing an un-bypassable firewall block against local wireless scanning.
🛠️ Staging Logs & Troubleshooting Breakthroughs
🔍 Case Study 1: The Implicit Deny DHCP Bootstrap Lockout
• The Symptom: After applying the security access-list to the Guest Wi-Fi sub-interface, public laptops could successfully locate and connect to the SSID broadcast but completely failed to pull an IP address from the router's dynamic DHCP pool.
• The Diagnosis: Deployed the Packet Tracer simulation tool to track the inbound configuration broadcast frame. Because a brand-new wireless client does not yet possess an IP identity, its initialization requests utilize UDP bootstrap protocols. The packet was hitting the top of the ACL, failing to match any explicit permit parameters, and getting discarded by the implicit deny rule at the absolute bottom of the ledger.
• The Resolution: Appended a specialized UDP bypass statement (permit udp any eq bootpc any eq bootps) to line 10 of the access list. This explicitly authorizes unconfigured wireless clients to negotiate UDP ports 67/68 to fetch their network leases before the strict inter-subnet data-plane blocks drop the remaining traffic.
🔍 Case Study 2: The Inter-VLAN Sub-Interface Encapsulation Mismatch
• The Symptom: Workstations cabled into the local switch could communicate perfectly with other machines inside their own department, but all traffic attempting to cross the gateway to reach outside network segments timed out instantly.
• The Diagnosis: Audited the running configuration of the edge router interface. While the sub-interfaces were assigned the correct IP addresses, the 802.1Q VLAN encapsulation tags were mismatched, causing the router to discard incoming frames because it could not map the switch's hardware tags to the corresponding virtual interfaces.
• The Resolution: Entered the interface configuration CLI, re-ordered the sub-interface bindings, and hardcoded the explicit 802.1Q encapsulation parameters to match the switch database IDs, instantly restoring clean gateway communication paths.
🧪 End-to-End Operational Verification
• DHCP Assignment Success: Guest wireless laptops and customer mobile devices seamlessly bypass the access-list gates to lease dynamic IP addresses from the local router pool.
• Data-Plane Traffic Isolation: Staff point-of-sale registers can transmit payment data securely, while guest users are completely blocked from pinging, scanning, or tracing routes into the private business network.
• Public Web Verification: Traffic originating from both corporate and public subnets successfully undergoes address translation at the network boundary to navigate outward toward public destinations.