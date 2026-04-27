# Enterprise-Risk-Assessment-Goldshadow
This repository contains a comprehensive Network Security Risk Assessment for "Goldshadow," an organization that recently opened a new corporate office in Northeast England to serve as its central hub for HR operations.

The physical environment presented unique security challenges: the company rented the ground and third floors of a 5-story building, leaving an unmanaged gap between the floors. This report analyzes the proposed network topology, identifies critical physical and logical vulnerabilities, and provides a prioritized "Defense in Depth" mitigation strategy.

## ⚠️ Key Risks Identified

### Physical Vulnerabilities
* [cite_start]**Fragmented Floor Plan:** The physical separation between the ground floor and third floor necessitated an unsecured communication link traversing unmanaged space[cite: 238, 239].
* [cite_start]**Unsecured Infrastructure:** Plans to connect the floors via Ethernet over Power (EoP) adapters or high-speed Wi-Fi introduced severe risks of data interception and electromagnetic interference[cite: 153, 240, 242].
* [cite_start]**Server Room Placement:** Critical servers and networking hubs were located in high-traffic, semi-public zones (like Reception) or standard open offices, increasing the risk of unauthorized physical access[cite: 244, 245, 247].

### Logical & Network Vulnerabilities
* [cite_start]**Flat Network Architecture:** The initial design lacked segmentation, allowing open access Wi-Fi in the Recreation Area to connect directly to the main switch structure, creating a backdoor into sensitive HR and Legal networks[cite: 261, 262, 273].
* [cite_start]**Rogue Devices:** The topology revealed an unauthorized "Sniffer" device attached to the internal switch, indicating active traffic interception[cite: 266, 267].
* [cite_start]**Cleartext Routing:** The use of EIGRP without authentication left the network vulnerable to route poisoning[cite: 274, 275].

## 🛡️ Proposed Mitigation Strategy
To address these vulnerabilities and ensure compliance with strict data protection regulations for HR and Legal data, the following remediations were designed:

1. [cite_start]**Logical Segmentation (VLANs):** Re-architected the flat network into strict VLANs (e.g., VLAN 20 for HR, VLAN 30 for Legal, VLAN 50 for Servers) to isolate broadcast domains and enforce "Zero Trust" boundaries[cite: 298, 301].
2. **Inter-Floor Encryption & Cabling:** Recommended negotiating a dedicated fiber-optic vertical riser. [cite_start]As a fallback, mandated WPA3-Enterprise security with EAP-TLS for any wireless bridges[cite: 291, 292, 295].
3. [cite_start]**Edge & Internal Security:** Proposed a Zone-Based Policy Firewall to inspect stateful traffic, alongside strict Port Address Translation (PAT) to obfuscate internal IP schemes[cite: 315, 324].
4. [cite_start]**Endpoint Authentication:** Mandated IEEE 802.1X Port Security and "Sticky MAC" configurations to immediately disable ports if rogue devices (like the Sniffer) are detected[cite: 309, 310, 312].
5. [cite_start]**Site-to-Site VPN:** Engineered a GRE over IPsec tunnel using AES encryption and SHA hashing to secure communications over the public WAN[cite: 320, 321, 394, 395].

## 📂 Files Included
* `Task 1-3-5.docx` / `.pdf`: The complete, detailed Risk Assessment, Subnetting Strategy, and Security Implementation report.
