# Enterprise-Risk-Assessment-Goldshadow
This repository contains a comprehensive Network Security Risk Assessment for "Goldshadow," an organization that recently opened a new corporate office in Northeast England to serve as its central hub for HR operations.

The physical environment presented unique security challenges: the company rented the ground and third floors of a 5-story building, leaving an unmanaged gap between the floors. This report analyzes the proposed network topology, identifies critical physical and logical vulnerabilities, and provides a prioritized "Defense in Depth" mitigation strategy.

## ⚠️ Key Risks Identified

### Physical Vulnerabilities
* **Fragmented Floor Plan:** The physical separation between the ground floor and third floor necessitated an unsecured communication link traversing unmanaged space.
* **Unsecured Infrastructure:** Plans to connect the floors via Ethernet over Power (EoP) adapters or high-speed Wi-Fi introduced severe risks of data interception and electromagnetic interference.
* **Server Room Placement:** Critical servers and networking hubs were located in high-traffic, semi-public zones (like Reception) or standard open offices, increasing the risk of unauthorized physical access.

### Logical & Network Vulnerabilities
* **Flat Network Architecture:** The initial design lacked segmentation, allowing open access Wi-Fi in the Recreation Area to connect directly to the main switch structure, creating a backdoor into sensitive HR and Legal networks.
* **Rogue Devices:** The topology revealed an unauthorized "Sniffer" device attached to the internal switch, indicating active traffic interception.
* **Cleartext Routing:** The use of EIGRP without authentication left the network vulnerable to route poisoning.

## 🛡️ Proposed Mitigation Strategy
To address these vulnerabilities and ensure compliance with strict data protection regulations for HR and Legal data, the following remediations were designed:

1. **Logical Segmentation (VLANs):** Re-architected the flat network into strict VLANs (e.g., VLAN 20 for HR, VLAN 30 for Legal, VLAN 50 for Servers) to isolate broadcast domains and enforce "Zero Trust" boundaries.
2. **Inter-Floor Encryption & Cabling:** Recommended negotiating a dedicated fiber-optic vertical riser. As a fallback, mandated WPA3-Enterprise security with EAP-TLS for any wireless bridges.
3. **Edge & Internal Security:** Proposed a Zone-Based Policy Firewall to inspect stateful traffic, alongside strict Port Address Translation (PAT) to obfuscate internal IP schemes.
4. **Endpoint Authentication:** Mandated IEEE 802.1X Port Security and "Sticky MAC" configurations to immediately disable ports if rogue devices (like the Sniffer) are detected.
5. **Site-to-Site VPN:** Engineered a GRE over IPsec tunnel using AES encryption and SHA hashing to secure communications over the public WAN.

## 📂 Files Included
* `Task 1-3-5.docx` / `.pdf`: The complete, detailed Risk Assessment, Subnetting Strategy, and Security Implementation report.
