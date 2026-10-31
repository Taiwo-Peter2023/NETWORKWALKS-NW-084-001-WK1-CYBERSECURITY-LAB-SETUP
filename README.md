## Networkwalks Cybersecurity Program – Batch B084J | Week 1 Project

## Project Overview

This project focuses on designing and deploying a virtual cybersecurity and penetration testing laboratory using Oracle VirtualBox and Kali Linux.

The objective was to establish a controlled and isolated virtual environment where cybersecurity tools, networking concepts, and penetration testing techniques can be explored and practised safely without interfering with the host computer's primary network environment.

As the first practical assignment in the Networkwalks Cybersecurity Program (Batch B084), this exercise introduced the foundational concepts of virtualization, virtual networking, IP addressing, DNS resolution, network connectivity testing, and virtual machine recovery.

The completed environment provides a foundation for subsequent cybersecurity exercises, vulnerability assessment, network reconnaissance, and ethical hacking laboratories.

## 🎯 Project Objectives

The primary objectives of this project were to:

- Install and configure Oracle VirtualBox as the virtualization platform.
- Download, import, and configure the Kali Linux virtual machine.
- Establish a private NAT Network for controlled virtual machine communication.
- Configure and verify Kali Linux network settings.
- Test network connectivity and DNS resolution.
- Create a clean virtual machine snapshot to enable recovery and restore functionality.
- Document the implementation process with screenshots for technical reference and reproducibility.

## 🛠️ Tools and Technologies

The following tools and technologies were used during the implementation:

| Tool / Technology    | Purpose                                                               |
| -------------------- | --------------------------------------------------------------------- |
| Oracle VirtualBox    | Virtualization platform for hosting the Kali Linux VM                 |
| Kali Linux           | Linux distribution designed for cybersecurity and penetration testing |
| NAT Network          | Provides private networking and controlled external network access    |
| Terminal             | Executing Linux networking commands and system checks                 |
| `ip` command         | Inspecting network interfaces and IP configurations                   |
| `ping`               | Testing network connectivity                                          |
| `nslookup`           | Verifying DNS resolution                                              |
| VirtualBox Snapshots | Creating recovery points for the virtual machine                      |

## 🏗️ Lab Architecture

The laboratory was configured using Oracle VirtualBox with Kali Linux operating as a guest virtual machine.

The virtual machine connects through a dedicated NAT Network, allowing it to communicate through the configured virtual network while providing access to external networks where permitted.

### Network Architecture

```
                INTERNET
                    |
                    |
             HOST COMPUTER
                    |
                    |
             ORACLE VIRTUALBOX
                    |
                    |
             PRIVATE NAT NETWORK
                    |
                    |
               KALI LINUX VM
                    |
                    |
          CYBERSECURITY LAB ENVIRONMENT
```

Network Configuration Concept:

- Host Machine: The physical computer running Oracle VirtualBox.
- Virtualization Layer: Oracle VirtualBox manages the virtual machine and its virtual hardware.
- NAT Network: Provides private network connectivity for connected virtual machines and outbound connectivity through network address translation.
- Kali Linux: The guest operating system used for cybersecurity practical exercises.

Note: NAT Network provides a private virtual network that can support communication between attached VMs. It is different from VirtualBox's standard NAT mode, which generally isolates individual VMs from one another.*

## ⚙️ Implementation Process

### Step 1: Installing Oracle VirtualBox

Oracle VirtualBox was downloaded and installed on the host computer.

The installation established the virtualization environment required to create, configure, and manage virtual machines.

Activities performed:

- Downloaded the VirtualBox installer.
- Installed the virtualization software.
- Verified that VirtualBox launched successfully.
- Prepared the environment for Kali Linux deployment.

Screenshot: virtualbox_page

### Step 2: Importing and Configuring Kali Linux

The Kali Linux virtual machine image was imported into Oracle VirtualBox.

After importing the virtual machine, its configuration was reviewed to ensure that the available virtual hardware resources were suitable for running the operating system.

Activities performed:

- Imported the Kali Linux virtual machine.
- Reviewed the virtual machine settings.
- Configured the available resources as required.
- Started the virtual machine.
- Verified that Kali Linux booted successfully.

Screenshot: `screenshots/02-kali-linux-import.png`

### Step 3: Creating a Private NAT Network

A dedicated NAT Network was created through VirtualBox's Network Manager.

This configuration provides a private virtual network for the laboratory environment.

Activities performed:

- Opened VirtualBox Network Manager.
- Created a new NAT Network.
- Configured the network settings.
- Enabled DHCP where required.
- Attached the Kali Linux network adapter to the newly created NAT Network.

Why NAT Network?

NAT Network allows virtual machines connected to the same network to communicate with one another while using Network Address Translation for external connectivity.

This is particularly useful when building a cybersecurity lab that may later contain multiple virtual machines for testing and analysis.

Screenshot: `screenshots/03-nat-network-configuration.png`

### Step 4: Configuring and Verifying Network Settings

After connecting Kali Linux to the NAT Network, its network interface and IP configuration were inspected.

The following command was used:

```
ip addr
```

This command displays network interfaces, assigned IP addresses, and interface status.

To inspect the routing table:

```
ip route
```

This helps identify the default gateway and available network routes.

Activities performed:

- Identified the active network interface.
- Checked the assigned IP address.
- Verified interface status.
- Inspected the default gateway and routing information.

Screenshot: `screenshots/04-kali-network-configuration.png`

### Step 5: Testing Network Connectivity

Network connectivity was tested to confirm that Kali Linux could communicate with external destinations.

The following command was executed:

```
ping -c 4 8.8.8.8
```

This sends four ICMP echo requests to Google's public DNS IP address.

Successful replies indicate IP-level connectivity to the destination.

Screenshot: `screenshots/05-network-connectivity-test.png`

### Step 6: Testing DNS Resolution

DNS resolution was tested to verify that Kali Linux could translate domain names into IP addresses.

The following command was executed:

```
nslookup google.com
```

This checks whether the configured DNS resolver can resolve the specified domain name.

Expected result: A successful response containing the resolved IP address or addresses for the domain.

Screenshot: `screenshots/06-dns-resolution-test.png`

### Step 7: Creating a Virtual Machine Snapshot

After successfully configuring and testing the environment, a clean virtual machine snapshot was created.

A snapshot preserves the virtual machine's state at a particular point in time, making it possible to restore the environment if future experiments cause configuration issues.

Activities performed:

- Opened the VirtualBox Snapshot Manager.
- Created a snapshot after completing the initial configuration.
- Assigned an appropriate snapshot name.
- Verified that the snapshot was available for recovery.

 `Kali-Linux-Clean-Lab-Setup`

Screenshot: `screenshots/07-kali-vm-snapshot.png`

## Testing and Verification Summary

The following checks were performed to validate the laboratory environment.

| Test                  | Command / Action            | Expected Outcome                 |
| --------------------- | --------------------------- | -------------------------------- |
| VM startup            | Start Kali Linux            | Successful boot                  |
| Network interface     | `ip addr`                   | Interface and IP address visible |
| Routing configuration | `ip route`                  | Routing information displayed    |
| Network connectivity  | `ping -c 4 8.8.8.8`         | Successful ICMP replies          |
| DNS resolution        | `nslookup google.com`       | Domain resolves successfully     |
| Snapshot verification | VirtualBox Snapshot Manager | Snapshot successfully created    |

## 📚 Key Technical Concepts Learned

This project provided practical exposure to several foundational cybersecurity and networking concepts.

1. Virtualization

Understanding how virtualization allows multiple operating systems to run independently on a single physical computer through virtual hardware.

2. NAT vs. NAT Network

Understanding the distinction between standard NAT and NAT Network in VirtualBox, particularly how they handle VM isolation, inter-VM communication, and external connectivity.

3. IP Addressing and Network Interfaces

Learning how Linux identifies network interfaces, assigns IP addresses, and manages network communication.

4. Default Gateway and Routing

Understanding how a default gateway enables communication with destinations outside the local network.

5. DNS Resolution

Understanding how the Domain Name System translates human-readable domain names into IP addresses.

6. Network Connectivity Troubleshooting

Using basic Linux networking commands to identify and verify connectivity issues.

7. Virtual Machine Snapshots

Learning how snapshots provide recovery points and help maintain a stable testing environment during cybersecurity experiments.

8. Technical Documentation

Understanding the importance of documenting technical configurations, implementation procedures, and verification results for future reference and troubleshooting.

## Project Repository Structure

The project documentation and screenshots are organized as follows:

```
cybersecurity-pentesting-lab/
│
├── README.md
│
├── screenshots/
│   ├── 01-virtualbox-installation.png
│   ├── 02-kali-linux-import.png
│   ├── 03-nat-network-configuration.png
│   ├── 04-kali-network-configuration.png
│   ├── 05-network-connectivity-test.png
│   ├── 06-dns-resolution-test.png
│   └── 07-kali-vm-snapshot.png
│
└── documentation/
    └── project-notes.md
```

The screenshot filenames above are suggested names. Ensure your actual uploaded files match the references.

## Future Improvements

Building on this initial setup, the next stages of the laboratory can include:

- Deploying additional virtual machines to simulate different network environments.
- Exploring Linux system administration and command-line operations.
- Practising network reconnaissance using Nmap.
- Understanding network traffic analysis with Wireshark.
- Exploring vulnerability assessment and security scanning.
- Learning basic penetration testing methodologies.
- Practising ethical hacking techniques within authorized lab environments.

##  Security and Ethical Considerations

This laboratory is intended strictly for educational purposes, authorized security testing, and controlled cybersecurity experiments.

All security assessments and penetration testing activities should be conducted only on systems and networks for which explicit authorization has been granted.

Maintaining an isolated testing environment helps reduce the risk of unintended interference with production systems and external networks.

## Acknowledgement

Special appreciation to Waqas Karim (CCIE) and the Networkwalks team for providing the training, guidance, and learning resources throughout the Cybersecurity Program (Batch B084).

This first project has provided a practical foundation for my continued development in cybersecurity, networking, and penetration testing.

## Author

Taiwo Peter Olatunji

Cybersecurity Learner | IT Support Engineer | Network Enthusiast

Program: Networkwalks Cybersecurity Program

Batch: B084

Project: Week 1 – Cybersecurity & Penetration Testing Lab Setup

---
 If you find this project useful, feel free to explore the repository and follow my learning journey as I continue developing practical cybersecurity skills.

Learn. Build. Test. Document. Repeat.

## GitHub presentation strucure


```
cybersecurity-pentesting-lab/
├── README.md
├── screenshots/
│   ├── 01-virtualbox-installation.png
│   ├── 02-kali-linux-import.png
│   ├── 03-nat-network-configuration.png
│   ├── 04-kali-network-configuration.png
│   ├── 05-network-connectivity-test.png
│   ├── 06-dns-resolution-test.png
│   └── 07-kali-vm-snapshot.png
└── documentation/
    └── project-notes.md
```
