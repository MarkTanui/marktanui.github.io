---
title: "AoC#4"
date: 2022-12-02
draft: false
toc: false
images:
tags: ["AoC 2022", "Scanning", "NMAP"]
---

## [Day 4] 
```SCANNING``` Scanning through the snow.

*On the fourth day of christmas: I find the attacker's initial access*

Task 4: Help McRed scan the network and find the reason for the website compromise

### Scanning.

The process of identifying and assessing the computer systems and devices, ports and services.
Scanning reveals parts of the attack surface for attackers and allows launching targeted attacks to exploit the system.

#### Scanning Types.
* Passive Scanning - Doesn't interact directly with the system.
Passive scanning is also less thorough and may not be able to identify all the devices and vulnerabilities on a network.
* Active Scanning - Interacts directly with the system/network.
Generates additional traffic on the network and is more likely to be detected by security systems.

### Scanning Techniques.

1. Networking scanning. - enumerates hosts/devices available in a network.
2. Port Scanning - Examining ports ('window/door' to a network service) to find possible attack vectors.

Port scanning results fall into the following three categories:
* Closed Ports: The host is not listening to the specific port.
* Open Ports: The host actively accepts a connection on the specific port.
* Filtered Ports: This indicates that the port is open; however, the host is not accepting connections or accepting connections as per certain criteria like specific source IP address.

3. Vulnerability Scanning.
Automated search for weaknesses to use in attacking a system.

Tools used include: Nikto, Nessus and Acunetix.

### Scanning Tools.
#### Network Mapper(NMAP)

Nmap is a popular tool used to carry out port scanning, discover network protocols, identify running services, and detect operating systems on live hosts.

Usage:
* Ping Scan: Allows scanning the live hosts in the network without going deeper and checking for ports services etc. Usage: `nmap -sn MACHINE_IP.`
* Operating System Scan: Allows scanning of the type of OS running on a live host. Usage: `nmap -O MACHINE_IP.`
* Detecting Services: Get a list of running services on a live host. Usage: `nmap -sV MACHINE_IP`

###### End of AoC#4