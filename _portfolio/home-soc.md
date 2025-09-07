---
title: "Cybersecurity Home Lab for Attack Detection & Analysis"
excerpt: "An in-progress project building a virtualized lab to simulate, detect, and analyze cyber attacks using pfSense (Firewall) and Wazuh (SIEM/XDR)."
collection: portfolio
---

This project documents my process of architecting and building a virtualized Security Operations Center (SOC) from the ground up. As a practical application of concepts from my CompTIA studies and coursework, the primary objective remains the same: to create a closed-loop environment where I can **launch a real-world attack and see the corresponding alert in an enterprise-grade monitoring tool.**

This portfolio entry serves as a living document, showcasing the build process, the challenges encountered, and the skills being developed along the way.

---

### Lab Architecture & Components

The lab operates on a private, segmented network (`192.168.1.0/24`) managed by a pfSense firewall, ensuring all traffic is monitored and controlled in a safe sandbox environment.

![Network Topology](/images/Topology_of_Project.png)

*The planned network topology, designed in draw.io to serve as the project's architectural blueprint.*

| Role              | Tool/OS             | Purpose                                                                 |
|:------------------|:--------------------|:------------------------------------------------------------------------|
| **Hypervisor**    | Oracle VirtualBox   | Manages and runs all virtual machines on the host.                      |
| **Firewall/Router** | pfSense             | Segments the lab network, controls traffic, and serves as a log source. |
| **SIEM/XDR**      | Wazuh               | Ingests logs, analyzes events, and generates security alerts.           |
| **Attacker VM**   | Kali Linux          | Launches simulated attacks (e.g., port scans, vulnerability exploits).  |
| **Victim VM**     | Metasploitable2     | An intentionally vulnerable Linux server to act as the target.          |

---

### Project Status & Next Steps

I am documenting the entire build process in a detailed lab journal. The core infrastructure is now provisioned, networked, and hardened.

**Completed Milestones:**
*   **Phase 1: Network Provisioning:** All core VMs (pfSense, Wazuh, Kali, Metasploitable2) have been provisioned in VirtualBox and connected to the correct virtual networks.
*   **Phase 2: System Configuration:** The pfSense firewall is installed and configured, providing DHCP and internet access to the lab. The Kali Linux VM has been hardened, and a Wazuh agent has been successfully deployed to it, confirming its connection to the SIEM.

![Wazuh Agent Confirmation](/images/Kali_deployed_agent.png)

*Confirmation in the Wazuh dashboard showing the Kali Linux agent is active and communicating.*

**Current Objective:**
My immediate focus is on fully integrating the **Metasploitable2** victim machine. The current challenge is to **successfully deploy and configure a Wazuh agent on this intentionally vulnerable system.** This involves troubleshooting the installation on an older Linux distribution and ensuring its logs are properly parsed and forwarded to the Wazuh server, which will complete the lab's monitoring instrumentation.

---

### Key Skills Practiced in this Project

*   **Network Architecture & Segmentation:** Deployed and configured a pfSense firewall to create a segmented network with custom routing and DHCP rules.
*   **SIEM/XDR Deployment:** Installed and configured a Wazuh SIEM and successfully deployed an agent to a Debian-based endpoint (Kali Linux).
*   **Problem Solving & Troubleshooting:** Identified and resolved technical issues during the build, such as a pfSense boot loop, demonstrating a systematic approach to debugging.
*   **Virtualization & Systems Administration:** Created, configured, and managed a multi-VM environment using VirtualBox.
*   **Technical Writing & Documentation:** Authored a detailed lab journal documenting the entire build process, configuration steps, and validation checks.

---

### Future Roadmap

Once the Metasploitable2 integration is complete, I plan to expand the lab's capabilities:
1.  **Execute & Analyze Attacks:** Begin launching controlled attacks (Nmap scans, Metasploit exploits) from Kali to validate detection rules in Wazuh.
2.  **Upgrade the Victim Environment:** Replace Metasploitable2 with a **Windows 10 VM** to practice detecting threats more relevant to modern corporate networks.
3.  **Integrate a NIDS:** Add **Suricata** on the pfSense firewall to incorporate signature-based threat detection at the network level.

For a detailed, step-by-step log of the entire lab build process so far, please see the full technical documentation on my GitHub.

[**View the Full Technical Write-up on GitHub**](https://github.com/busch-l/Home-SOC-Lab)
