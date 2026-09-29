# Home Lab: Network Segmentation & Active Directory

## Overview
A virtualized network built in VirtualBox to practice real-world IT 
infrastructure concepts: firewall/router configuration, network 
segmentation, DNS/DHCP, and Active Directory administration.

## Architecture
- **pfSense** — acts as firewall/router, connects WAN to three 
  internal segments (LAN, Isolated, AD_LAB)
- **Kali Linux** — client machine on LAN, used to access pfSense's 
  web admin panel
- **Windows Server (AD_LAB segment)** — domain controller running 
  Active Directory
- **Windows 11 Enterprise (AD_LAB segment)** — domain-joined client
- **Mr. Robot VM (Isolated segment)** — deliberately vulnerable 
  target, fully walled off from other segments

## What I Built
- Configured pfSense as router/firewall with three separate network 
  interfaces
- Set up DHCP so devices automatically receive IPs on join
- Wrote firewall rules controlling which segments can talk to each 
  other (e.g., Isolated segment cannot reach AD_LAB)
- Deployed Active Directory on Windows Server, created OUs and test 
  user accounts
- Joined a Windows 11 client to the domain

## Problems I Ran Into & How I Fixed Them
- **Kali wouldn't get an IP address** — turned out pfSense wasn't 
  booted first. Learned pfSense needs to be fully up before client 
  VMs, since it's acting as the DHCP server.
- **Windows 10 Enterprise eval no longer available** — Microsoft 
  retired it, so I used Windows 11 Enterprise instead. Had to enable 
  TPM emulation in VirtualBox settings to get past the install 
  requirements.
- **Mr. Robot OVA flagged as a virus on import** — expected, since 
  Vulnhub VMs contain intentionally vulnerable/exploit-style content. 
  Added a Defender exclusion and kept the VM isolated on its own 
  segment with no route to other networks.

## What This Demonstrates
- Understanding of network segmentation and why it matters for security
- Practical firewall rule configuration
- DNS/DHCP fundamentals in a working environment
- Active Directory basics: domain setup, user/OU management, domain-
  joining a client
- Troubleshooting unexpected problems

## Tools Used
VirtualBox, pfSense, Kali Linux, Windows Server 10, 
Windows 11 Enterprise
