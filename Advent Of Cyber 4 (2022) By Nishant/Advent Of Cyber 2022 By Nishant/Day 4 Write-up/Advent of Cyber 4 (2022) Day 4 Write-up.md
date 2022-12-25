Did you finish your OSINT? Now time to do some scanning.

Welcome to Day 4 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*YMTfEttVH_y8nZrgDYj60w.png)

# [Day 4] Scanning Scanning through the snow

Today’s task discusses scanning and tools to perform scanning on target systems and gather the information that can be useful in exploiting and attacking.

# **Learning Objectives**

-   What is Scanning?
-   Scanning types
-   Scanning techniques
-   Scanning tools

# What is Scanning

Scanning is a set of procedures for identifying live hosts, ports, and services, discovering the operating system of the target system, and identifying vulnerabilities and threats in the network. These scans are typically automated and give an insight into what could be exploited. Scanning reveals parts of the attack surface for attackers and allows launching targeted attacks to exploit the system.

# Scanning Tools

## Network Mapper (Nmap)

Nmap is a popular tool used to scan ports, discover network protocols, identify running services, and detect operating systems on live hosts.

A quick summary of important Nmap options is listed below:

**TCP SYN Scan**: Get the list of live hosts and associated ports on the hosts without completing the TCP three-way handshake and making the scan a little stealthier. Usage: nmap -sS MACHINE_IP.

**Ping Scan**: Allows scanning the live hosts in the network without going deeper and checking for ports services etc. Usage: nmap -sn MACHINE_IP

**Operating System Scan**: Allows scanning of the type of OS running on a live host. Usage: nmap -O MACHINE_IP.

**Detecting Services**: Get a list of running services on a live host. Usage: nmap -sV MACHINE_IP

## Nikto

Nikto is open-source software that allows scanning websites for vulnerabilities. It enables looking for subdomains, outdated servers, debug messages, etc., on a website. You can access it on the AttackBox by typing nikto -host MACHINE_IP.

Let’s connect to the Samba service using the credentials we found through the source code (OSINT task). Type the following command smb://MACHINE_IP in the address bar and use the following username and password:

-   Username: ubuntu
-   Password: S@nta2022

If you want to learn more, refer to the Day 4.

Let’s get started!

1.  What is the name of the HTTP server running on the remote host?

Using the following command:

nmap -sV Machine_IP

![](https://miro.medium.com/max/853/1*47TMN-lcjWJ0rsGxZ89wdA.png)

Answer: Apache

2. What is the name of the service running on port 22 on the QA server?

From the previous output, we know that ssh is running on port 22.

![](https://miro.medium.com/max/840/1*RkkQ-zf_lz4Idd84Ot2KJw.png)

Answer: ssh

3. What flag can you find after successfully accessing the Samba service?

Let’s connect to the Samba service using the credentials we found through the source code (OSINT task). Type the following command `smb://10.10.150.171` in the address bar and use the following username and password:

-   Username: ubuntu
-   Password: S@nta2022

![](https://miro.medium.com/max/848/1*e06yGJHmW0DZE869Ttc3Wg.png)

Open the flag.txt file inside the admin folder and then submit the flag.

![](https://miro.medium.com/max/875/1*gJxR_EskDbcbYUdjzGkhrg.png)

Answer: {THM_SANTA_SMB_SERVER}

4. What is the password for the username santahr?

Open the userlist.txt file and search for username santahr.

![](https://miro.medium.com/max/875/1*UZL_AJZonGw9gixA02-Lcg.png)

Answer: santa25

5. If you want to learn more scanning techniques, we have a module dedicated to [Nmap](https://tryhackme.com/module/nmap)!

Answer: No answer needed

# Closure

Today’s task discussed scanning and its different types. We also learned about various scanning tools for finding open ports and vulnerabilities.

![](https://miro.medium.com/max/593/1*L_U9ljZprfMfI75UzjQbAQ.jpeg)

Voila!  
Great job for completing Day 4.

> _Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.