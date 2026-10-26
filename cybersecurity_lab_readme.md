<div align="center">

# 🔐 Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for penetration testing and ethical hacking practice**
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Praful%20Vadar-C00000?style=flat-square" />
</p>

---

## 📌 Project Overview

This project focuses on setting up a **virtual cybersecurity and penetration-testing laboratory** using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

---

## 🎯 Objectives

The main objectives of this project are to:

- Install and configure VirtualBox.
- Set up Kali Linux as a virtual machine using the official ISO.
- Create a private **NAT Network** (10.0.0.0/24) for the cybersecurity lab.
- Configure network connectivity for Kali Linux.
- Assign a consistent, static IP address to the Kali VM (10.0.0.2).
- Verify network connectivity and DNS resolution.
- Document the complete setup process and troubleshooting steps.
- Prepare the environment for future cybersecurity projects.

---

## 🛡️ Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:
- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice

⚠️ **Important:** This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.

---

## 🏗️ Lab Architecture

<img width="1917" height="1007" alt="Screenshot 2026-10-26 225713" src="https://github.com/user-attachments/assets/51d89445-997b-4037-b6c1-ea9953635643" />


Additional target machines can be added to the same virtual network in future projects.

---

## ⚙️ Lab Configuration

| 🧩 Component       | ⚙️ Configuration   |
| ------------------ | ------------------  |
| 🖥️ Host OS         | Windows             |
| 🧰 Hypervisor      | VirtualBox 7.2.22   |
| 🐉 Security OS     | Kali Linux          |
| 🧠 Kali RAM        | 4096 MB             |
| ⚡ Kali CPUs       | 4                   |
| 💾 Disk Size       | 50.00 GB            |
| 🌐 Virtual Network | NAT Network         |
| 📡 Network Address | 10.0.0.0/24         |
| 🐧 Kali IP Address | 10.0.0.2/24         |
| 🚪 Default Gateway | 10.0.0.1            |
| 🌍 DNS Server      | 10.0.0.1            |

---

# 🪜 Lab Setup Procedure

## Step 1. Create the NAT Network

A dedicated NAT Network was created in VirtualBox to isolate the lab environment while maintaining internet connectivity for the virtual machines.

Configuration:
- **Network Name:** NatNetwork
- **IPv4 Prefix:** 10.0.0.0/24
- **DHCP:** Enabled

<img width="1917" height="1023" alt="Screenshot 2026-10-26 225648" src="https://github.com/user-attachments/assets/3e3cd0e6-283f-4562-b34a-6e951358463e" />


A **NAT Network** was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity. This allows future target VMs to be added to the lab.

---

## Step 2. Configure the Kali Linux VM Hardware

A new virtual machine was created for Kali Linux. The hardware and network settings were configured to ensure smooth performance during penetration testing tasks.

- **Base Memory:** 4096 MB
- **Processors:** 4
- **Network Adapter:** Attached to NAT Network (`NatNetwork`)

<img width="1907" height="1016" alt="Screenshot 2026-10-26 225623" src="https://github.com/user-attachments/assets/33791f9e-b8da-4ec1-9e58-d81690f96fb1" />


---

## Step 3. Configure the Static IP in Kali Linux

After the VM was installed and booted, the network configuration was changed from DHCP to a manual (static) assignment to ensure a consistent IP address (10.0.0.2) for the attacker machine.

Configuration applied via the Network Manager GUI:

```text
IPv4 Method: Manual
Address:     10.0.0.2
Netmask:     24
Gateway:     10.0.0.1
DNS servers: 10.0.0.1
```
<img width="1917" height="1030" alt="Screenshot 2026-10-26 225738" src="https://github.com/user-attachments/assets/8e091d19-4828-4e5b-9e94-0f0598d9538d" />


---

## Step 4. Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.
The snapshot represents the clean baseline of the laboratory. If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

---

# 🔎 Lab Verification

| ✅ Test                        | 🧾 Command                      | 🎯 Expected Result              |
| ----------------------------- | ------------------------------- | ------------------------------- |
| 🌐 Check IP address           | `ip a`                          | IP is 10.0.0.2                  |
| 📡 Test gateway               | `ping 10.0.0.1`                 | Successful replies              |
| 🌍 Test Internet connectivity | `ping 8.8.8.8`                  | Successful replies              |

---

# 🐞 Problems Encountered & Solutions

## Problem 1. Internet Connectivity After Static IP Configuration

After manually configuring the IPv4 settings, the network connection failed to initialize properly. 

This issue was resolved by modifying the connection timeout settings and resetting the network interface via the terminal:

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

<img width="1917" height="1011" alt="Screenshot 2026-10-26 225105" src="https://github.com/user-attachments/assets/04922e3b-0fe5-481c-a75b-2ea04d3882b0" />


After running these commands, the connection successfully activated and internet connectivity was restored.

---

# 💡 What I Learned

Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I learned include:

### 1. Resource Allocation
I learned how to appropriately scale virtual hardware (RAM and CPUs) based on the host machine's available resources to ensure smooth operation of the attacking VM without degrading host performance.

### 2. NAT Network Configuration
I learned that a NAT Network allows multiple VMs to communicate internally (essential for a lab with attacker and target machines) while still providing outbound internet access for tool updates.

### 3. Static IP & Troubleshooting
I learned how to configure IPv4 addressing manually and how to use `nmcli` in the terminal to troubleshoot and restart network interfaces when GUI configurations fail to apply immediately.

---

# 🔐 Security & Ethical Use

This laboratory is intended strictly for education purposes only.

---

# 👤 Author

**Praful Ramchandra Vadar**
Cybersecurity Diploma Student , Maharashtra<img width="1917" height="1007" alt="Screenshot 2026-10-26 225713" src="https://github.com/user-attachments/assets/0de37659-4d40-4749-b2cf-b259bc596624" />
