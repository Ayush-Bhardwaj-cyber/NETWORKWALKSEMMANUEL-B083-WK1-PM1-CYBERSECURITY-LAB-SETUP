# 🛡️ Networkwalks – Week 1 Cybersecurity Lab Setup

## 📌 Project Overview

This repository documents my Week 1 lab setup for the **Networkwalks Cybersecurity Internship Program – Batch B083**.

The objective was to create a Kali Linux virtual machine, configure its network settings, establish internet connectivity, and enable file sharing between the Windows host and the virtual machine.

## 🧰 Tools and Technologies

| Tool | Purpose |
|---|---|
| Windows 10 | Host operating system |
| Oracle VirtualBox 7.2 | Virtualization software |
| Kali Linux | Cybersecurity testing environment |
| NAT Network | Virtual machine network connectivity |
| Shared Folders | File transfer between host and VM |
| Terminal | Network configuration and testing |

## 🏗️ Lab Architecture

The lab uses a Windows host running VirtualBox, with Kali Linux connected to a VirtualBox NAT Network.

- **Host OS:** Windows 10
- **Virtualization:** Oracle VirtualBox
- **Guest OS:** Kali Linux
- **Network Name:** `NatNetwork`
- **Network Subnet:** `10.0.0.0/24`
- **Kali Linux IP:** `10.0.0.2/24`
- **Gateway:** `10.0.0.1`
- **DNS Servers:** `1.1.1.1`, `8.8.8.8`
- **Shared Folder:** `Downloads`
- **Guest Mount Point:** `/downloads`

## ⚙️ Step-by-Step Implementation

### 1. Install VirtualBox

Installed Oracle VirtualBox on the Windows host to create and manage virtual machines.

VirtualBox provides an isolated environment for running Kali Linux without replacing the host operating system.

### 2. Import Kali Linux

Imported the Kali Linux virtual machine into VirtualBox and started it successfully.

After booting, I verified that the Kali Linux desktop was accessible.

### 3. Configure the NAT Network

Created a VirtualBox NAT Network named `NatNetwork`.

The network was configured with the following settings:

| Setting | Value |
|---|---|
| Network Name | `NatNetwork` |
| IPv4 Prefix | `10.0.0.0/24` |
| DHCP | Enabled |
| IPv6 | Disabled |

The DHCP configuration was adjusted to avoid conflicts with the static IP assigned to Kali Linux.

**Screenshot: NAT Network Configuration**

![VirtualBox NAT Network Configuration](screenshots/nat-network.png)

### 4. Start Kali Linux

Started the Kali Linux virtual machine and verified that the desktop environment was working.

The shared folder was also made accessible from the Kali Linux desktop.

**Screenshot: Kali Linux Desktop**

![Kali Linux Desktop](screenshots/kali-desktop.png)

### 5. Configure the Static IP Address

Configured the Kali Linux network interface `eth0` with a static IPv4 address.

```bash
sudo ip addr add 10.0.0.2/24 dev eth0
sudo ip link set eth0 up
sudo ip route replace default via 10.0.0.1
```

Configured DNS servers:

```bash
sudo nano /etc/resolv.conf
```

Added the following entries:

```text
nameserver 1.1.1.1
nameserver 8.8.8.8
```

Verified the network configuration:

```bash
ip addr show eth0
ip route
```

**Note:** These commands configure the address and DNS for the current session. Persistent network configuration may be required after restarting the virtual machine.

### 6. Configure the Shared Folder

Created a shared folder in VirtualBox with the following settings:

- **Folder Name:** `Downloads`
- **Auto-mount:** Enabled
- **Access:** Read/write
- **Guest Mount Point:** `/downloads`

Created the mount directory inside Kali Linux:

```bash
sudo mkdir -p /downloads
```

Mounted the shared folder:

```bash
sudo mount -t vboxsf Downloads /downloads
```

Verified that the shared files were accessible:

```bash
ls /downloads
```

The files were successfully listed in the terminal.

### 7. Test Internet Connectivity

Tested connectivity to an external IP address:

```bash
ping -c 4 1.1.1.1
```

Tested DNS resolution and connectivity using a domain name:

```bash
ping -c 4 google.com
```

Both tests completed successfully, with four packets received and **0% packet loss** in the displayed domain-name test.

**Screenshot: Shared Files, IP Configuration and Connectivity Test**

![Kali Linux Network and Shared Folder Verification](screenshots/network-and-downloads.png)

## 🐛 Troubleshooting

### Issue 1: Static IP Address Conflict

**Problem:** The desired static IP address could not be assigned because it conflicted with the VirtualBox DHCP configuration.

**Solution:** Adjusted the DHCP server and address pool so that the static address `10.0.0.2` did not overlap with the dynamically assigned range.

### Issue 2: Shared Folder Not Accessible

**Problem:** The shared folder was not immediately available inside Kali Linux.

**Solution:** Verified the VirtualBox shared-folder configuration, created `/downloads`, and mounted the shared folder manually using `mount -t vboxsf`.

### Issue 3: Internet Connectivity Verification

**Problem:** Network configuration needed to be verified after assigning the static IP.

**Solution:** Checked the interface and routing configuration, then tested connectivity using `ping` against an IP address and a domain name.

## 🔐 Security Considerations

- Use a virtual machine to keep cybersecurity lab activities separate from the host environment.
- Perform scanning and penetration-testing exercises only on authorized systems.
- Keep the virtual machine updated.
- Avoid exposing unnecessary services or ports.
- Create a clean VirtualBox snapshot before performing experiments that may affect the system.
- Do not store passwords, private keys, or other sensitive information in the repository.

## 📚 Learning Outcomes

Through this lab, I learned how to:

- Set up a Kali Linux virtual machine using VirtualBox.
- Configure a NAT Network and understand IPv4 subnetting.
- Assign a static IP address and configure a default gateway.
- Configure DNS servers and test network connectivity.
- Create and mount shared folders between Windows and Kali Linux.
- Troubleshoot basic network and shared-folder configuration issues.

## 🚀 Next Steps

- Verify network configuration after a virtual machine reboot.
- Configure persistent network settings if required.
- Create and verify a clean VirtualBox snapshot.
- Continue with network reconnaissance and cybersecurity lab exercises.

## 👨‍💻 Author

**Ayush Bhardwaj**  
Networkwalks Cybersecurity Internship Program – Batch B083

- **GitHub Repository:** [NETWORKWALKSEMMANUEL-B083-WK1-PM1-CYBERSECURITY-LAB-SETUP](https://github.com/Ayush-Bhardwaj-cyber/NETWORKWALKSEMMANUEL-B083-WK1-PM1-CYBERSECURITY-LAB-SETUP)
- **LinkedIn Post:** [View LinkedIn Update](https://lnkd.in/p/e3wQUS7c)

---

*Week 1 – Cybersecurity Lab Setup | Networkwalks Internship Program*
