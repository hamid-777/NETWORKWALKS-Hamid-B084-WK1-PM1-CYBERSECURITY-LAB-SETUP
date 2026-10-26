<h1 align="center">Cybersecurity Lab Environment Setup</h1>

## 1. Project Overview
In this project, I built a basic cybersecurity laboratory using VirtualBox and Kali Linux.

The purpose of this lab is to create a safe environment where I can learn cybersecurity, practice penetration testing, and experiment with different security tools.

I configured a private virtual network for Kali Linux so that I can add other virtual machines and use them as targets for authorized security testing.

## 2. Project Objectives
The main objectives of this project are:

• Install 7-Zip and VirtualBox.

• Download and import Kali Linux.

• Create a private NAT Network.

• Connect Kali Linux to the virtual network.

• Configure and check the IP address.

• Test network and Internet connectivity.

• Verify DNS resolution and Nmap Installation.

• Create a clean virtual machine snapshot.

• Document the setup for future projects.

## 3. Tools and Requirements
Before starting, I prepared the following tools:

| Tool | Purpose |
| :--- | :--- | 
| 7-Zip | Extract compressed Kali Linux files |
| VirtualBox | Run virtual machines | 
| Kali Linux | Operating system for cybersecurity testing |
| Terminal | Run commands and check network settings |

## 4. Step 1: Install 7-Zip
First, I downloaded 7-Zip from its official website and installed it on my computer.

7-Zip is used to extract compressed files. It is useful when downloading a Kali Linux virtual machine packaged in a .7z archive.

After installation, I was ready to extract the Kali Linux files if required.

<img width="811" height="90" alt="image" src="https://github.com/user-attachments/assets/8ba42534-b7e0-4785-ac44-fe05933928d8" />

## 5. Step2: Install VirtualBox
Next, I downloaded and installed VirtualBox.

VirtualBox is a virtualization program that allows us to run another operating system inside our computer without replacing the main operating system.

For this project, I used VirtualBox to run Kali Linux as a virtual machine (VM).

After installation, I opened VirtualBox and prepared to configure the virtual network.

<img width="811" height="96" alt="image" src="https://github.com/user-attachments/assets/a8335c40-6240-48a3-9b83-217a446a7ed4" />

## 6. Step 3: Create a Private NAT Network
I created a dedicated NAT Network in VirtualBox for my cybersecurity laboratory.

A NAT Network allows virtual machines connected to the same network to communicate with each other and access external networks through network address translation.

### Network Configuration
| Setting | Value |
| :--- | :--- | 
| Network Name | NATNetwork |
| IPv4 Prefix | 10.0.0.0/24 | 
| DHCP | Enabled |
| IPV6 | Disabled |

### Steps
1. Open VirtualBox.
2. Open the Network settings or Network Manager.
3. Find the NAT Networks section.
4. Create a new NAT Network.
5. Set the network name NATNetwork.
6. Set the IPv4 prefix to 10.0.0.0/24.
7. Enable DHCP
8. Disable IPv6 if it is not needed.
9. Save the configuration.

<img width="1917" height="1197" alt="Network" src="https://github.com/user-attachments/assets/bfd1bab2-af91-4ebb-8fae-8a6159010902" />

<img width="1916" height="1197" alt="NAT IP" src="https://github.com/user-attachments/assets/2a7b745b-8780-4e7d-b6b2-7222d39cd38a" />

### Why did i use a NAT Network?
I want to add more virtual machines to this lab in the future. A NAT Network allows these machines to communicate with each other while providing outbound network access.

This is useful when building a lab with a Kali Linux machine and seperate tearget machines.

## 7. Step 4: Download and Import Kali Linux
I downloaded the Kali Linux virtual machine from the official Kali Linux website.

I then imported the VM into VirtualBox

If the download is compressed archive, I extracted it using 7-Zip before importing or opening the provided virtual machine file.

<img width="797" height="180" alt="image" src="https://github.com/user-attachments/assets/99cfd8df-6dce-4860-92db-63ec6074e7b5" />

### Configure the virtual machine
I checked the VM settings and configured the network adapter.

| Setting | Value |
| :--- | :--- | 
| Network Adapter | Adapter 1 |
| Attached to | NATNetwork | 
| Network Name | NatNetwork |
| Adapter Type | Intel PRO/1000 MT Desktop |

<img width="1917" height="1197" alt="Kali Linux Settings" src="https://github.com/user-attachments/assets/285d5a5e-b4e9-4092-bdc2-264f45754cb2" />

Note: The available RAM should be suitable for your computer. Kali Linux may run slowly with only 2 GB, espicialy when multiple applications are open.

## 8. Step 5: Start Kali and Configure a Consistent IP Address
A consistent IP address makes it easier to identify and manage the Kali Linux machine during future exercises.

For this lab, the intended configuration was:

| Setting | Value |
| :--- | :--- | 
| IP Address | 10.0.0.2 |
| Subnet Mask | 24 | 
| Gateway | 10.0.0.1 |
| DSN Server | 10.0.0.1 |

<img width="1917" height="1197" alt="Kali Linux IP" src="https://github.com/user-attachments/assets/0f3c4dc1-f439-40d9-9305-b6ebcdcfd8ba" />

## 9. Step 6: Test Network Connectivity
After configuring the network, I performed several tests to confirm that Kali Linux could communicate with the network and access the Internet.

<img width="1917" height="1197" alt="Searching google" src="https://github.com/user-attachments/assets/e744bf1d-3acc-480a-944e-dc9ed356e801" />

## 10. Step 7: Create a Clean Virtual Machine Snapshot
After completing the initial configuration and checking the network, I created a snapshot of the Kali Linux virtual machine.

A snapshot saves the VM's state at a particular point in time. It can be used to return to that earlier state f a future experiment causes problems.

### Steps
1. Shut down or prepare the VM according to VirtualBox's snapshot requirements.
2. Open the virtual machine's Snapshots View.
3. Create a new snapshot.
4. Give it a clear name

Example snapshot name: Clean Kali - Lab Setup

I created this snapshot as a clean starting point for future cybersecurity exercises.

Before performing risky experiments, I can restore the VM to this baseline if needed.

## 11. Problems Encountered and Solutions
### Internet Connectivity stopped working
After changing the IPv4 settings manually, Internet connectivity may stop working.

During troubleshooting, I tried the following NetworkManager settings:

`sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0`

This changes the IPv4 duplicate-address-detection timeout for the specified connection. It is not a general fix for NAT or Internet connectivity problems, so it should not be applied unless the setting is relevant to the issues being diagnosed.

## 12. What I learned
Through this project, I learned the basics of building a virtual cybersecurity laboratory.

The main things I learned were:
1. Virtualization: How to run Kali Linux inside VirtualBox without replacing my main operating system.
2. NAT Networks: How multiple virtual machines can communicate on a shared virtual network while using NAT for external connectivitiy.
3. Network configurations: How to check IP addresses, routing tables, gateways, and DNS settings.
4. Network troubleshooting: How to use basic Linux commands to investigate connectivity problems.
5. Virtual machine snapshots: How to create a recovery point before performing experiments.
6. Cybersecurity lab preparation: How to prepare an environment for future reconnaissance, scanning, and vulnerability assessment exercises.
7. Documentation: How to record configurations, commands, problems, and solutions in a structured way.

## 13. Project Information

• Program: Cybersecurity Internship at NETWORKWALKS

• Week: 01

• Project: Cybersecurity and Penetration Testing Lab Setup

• Repository: GitHub

• Author: Hamid Sheraz

• LinkedIn: www.linkedin.com/in/hamid-sheraz-242000257
