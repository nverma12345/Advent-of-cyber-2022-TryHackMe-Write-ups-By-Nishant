Time to bake in CyberChef!

Welcome to Day 7 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).
![](https://miro.medium.com/max/875/1*Ums6ZXaqCdBMXPRkwph0Tg.png)

# [Day 7] CyberChef Maldocs roasting on an open fire

Today’s task will discuss CyberChef and how to use it in investigating and analyzing documents. We will practice analyzing and decoding the malicious document we discovered in the previous task.

# Learning Objectives

-   What is CyberChef
-   What are the capabilities of CyberChef?
-   How to leverage CyberChef to analyze a malicious document
-   How to deobfuscate, filter and parse the data

# CyberChef Overview

CyberChef is a web-based application to slice, dice, encode, decode, parse and analyze data or files.

-   Add the text or file in panel 1.
-   Panel 2 contains various functions, also known as recipes, that we use to encode, decode, parse, search or filter the data.
-   Drag the functions or recipes from Panel 2 into Panel 1 to create a recipe.
-   The output from the recipes is shown in panel 4.
-   Click on bake to run the functions added in Panel 3 in order. We can select AutoBake to run the recipes as they are added automatically.

**Note:** Since the walkthrough of decoding the malicious file is given in the TryHackMe, I will skip that part, and you can refer to Day 7.

Let’s get started!

1.  What is the version of CyberChef found in the attached VM?

You will need to deploy the machine attached to this task for today’s task by pressing the green “**Start Machine**” button at the top right. The machine should launch in a split-screen view. If it does not, you will need to press the blue “Show Split View” button near the top-right of this page.

Open the Firefox browser and open the CyberChef.

![](https://miro.medium.com/max/850/1*ayX3Ny5xs43YS-t_ANqzaA.png)

You can check the CyberChef version on the top left side of the website.

![](https://miro.medium.com/max/875/1*tsNDBBgtPAnl1rGKzGUMpw.png)

Answer: 9.49.0

2. How many recipes were used to extract URLs from the malicious doc?

As shown in the walkthrough on Day 7, 10 recipes were used.

Answer: 10

3. We found a URL that was downloading a suspicious file; what is the name of that malware?

From the output of the previous step, we’ve found a couple of links. The name of the malware is mentioned there.

![](https://miro.medium.com/max/875/1*TBgzCfRmufBm4aCwkmk1cw.png)

Answer: mysterygift.exe

4. What is the last defanged URL of the bandityeti domain found in the last step?

![](https://miro.medium.com/max/854/1*6EhG3NR2KXciIxlwnBDa9A.png)

Answer: hxxps[://]cdn[.]bandityeti[.]THM/files/index/

5. What is the ticket found in one of the domains? (Format: Domain/<GOLDEN_FLAG>)

![](https://miro.medium.com/max/854/1*157Q4a6FXWvTv6s_o1Qrvg.png)

Answer: THM_MYSTERY_FLAG

6. If you liked the investigation today, you might also enjoy the [Security Information and Event Management](https://tryhackme.com/module/security-information-event-management) module!

Answer: No answer needed

# Closure

Today’s task taught us how to investigate and analyze a malicious document. We also learned how to decode an encoded document using CyberChef and extract useful information.

![](https://miro.medium.com/max/593/1*6PlGmMbVYRofimhcTC4vnw.jpeg)

You are extraordinary!  
You’ve come so far, and keep up the hard work!  

> _Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.