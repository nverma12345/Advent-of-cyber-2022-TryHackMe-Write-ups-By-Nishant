Are they not allowing you? Then let’s brute-force them!

Welcome to Day 5 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*Cj6vxCRy3TyPcAxlhoTpeg.png)

# [Day 5] Brute-Forcing He knows when you’re awake

Today’s task will discuss a few standard services and authentication. We will also learn to hack an authentication service using Hydra and VNC clients.

# Learning Objectives

-   Learn about common remote access services.
-   Recognize a listening VNC port in a port scan.
-   Use a tool to find the VNC server’s password.
-   Connect to the VNC server using a VNC client.

# Remote Access Services

**SSH** stands for **Secure Shell**. Experts initially used it in Unix-like systems for remote login. It provides the user with a command-line interface (CLI) that the user can use to execute commands.

**RDP** stands for **Remote Desktop Protocol**; it is also known as Remote Desktop Connection (RDC) or simply Remote Desktop (RD). It provides a graphical user interface (GUI) to access an MS Windows system. When using Remote Desktop, the user can see their desktop and use the keyboard and mouse as if sitting at the computer.

**VNC** stands for **Virtual Network Computing**. It provides access to a graphical interface that allows the user to view the desktop and (optionally) control the mouse and keyboard. VNC is available for any system with a graphical interface, including MS Windows, Linux, macOS, Android, and Raspberry Pi.

# Hacking an Authentication Service

To start the AttackBox and the attached Virtual Machine (VM), click on the “Start the AttackBox” button and click on the “Start Machine” button. Please give it a couple of minutes so that you can follow along.

On the AttackBox, we open a terminal and use Nmap to scan the target machine of IP address MACHINE_IP. The terminal window below shows that we have two listening services, SSH and VNC. Let’s see if we can discover the passwords used for these two services.

We want an automated way to try the common passwords or the entries from a word list; here comes [THC Hydra](https://github.com/vanhauser-thc/thc-hydra). Hydra supports many protocols, including SSH, VNC, FTP, POP3, IMAP, SMTP, and all methods related to HTTP. You can learn more about THC Hydra by joining the [Hydra](https://tryhackme.com/room/hydra) room. The general command-line syntax is the following:

hydra -l username -P wordlist.txt server service where we specify the following options:

-   l username: l should precede the username, i.e., the login name of the target. You should omit this option if the service does not use a username.
-   P wordlist.txt: P precedes the wordlist.txt file, which contains the passwords you want to try with the provided username.
-   server is the hostname or IP address of the target server.
-   service indicates the service you are trying to launch the dictionary attack.

Consider the following concrete examples:

-   hydra -l mark -P /usr/share/wordlists/rockyou.txt MACHINE_IP ssh will use the mark as the username as it iterates over the provided passwords against the SSH server.
-   hydra -l mark -P /usr/share/wordlists/rockyou.txt ssh://MACHINE_IP is identical to the previous example. MACHINE_IP ssh is the same as ssh://MACHINE_IP.

You can replace ssh with another protocol name, such as rdp, vnc, ftp, pop3, or any other protocol supported by Hydra.

There are some extra optional arguments that you can add:

-   V or vV, for verbose, makes Hydra show the username and password combinations being tried. This verbosity is very convenient to see the progress, especially if you still need to be more confident in your command-line syntax.
-   d, for debugging, provides more detailed information about what’s happening. The debugging output can save you much frustration; for instance, if Hydra tries to connect to a closed port and timing out, d will reveal this immediately.

To learn more, you can refer to Day 5.

Let’s get started!

1.  Use Hydra to find the VNC password of the target with IP address 10.10.91.66. What is the password?

To start the AttackBox and the attached Virtual Machine (VM), click on the “Start the AttackBox” button and click on the “Start Machine” button. Please give it a couple of minutes so that you can follow along.

Scan the machine using Nmap as shown below:

nmap -sS 10.10.91.66

The terminal window below shows that we have two listening services, SSH and VNC.

![](https://miro.medium.com/max/849/1*s4OBHYuHN15-RzlOVH_kzA.png)

Since the question it is given to find the VNC password using Hydra, you can use the following command:

hydra -P /usr/share/wordlists/rockyou.txt 10.10.91.66 vnc  
  
OR   
  
hydra -P /usr/share/wordlists/rockyou.txt vnc://10.10.91.66 -V -f -t 4

Note: Since this host doesn’t have any username for VNC service, we omit to add -l username.

![](https://miro.medium.com/max/875/1*yNZUpxYco2dsinQBMs6mHg.png)

We can use the following Nmap command:

nmap —script vnc-brute -p 5900 10.10.91.66

Answer: 1q2w3e4r

2. Using a VNC client on the AttackBox, connect to the target of IP address 10.10.91.66. What is the flag written on the target’s screen?

For this challenge, we can use Remmina as a VNC client.

![](https://miro.medium.com/max/540/1*34nRmGpMJ59acZVhVxILtg.png)

Click on Cancel in case any window appears for entering the login password.

![](https://miro.medium.com/max/716/1*ffOxU03KjliEPwQL75_E9A.png)

Choose VNC as service and enter your machine IP and click Enter as shown below:

![](https://miro.medium.com/max/743/1*5eNa5dRz0XkU9me9YA-93Q.png)

Enter the password that we found in the previous step and click on OK, as shown below:

![](https://miro.medium.com/max/800/1*x18zYSXKnHjmwyA8B8qc-g.png)

Voila! You found the flag.

![](https://miro.medium.com/max/800/1*6elexuP2lAu9-2DF_eeLmg.png)

Answer: THM{I_SEE_YOUR_SCREEN}

3. If you liked the topics presented in this task, check out these rooms next: [Protocols and Servers 2](https://tryhackme.com/room/protocolsandservers2), [Hydra](https://tryhackme.com/room/hydra), [Password Attacks](https://tryhackme.com/room/passwordattacks), [John the Ripper](https://tryhackme.com/room/johntheripper0).

Answer: No answer needed

# Closure

Today’s task covered common remote access services, authentication, password-attacking types, and how to hack an authentication using Hydra by brute-forcing the user’s password in an SSH or VNC service.

![](https://miro.medium.com/max/875/1*_DChZcYD4g8lYpivtltlWg.jpeg)

Great work! Keep it up, and don’t give up!  

>_Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.