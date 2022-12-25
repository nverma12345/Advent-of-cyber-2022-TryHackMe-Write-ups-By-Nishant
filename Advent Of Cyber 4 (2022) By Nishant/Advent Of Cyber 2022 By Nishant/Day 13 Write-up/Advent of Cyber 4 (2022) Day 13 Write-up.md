Time to find out how mysterygift.exe got into our systems!

Welcome to Day 13 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*_a5_2UII3t9ms4NToJgh_Q.png)

# [Day 13] Packet Analysis Simply having a wonderful pcap time

In today’s task, we will learn about packet analysis and its importance. We will use Wireshark, a popular packet analysis tool, and find out how mysterygift.exe and other malicious files got into our systems.

# Learning Objectives

-   Learn what traffic analysis is and why it still matters.
-   Learn the fundamentals of traffic analysis.
-   Learn the essential Wireshark features used in case investigation.
-   Learn how to assess the patterns and identify anomalies on the network.
-   Learn to use additional tools to identify malicious addresses and conduct further analysis.
-   Help the Elf team investigate suspicious traffic patterns.

# Packets and Packet Analysis?

Packets are the most basic unit of the network data transferred over the network. When a message is sent from one host to another, it is transmitted in small chunks; each called a packet. Packet analysis is the process of extracting, assessing, and identifying network patterns such as connections, shares, commands, and other network activities, like logins, and system failures, from the prerecorded traffic files.

# What is Wireshark and How to Use It?

Wireshark is an industry-standard tool for network protocol analysis and is essential in any traffic and packet investigation. You can view, save and break down the network traffic with it. You can learn more about Wireshark by completing the [**Wireshark module**](https://tryhackme.com/module/wireshark).

To learn more, check out Day 13.

Let’s get started!

View the “Protocol Hierarchy” menu.

1.  What is the “Percent Packets” value of the “Hypertext Transfer Protocol”?

A quick tool demonstration for fundamental analysis is shown below. Now click on the **Start Machine** button at the top of the task to launch the **Virtual Machine**. The machine will start in a split-screen view. If the VM is not visible, use the blue Show Split View button at the top-right of the page.

Once you double-click the PCAP file, it will load up in the tool. Alternatively, you can open the tool, drag and drop the file, or use the **“File”** menu.

![](https://miro.medium.com/max/875/1*COI5WW1-LzMm7h12TKScsw.png)

Navigate to Statistics → Protocol Hierarchy as shown below:

![](https://miro.medium.com/max/875/1*ym3ViyjaVQWiQ7dWFqjjkg.png)

As shown below, the HTTP Percent Packets is 0.3 percent:

![](https://miro.medium.com/max/875/1*MKmiUBXZGou5lHbq4P5T1Q.png)

Answer: 0.3

View the “Conversations”. Navigate to the TCP section.

![](https://miro.medium.com/max/554/1*go98x0svp8SgoQ0_LDEGHw.png)

2. Which port number has received more than 1000 packets?

After opening the TCP section, you can see that Port B has received 1125 packets via port number 3389, as shown below:

![](https://miro.medium.com/max/875/1*En1pP-DcD6g5ZfZxJztqLg.png)

Answer: 3389

3. What is the service name of the used protocol that received more than 1000 packets?

By googling the port number, we can find that this port belongs to the RDP service:

![](https://miro.medium.com/max/866/1*LdJHiL3F6M1cK283zyyZsQ.png)

Answer: rdp

Filter the DNS packets.

4. What are the domain names?Enter the domains in alphabetical order and defanged format. (format: domain[.]zzz,domain[.]zzz)

Type DNS in the filter bar and press Enter, and you will see the following screen:

![](https://miro.medium.com/max/875/1*sNmQ546k6NF1yX1bAgaBgQ.png)

Navigate to [CyberChef.org](http://cyberchef.org/) and insert these domains in the input section and add Defang URL ingredient from the left side as shown below:

![](https://miro.medium.com/max/875/1*SxqonGplVTyIa63oEVKmvA.png)

bestfestivalcompany[.]thm,cdn[.]bandityeti[.]thm

Filter the HTTP packets.

5. What are the names of the requested files?Enter the names in alphabetical order and in defanged format. (format: file[.]xyz,file[.]xyz)

Enter HTTP in the filter bar and click Enter as shown below:

![](https://miro.medium.com/max/875/1*Z0o3aBETInKyedrZfplMUQ.png)

Enter the marked file names and paste them in the input section of the CyberCheft to defang it as shown in the previous section:

![](https://miro.medium.com/max/875/1*4uSO9azLKPd1-HgXL6w1bQ.png)

Answer: favicon[.]ico,mysterygift[.]exe

6. Which IP address downloaded the executable file?Enter your answer in defanged format.

Get the IP address of the source which downloaded mysterygift.exe.

![](https://miro.medium.com/max/875/1*VgPNKQQO2whmrrrkcVG5Iw.png)

Now defang the IP address as shown below:

![](https://miro.medium.com/max/875/1*cxmeR4AgfPO1YXCg3rnJCQ.png)

Answer: 10[.]10[.]29[.]186

7. Which domain address hosts the malicious file? Enter your answer in defanged format.

Double click on this packet and navigate to Hyper Text Transfer Protocol → GET and then check for the Host as shown below:

![](https://miro.medium.com/max/875/1*jWijNGb8XRpfLAR9TMYB5A.png)

Defang the URL as shown in the previous steps:

Answer: cdn[.]bandityeti[.]thm

8. What is the “user-agent” value used to download the non-executable file?

Open the packet which downloaded the favicon.ico file.

![](https://miro.medium.com/max/875/1*GwFwOkaySFLIBDOE0iCNNA.png)

Then check for the User-Agent as shown below:

![](https://miro.medium.com/max/875/1*LrVMZQsBDN2NBhNSk4nNxw.png)

Answer: Nim httpclient/1.6.8

Export objects from the PCAP file.Calculate the file hashes.

9. What is the sha256 hash value of the executable file?

To export the shared files, navigate to File → Export Objects → HTTP as shown below:

![](https://miro.medium.com/max/626/1*VNJL0Usd-HekzM8BotDZBA.png)

Click on Save all to extract and save the files as shown below:

![](https://miro.medium.com/max/875/1*FQHgtf1GUD97AwklJqZMkg.png)

Navigate to the directory in which you saved the files using the cd command  
Then calculate the SHA256 sum using the following command:

sha256sum mysterygift.exe

![](https://miro.medium.com/max/875/1*AKesu5nHjr0bjqTVrWw58A.png)

Answer: 0ce160a54d10f8e81448d0360af5c2948ff6a4dbb493fe4be756fc3e2c3f900f

Search the hash value of the executable file on Virustotal. Navigate to the “Behavior” section. There are multiple IP addresses associated with this file.

10. What are the connected IP addresses? Enter the IP addressed defanged and in numerical order. (format: IPADDR,IPADDR)

Open [Virustotal.com](http://virustotal.com/) → Search and then insert the hash value, and press Enter as shown below:

![](https://miro.medium.com/max/875/1*uEs1SaPuguzEBglOz_mk4A.png)

Navigate to the Behavior section and search for the IP addresses as shown below:

![](https://miro.medium.com/max/716/1*1akT09ktpLkfl1fD8wY3Hg.png)

Defang these IP addresses using CyberChef.

Answer: 20[.]99[.]133[.]109,20[.]99[.]184[.]37,23[.]216[.]147[.]64,23[.]216[.]147[.]76

11. If you liked working with Wireshark, we have a comprehensive module on this helpful tool [here](https://tryhackme.com/module/wireshark). If you want to dive deeper, the [Network Security and Traffic Analysis](https://tryhackme.com/module/network-security-and-traffic-analysis) module is waiting for you!

Answer: No answer needed

# Closure

We learned what packet/traffic analysis is and why it is crucial in an investigation. We also learned how to use Wireshark and its different functionalities and features to analyze packets and find clues for our research.

![](https://miro.medium.com/max/593/1*5N8t4llqPOqRNPZRPSmIbQ.jpeg)

Way to go! 🥳

> _Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.