# 🛡️ Networkwalks – Week 1 Cybersecurity Lab Setup

## 📌 Project Overview

This repository documents my Week 1 cybersecurity lab setup for the **Networkwalks Cybersecurity Internship Program – Batch B083**.

The objective was to set up Kali Linux in VirtualBox, configure the virtual network, access shared files, and verify internet connectivity.

## 🧰 Tools Used

| Tool | Purpose |
|---|---|
| Windows 10 | Host operating system |
| Oracle VirtualBox 7.2 | Virtual machine management |
| Kali Linux | Cybersecurity lab environment |
| VirtualBox NAT Network | Network connectivity |
| Shared Folders | Accessing host files from Kali Linux |
| Linux Terminal | Network configuration and testing |

## 🏗️ Lab Configuration

| Component | Configuration |
|---|---|
| Virtual Machine | Kali Linux |
| Virtual Network | `NatNetwork` |
| IPv4 Network | `10.0.0.0/24` |
| DHCP | Enabled |
| IPv6 | Disabled |
| Network Interface | `eth0` |
| Kali Linux IP | `10.0.0.2/24` |
| Shared Folder | `Downloads` |
| Guest Mount Point | `/downloads` |

## ⚙️ Step-by-Step Implementation

### 1. Set Up VirtualBox

Used Oracle VirtualBox to run Kali Linux in a virtual machine on the Windows host.

### 2. Start Kali Linux

Started the Kali Linux virtual machine and accessed its desktop environment.

### 3. Configure the NAT Network

Configured a VirtualBox NAT Network named `NatNetwork`.

The network uses the IPv4 subnet `10.0.0.0/24`. DHCP was enabled, and IPv6 was disabled in the displayed configuration.

**Screenshot: NAT Network Configuration**

<img width="1279" height="747" alt="Screenshot 2026-10-29 192539" src="https://github.com/user-attachments/assets/8a635dcc-1fb5-467b-9121-cb77e068073f" />

### 4. Access the Kali Linux Desktop

Started Kali Linux successfully and accessed its desktop environment.

**Screenshot: Kali Linux Desktop**

<img width="428" height="268" alt="Screenshot 2026-10-29 192822" src="https://github.com/user-attachments/assets/c9e32609-ac3c-4b02-8127-ab8f126dbff7" />

### 5. Configure the Kali Linux Network Interface

Assigned the static IPv4 address `10.0.0.2/24` to the `eth0` network interface and brought the interface up.

Commands used:

```bash
sudo ip addr add 10.0.0.2/24 dev eth0
sudo ip link set eth0 up
```

Verified the interface configuration using:

```bash
ip addr show eth0
```

**Screenshot: Interface configuration**

<img width="439" height="76" alt="image" src="https://github.com/user-attachments/assets/6314124c-d661-4131-b0b8-af0c252a5b48" />

The terminal output showed the assigned IP address and that the interface was up.

### 6. Access the Shared Folder

Accessed the VirtualBox shared folder from Kali Linux using the guest mount point `/downloads`.

The shared folder was mounted with:

```bash
sudo mkdir -p /downloads
sudo mount -t vboxsf Downloads /downloads
```

Verified access to the files using:

```bash
ls /downloads
```

**Screenshot: Downloads Folder**

<img width="859" height="190" alt="image" src="https://github.com/user-attachments/assets/12423e17-1236-4d24-ae06-b8897cbd33e6" />

The terminal displayed the files available in the shared folder.

### 7. Test Internet Connectivity

Tested connectivity and domain-name resolution using:

```bash
ping -c 4 google.com
```

The test completed successfully:

- Packets transmitted: 4
- Packets received: 4
- Packet loss: 0%

This verified that the domain-name ping test succeeded at the time of testing.

**Screenshot: Network Interface and Ping Test**

<img width="428" height="172" alt="Screenshot 2026-10-29 193332" src="https://github.com/user-attachments/assets/49537e52-de1f-41f0-a32b-2b321381858f" />

## 🐛 Troubleshooting

### Static IP Address Conflict

Encountered a conflict between the desired static IP address and the VirtualBox DHCP configuration.

Adjusted the DHCP configuration to resolve the address conflict and allow Kali Linux to use `10.0.0.2`.


## 📚 Learning Outcomes

- Set up and accessed a Kali Linux virtual machine.
- Configured a VirtualBox NAT Network.
- Assigned an IPv4 address to a Linux network interface.
- Accessed shared files through VirtualBox shared folders.
- Used the Linux terminal to inspect network settings.
- Tested connectivity using the `ping` command.
- Troubleshot network address conflicts and shared-folder access.

## 👨‍💻 Author

**Ayush Bhardwaj**

Networkwalks Cybersecurity Internship Program – Batch B083

- **GitHub Repository:** [Cybersecurity Lab Setup](https://github.com/Ayush-Bhardwaj-cyber/NETWORKWALKSEMMANUEL-B083-WK1-PM1-CYBERSECURITY-LAB-SETUP)
- **LinkedIn Update:** [View LinkedIn Post](https://lnkd.in/p/e3wQUS7c)

---

*Week 1 – Cybersecurity Lab Setup*
