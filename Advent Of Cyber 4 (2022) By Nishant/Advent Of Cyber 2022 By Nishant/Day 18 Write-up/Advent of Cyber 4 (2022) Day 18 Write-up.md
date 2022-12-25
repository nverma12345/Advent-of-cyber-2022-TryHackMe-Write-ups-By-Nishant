Welcome to Day 18 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*2Yj5_aC8sgKGR-ul1f7mcg.png)

# [Day 18] Sigma Lumberjack Lenny Learns New Rules

In today’s task, we will discuss Sigma rules, their usage, and their importance in investigation and threat detection.

# Learning Objectives

-   Learn What is threat detection
-   Understand what is Sigma rules
-   Why are Sigma rules used
-   How to implement Sigma rules in threat detection

# Threat Detection

Cyber threats and criminals have advanced tactics to steal info and cause havoc. Security teams can prepare defenses and identify threats. Most blue-team activities require proactive approaches to log, malware, and network traffic analysis — known as threat detection.

# Chopping Logs with Sigma Rules

Sigma is an open-source generic signature language developed by Florian Roth & Thomas Patzke to describe log events in a structured format. The format involves using a markup language called [YAML](http://yaml.org/), a designed syntax that allows for quick sharing of detection methods by security analysts. The common factors to note about YAML files include the following:

-   YAML is case-sensitive.
-   Files should have the .yml extension.
-   Spaces are used for indentation and not tabs.
-   Comments are attributed using the # character.
-   Key-value pairs are denoted using the colon: character.
-   Array elements are represented using the dash -character.

Sigma makes it easy to perform content matching based on collected logs to raise threat alerts for analysts to investigate. Log files are usually collected and stored in a database or a Security Information and Event Management (SIEM) solution for further analysis. Sigma is vendor-agnostic; therefore, you can convert the rules to a format that fits the target SIEM.

Sigma was developed to satisfy the following scenarios:

-   To make detection methods and signatures shareable alongside IOCs and Yara rules.
-   To write SIEM searches that avoid vendor lock-in.
-   To share signatures with threat intelligence communities.
-   To write custom detection rules for malicious behavior based on specific conditions.

To learn more, check out Day 18.

Let’s get started!

Before we proceed to the next section, deploy the attached machine and give it up to 5 minutes to launch its services. Once launched, use the AttackBox or VPN to access the link [http://MACHINE_IP](http://machine_ip/) to our Sigma application, which constitutes the following features:

1.  What is the Challenge #1 flag?

Open the given link in your VM browser or Attack Box and then click on Create Rule under Challenge #1 as shown below:

![](https://miro.medium.com/max/605/1*4ah2-omPQFbNC_nHG4W0pg.png)

Then apply the following changes in the editor, and then click on Run:

title: Local Account Creation Detection  
id: 1  
status: experimental  
description: Detects the creation of a local user account on a computer.  
product: windows  
service: security  
EventID: 4720  
level:  low

![](https://miro.medium.com/max/875/1*mOLToayP-ZYP8V57eFLeSw.png)

Answer: THM{n0t_just_your_u$ser}

2. From the Challenge 1 log, what user account was created?

Click on view log to see the details of the log as shown below:

![](https://miro.medium.com/max/709/1*xH0oh191CZpYQAyTyu71JQ.png)

Then search for the Username created in this log:

![](https://miro.medium.com/max/875/1*3uzsHVPl7O8CWYo2nlVLtQ.png)

Answer: BanditYetiMini

3. What is the Challenge #2 flag?

Click on create a rule to next Challenge 2, as shown below:

![](https://miro.medium.com/max/650/1*ApZVbdDr9e-VH1dao14_iw.png)

Then apply the following changes and click on Run:

product: windows  
  service: sysmon  
  category: process_creation  
detection:  
  selection:  
    EventID: 1   
    Image|endswith:  
    - reg.exe  
    CommandLine|contains|all:  
    - reg  
    - quer  
    - /v  
    - svcVersion

![](https://miro.medium.com/max/875/1*1jivGwTx__FWD4O36YhYLQ.png)

Answer: THM{wh@t_1s_Runn1ng_H3r3}

4. What was the User’s path in the Challenge #2 log file?

Click on the View Log and search for the User’s path:

![](https://miro.medium.com/max/609/1*akm6E17nCrFX2uu_6YgSJA.png)

Answer: SIGMA_AOC2022\Bandit Yeti

5. What is the Challenge #3 flag?

Click on Create rule next to Challenge #3:

![](https://miro.medium.com/max/654/1*OdTOxh02vi9TlVigvEoUkA.png)

Apply the following changes and click on Run:

product: windows  
  service: sysmon  
  category: process_creation  
detection:  
  selection:  
    EventID: 1  
    Image|endswith:  
    - schtasks.exe  
    CommandLine|contains|all:  
    - schtasks  
    - cmd.exe  
    - /create

![](https://miro.medium.com/max/875/1*C2c-z7kOt3nAQHbJKjdZcA.png)

Answer: THM{sch3dule_0npo1nt_101}

6. What was the MD5 hash associated with Challenge #3 logs?

Go to View log and search for MD5 hash:

![](https://miro.medium.com/max/875/1*hbLIaZ2JCV0xUXz9hDDzhw.png)

Decrypt the hash using the following command:

ccat -d 2F6CE97FAF2D5EEA919E4393BDD416A7,SHA256=4B679CCC4E0E84A9EDDC24362EA4A86835597A90D94A1AE0EA905D7BCD9F771C,IMPHASH=0BF09EE8918142EE8D325D5955AA1CD9

![](https://miro.medium.com/max/875/1*5JUY492ajhhp5T-ylHfPxw.png)

Answer: 2F6CE97FAF2D5EEA919E4393BDD416A7

7. Did you like learning about detection? Check out the [Yara](https://tryhackme.com/room/yara) room to learn more!

Answer: No answer needed

# Closure

Today’s task taught us about Sigma rules and their importance in threat detection. We learned how to implement these rules to detect and identify threats with different levels of severity.

![](https://miro.medium.com/max/500/0*Tmo59nsBysAurfLw)

Well done!  
Keep it up and do your best in the upcoming tasks.

> Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.