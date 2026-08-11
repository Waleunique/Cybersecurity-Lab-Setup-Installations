# Cybersecurity-Lab-Setup-Installations
Hands-on cybersecurity lab for developing practical skills in Linux, networking, security testing, vulnerability assessment, and incident response using Kali Linux and VirtualBox.
## Project Overview
This project is a hands-on cybersecurity laboratory developed as part of my internship journey and preparation for a career in cybersecurity. The lab provides a controlled environment for applying cybersecurity concepts through practical experimentation using Kali Linux, Oracle VirtualBox, and virtual networking.

The project focuses on developing practical skills in Linux administration, computer networking, network reconnaissance, vulnerability assessment, web application security, network traffic analysis, security monitoring, and incident response.

The laboratory is designed to evolve progressively as new cybersecurity concepts and tools are learned. Each exercise is documented with its objectives, configuration, methodology, commands, results, security implications, troubleshooting processes, and lessons learned.

All security testing within this project is performed in controlled laboratory environments on systems owned by me or where explicit authorization has been provided
<img width="888" height="705" alt="Screenshot 2026-08-11 114341" src="https://github.com/user-attachments/assets/2cb873fd-39c0-4bc0-aec6-0f19f09e0ff2" />

## Key Objectives
- Install and configure VirtualBox
- Install/Import Kali linux as a Virtual machine
- Create a private NAT Network for the cybersecurity lab
- Configure network connectivity for Kali Linux
- Verify network connectivity and DNS resolution
- Take a clean VM snapshot for recovery
- Practise authorized security testing and vulnerability assessment.
- Develop analytical and troubleshooting skills.
- Document security findings and remediation recommendations.

<img width="888" height="705" alt="Screenshot 2026-08-11 114426" src="https://github.com/user-attachments/assets/9d40e0a9-a434-439b-8845-08c237dabe22" />

## 🖥️ Laboratory Environment
<img width="1085" height="751" alt="Screenshot 2026-08-11 114614" src="https://github.com/user-attachments/assets/bf9762d4-1322-4991-a03e-94d4f1ef580b" />

| Component | Configuration | Purpose |
|:---|:---|:---|
| Host OS | Windows | Runs the virtual environment |
| Hypervisor | Oracle VirtualBox | Hosts virtual machines |
| Security OS | Kali Linux | Cybersecurity testing |
| Network | 10.0.0.0/24 | Isolated virtual network |
| Gateway | 10.0.0.1 | Network gateway |
| Kali IP | 10.0.0.2 | Static IP address |
| DNS | 8.8.8.8 / 1.1.1.1 | Domain name resolution |

## Lab Setup Procedure
- Step 1: Install 7-Zip to extract kali linux virtual machine package
- Step 2: Install VirtualBox as the hypervisor
- Step 3: Create the NAT Network [NatNetwork IPv4 Prefix: 10.0.0.0/24 DCHP: Enabled IPv6: Disabled]
- Step 4: Import Kali Linux
- Step 5: Configure the Kali Linux Network
  <img width="1084" height="705" alt="image" src="https://github.com/user-attachments/assets/06d14b63-e953-4b65-9b07-01164cd51531" />

## 🛠️ Challenges & Troubleshooting

This section documents the technical challenges encountered while
building and configuring the cybersecurity laboratory, the
investigation carried out to identify their causes, and the
solutions implemented.

| # | Challenge | Cause | Solution | Status |
|---|---|---|---|---|
| 1 | Kali Linux VM failed to start | Virtualization configuration issue | Adjusted VirtualBox configuration | ✅ Resolved |
| 2 | Kali could not connect to the network | Network connection profile issue | Reconfigured NetworkManager | ✅ Resolved |
| 3 | Static IP `10.0.0.2` could not be assigned | VirtualBox DHCP conflict | Disabled DHCP on the NAT Network | ✅ Resolved |

### Challenge 01 — Static IP Configuration

**Problem**

Kali Linux was unable to activate the network connection when
configured with the static IP address `10.0.0.2`.

**Initial Behaviour**

The connection failed with:

```text
Connection activation failed:
IP configuration could not be reserved

When DHCP was enabled, Kali successfully connected but received
10.0.0.3 instead of the required 10.0.0.2. 
```

## Investigation 

The VirtualBox NAT Network configuration was inspected using:

``` VBoxManage list natnetworks ```

The investigation revealed that the VirtualBox DHCP server was
using 10.0.0.2, creating a conflict with the static IP intended
for Kali Linux.

## Solution

The VirtualBox DHCP server was disabled, allowing 10.0.0.2 to
be assigned exclusively to Kali Linux.

```
Kali was then configured with:
IP Address: 10.0.0.2/24
Gateway:    10.0.0.1
DNS:        8.8.8.8 / 1.1.1.1
```
