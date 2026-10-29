# Cybersecurity Lab Setup – Week 1

## Objective
Set up a Kali Linux virtual machine using Oracle VirtualBox and configure its network connectivity and shared folder access.

## Tools Used
- Oracle VirtualBox
- Kali Linux
- Windows host operating system

## Tasks Completed
1. Created and configured a Kali Linux virtual machine.
2. Configured the VirtualBox NAT Network to use the `10.0.0.0/24` subnet.
3. Assigned Kali Linux the static IP address `10.0.0.2/24`.
4. Configured the default gateway and DNS settings.
5. Verified internet connectivity using `ping`.
6. Configured a shared folder to access Windows Downloads from Kali Linux.
7. Enabled bidirectional clipboard and drag-and-drop settings in VirtualBox.

## Verification
- Kali network interface: `eth0`
- Assigned IP address: `10.0.0.2/24`
- Internet connectivity: Verified using `ping -c 4 google.com`
- Shared folder: `/downloads`

## Screenshot Evidence
<img width="859" height="541" alt="image" src="https://github.com/user-attachments/assets/fc07b4ad-9b1a-4818-b267-b7235e31d4f2" />


## Troubleshooting
Initially, the static IP address could not be assigned because the VirtualBox DHCP server was using `10.0.0.2`. I changed the DHCP server address and its allocation range so that the required static IP was available.

The shared folder was recognized by VirtualBox but was not automatically mounted at the expected location. I created the mount point and mounted the shared folder manually.

## Learning Outcome
I learned how to configure a Kali Linux virtual machine, assign a static IP address, verify network connectivity, configure shared folders, and troubleshoot VirtualBox networking issues.
