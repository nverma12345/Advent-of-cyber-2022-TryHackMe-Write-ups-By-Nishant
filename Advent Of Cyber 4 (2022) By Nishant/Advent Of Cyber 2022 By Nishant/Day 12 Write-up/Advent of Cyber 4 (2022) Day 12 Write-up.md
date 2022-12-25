Psst! Did you find the mysterygift file? It might be malware. 🐛  
Time to dig deeper and find out what it is!?

Welcome to Day 12 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*riMKrgDgLNusfbniqaBCZA.png)

# [Day 12] Malware Analysis Forensic McBlue to the REVscue!

In today’s task, we will learn about malware and its analysis. Also, we will cover the behavior of malware and learn how to investigate it in a safe environment (e.g., sandbox) and find clues.

# Learning Objectives

-   Learn the fundamentals of analyzing malware samples without relying on automated sandbox scanners.
-   Learn and understand typical malware behavior and its importance in the incident investigation pipeline.

# Key Malware Behaviors

A prominent word in cybersecurity, **malware** is software created to harm a computer or an entire network. Threat actors develop malware to achieve specific goals, such as infiltrating networks, breaching sensitive data, or disrupting operational services.

-   **Network connections** — Malware tends to establish either external network connections or internal connections. External connections allow remote access or for downloading staged payloads from a threat actors’ infrastructure. Meanwhile, internal connections allow for lateral movement, a technique that extends access to other hosts or applications within the network.
-   **Registry key modifications** — Malware typically uses registry keys to establish persistence, a method threat actors use to maintain long-term access to a system despite disruptions discreetly. A good example is Registry Run Keys, which allows binaries to be automatically executed when a user logs in or the machine boots up.
-   **File manipulations** — Malware also tends to download (one of the common reasons to establish network connections) or create new files needed for its successful execution.

## What is a Sandbox?

A **sandbox** is a controlled test environment that mimics a legitimate end-user working environment. It gives analysts a safe environment to execute malware samples and learn their behavior. Lastly, having a ready sandbox prevents analysts from running malware samples in their workstations, which is highly dangerous and impractical for the possibility of unwanted impact.

# Static and Dynamic Analysis

**_Static analysis_** is a way of analyzing a malware sample without executing the code. This method mainly focuses on profiling the binary with its readable information, such as its properties, program flow, and strings. Given the limitation of executing it, sometimes this method needs to give more information, which is why we resort to Dynamic Analysis.

Meanwhile, **_Dynamic Analysi_s** mainly focuses on understanding the malware by executing it in a safe environment, such as a Sandbox. By doing this, you will see the malware live in action, its exact behavior, and how it infects the environment.

Check out Day 12 to learn more.

Ready to dive in? Let’s go! 🔥

1.  What is the architecture of the malware sample? (32-bit/64-bit)?

Start the attached FlareVM instance by clicking on the Start Machine button for this task. This VM will serve as your **sandbox**. However, do not expect this machine to provide an automated analysis since we will assist Forensic McBlue in conducting manual analysis.

Please navigate to the Malware Sample folder on the Desktop, right-click on mysterygift, and click on detect it easily.

![](https://miro.medium.com/max/769/1*MQ0O3cmNe1aPCokbMIuRxA.png)

As you see in the picture below, the architecture of this malware is AMD64, which is 64-bit.

![](https://miro.medium.com/max/875/1*GNATlIGYyrJETYpHNN7Byg.png)

Answer: 64-bit

2. What is the packer used in the malware sample? (format: lowercase)

![](https://miro.medium.com/max/788/1*ttyLPDh-tRZXIlpo1fWiyQ.png)

Answer: upx

3. What is the compiler used to build the malware sample? (format: lowercase)

To find out more details, we can use CAPA.  
Open cmd.exe and navigate to the Malware Sample folder using the following command:

cd "Desktop\Malware Sample"

Analyze the mysterygift by CAPA using the following command:

capa mysterygift

Since malware is packed, we must unpack it first because we can’t get further details. We can unpack the malware using UPX by the following command:

upx -d mysterygift

![](https://miro.medium.com/max/791/1*OThZhYA27JmEhLQ7SXq3ig.png)

Now rerun a scan of the file using CAPA using the following command:

capa mysterygift

![](https://miro.medium.com/max/875/1*vKHonAvKXHMOYlI0e1HGlw.png)

Answer: nim

4. How many MITRE ATT&CK techniques have been discovered attributed to the DISCOVERY tactic?

From the previous step, we can check the MITRE ATT&CK section as shown below:

![](https://miro.medium.com/max/875/1*KoFo4usgSh2yOgapqKwqBg.png)

Answer: 2

5. What is the registry key abused by the malware?

Access the ProcMon via the taskbar as shown below:

![](https://miro.medium.com/max/875/1*NSx-do7qCSu6qjWbVdxEDw.png)

Let’s set the condition Process Name — is — mysterygift.exe; add the filter and choose OK to close the prompt.

![](https://miro.medium.com/max/740/1*Nhaa9g5cTM6T2MZVgm0uVg.png)

To do this, unclick all filters and only choose **Show Registry Activity**. The results still give several results so let’s add a filter by finding all Registry Key Creations and Modifications. Remove the following Operations by right-clicking an entry from the Operation column and choosing **Exclude ‘<operation (e.g., RegQueryKey)>’** similar to the image below:

-   RegOpenKey
-   RegQueryValue
-   RegQueryKey
-   RegCloseKey

![](https://miro.medium.com/max/875/1*RKsFg97F-hTjcWgIyg-l4g.png)

Now by looking into the remaining registries, you can find the one which is used by malware (RegCreateKey), as shown below:

![](https://miro.medium.com/max/875/1*UpavghdoNN02ct9TU2a1Og.png)

Answer: HKCU\Software\Microsoft\Windows\CurrentVersion\Run

6. What is the value written on the registry key based on the previous question?

Below the previous registry, we can see a RegSetValue which indicates what value malware has written after creation.

![](https://miro.medium.com/max/875/1*E9pT4FeHU0Yd-x53ik0Vzw.png)

Double-click on the event, and then you can find the value as shown below:

![](https://miro.medium.com/max/875/1*hRcuJBmmN_a0HPXYJvJXKw.png)

Answer: C:\Users\Administrator\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\wishes.bat

7. What are the names of two files created by the malware under the C:\Users\Administrator\ directory? (format: file1,file2 in alphabetical order)

Unclick all filters and choose the second filter — **Show File System Activity**. Again, the results are still numerous so let’s add extra filters by focusing only on **File Write** events. Remove the following Operations again by right-clicking an entry from the Operation column and choosing Exclude ‘<operation (e.g., CreateFile)>’:

-   CreateFile
-   CreateFileMapping
-   QuerySecurityFile
-   QueryNameInformationFile
-   QueryBasicInformationFile
-   CloseFile
-   ReadFile

![](https://miro.medium.com/max/673/1*ZMGAGkZddBXtC1VE5UE0gg.png)

Then you will see the following screen with the following operations:

![](https://miro.medium.com/max/875/1*lboEFf60pJbcckgWn77_NQ.png)

By analyzing these events, we can see that test.jpg and wishes.bat are created under the C:\Users\Administrator\ directory, as shown below:

![](https://miro.medium.com/max/875/1*pK8Dj1VRconxVUyEpXd5dw.png)

![](https://miro.medium.com/max/875/1*TOsyAaSAUHH-IK_a9DvFvg.png)

![](https://miro.medium.com/max/875/1*hjD-cMDywWUxs8mQQTyvVg.png)

Answer: test.jpg,wishes.bat

8. What are the two domains wherein malware has initiated a network connection? (format: domain1,domain2 in alphabetical order)

Lastly, let’s confirm if the malware sample attempts to make a network connection. It may indicate that the malware communicates with external resources to download or establish remote access.  
Unclick all filters and choose the third filter — Show Network Activity. ****, Unlike the previous filters, the results are few and can be easily interpreted.

![](https://miro.medium.com/max/875/1*dL0Ysf5E54TxqNP2pVeU3A.png)

Answer: bestfestivalcompany.thm, virustotal.com

9. Going back to strings inside the malware sample, what is the complete URL used to download the file hosted in the first domain accessed by the malware?

Using the following command, we can extract the URLs in the malware:

mysterygift.exe | grep http://

![](https://miro.medium.com/max/866/1*vSo14yd1MTaF3z4cM1RMeg.png)

Answer: http://bestfestivalcompany.thm/favicon.ico

10. If you enjoyed malware analysis, try the [Intro to Malware Analysis](https://tryhackme.com/room/intromalwareanalysis) or [Dissecting PE Headers](https://tryhackme.com/room/dissectingpeheaders) rooms next!

Answer: No answer needed

# Closure

We covered exciting analysis techniques today. We learned about malware and its different behavior, how to test malware in a safe environment using a sandbox, differentiate between static and dynamic analysis.

![](https://miro.medium.com/max/875/1*hJuQ3dDv7Ax-vO5_buZBsQ.jpeg)

Great job, McBlue!  
You’ve done it! 👏

> _Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.