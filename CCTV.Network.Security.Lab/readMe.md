markdown
# Physical Deployment & Security Hardening of a CCTV Network (DW Spectrum IPVMS)

## Project Overview
This project showcases a hands-on, end-to-end deployment of a physical IP camera infrastructure integrated with **Digital Watchdog (DW) Spectrum IPVMS**. Beyond the hardware installation and software setup, the primary core of this lab was applying **System Hardening** and **Network Defense** principles to secure an inherently high-risk IoT environment against unauthorized access, data interception, and lateral network movement.

---

## Part 1: Physical Installation & Infrastructure Setup
*This section highlights field engineering and hardware deployment capabilities.*

* **Surveillance Platform:** DW Spectrum IPVMS (Media Server & Desktop Client).
* **Hardware Deployed:** Installed and wired 25 physical IP cameras Hikvision around 3 office, 14 cameras in the first office, 5 cameras in the second office and 6 cameras in the third office.
* **Physical Infrastructure:** 
  * Ran and crimped Cat6 Ethernet cabling.
  * Deployed a 26 port PoE Switch in each office to power the cameras using Power over Ethernet (PoE).
  * Mounted cameras physically ensuring optimal coverage and tamper-resistant positioning.

---

## Part 2: Security Hardening & Blue Team Controls
*This section highlights cybersecurity remediation and attack surface reduction.*

To ensure the confidentiality, integrity, and availability of the video surveillance infrastructure, the following controls were implemented:

### 1. Identity & Access Management (IAM)
* **Default Credential Remediation:** Permanently changed the factory-default credentials on both the Host Server Operating System and the core DW Spectrum `admin` account.
* **Bulk Device Hardening:** Utilized **DW IP Finder** to push complex, unique administrative passwords across all connected IP cameras, eliminating automated brute-force entry vectors.

### 2. Data Protection & Encryption (In-Transit & At-Rest)
* **Enforced Transport Security (HTTPS):** Configured strict TLS/HTTPS redirection in the Media Server settings to secure web management interfaces and block Man-in-the-Middle (MitM) credential harvesting.
* **Stream Encryption:** Enabled **Video Traffic Encryption** within DW Spectrum to secure live and playback RTSP streams traveling from the server to desktop and mobile clients.
* **Storage Volume Encryption:** Activated **Archive Encryption** (utilizing AES-128-CTR) on the local storage pools. Even if physical hard drives are stolen, the recorded footage remains encrypted and unreadable.

### 3. Network Architecture & Attack Surface Reduction
* **Network Segmentation:** Isolated all CCTV hardware and cameras into a dedicated CCTV VLAN proposed as a security improvement, preventing lateral movement we separated physical network that is in no way connected to the internet to ensure there is no way for the individual cameras to be accessible.
* **Secure Remote Access Topology:** Mitigated external scanning and exploit attempts by avoiding risky traditional port forwarding (exposing TCP Port 7001 directly to the WAN). Instead, remote viewing was achieved via **DW Cloud**, minimizing the external attack surface.

---

## Evidence & Visual Verification
*Below are the verifications of the secure setup (Replace placeholders with your screenshots/diagrams):*

1. **Network Topology Diagram:**
   ![Network Topology](<diagrams/Security Survillance Diagram.png>)

2. **DW Spectrum Security Settings:**
   ![DW Spectrum Hardening](<img/image.png>) 

---

## Key Takeaways & Lessons Learned
1. **IoT Security is Critical:** Physical access to cameras can lead to local network breaches if the infrastructure is not properly segmented.
2. **Defense-in-Depth:** Combining strong authentication, video streaming encryption, and strict network perimeter controls turns an insecure IoT node into a resilient system.
3. **The Power of VMS Tools:** Leveraging advanced built-in security features in professional VMS software like DW Spectrum significantly mitigates risks without requiring third-party heavy tools.