Don’t get spooked by spooky mails! 😱

Welcome to Day 6 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*_0tu8r3QXM1Y0BtAhY-Yrw.png)

# [Day 6] Email Analysis It’s beginning to look a lot like phishing

Today’s task discusses email analysis. We will discuss how to identify spooky suspicious emails and how to extract data from them. Also, we are going to perform the further investigation using different tools.

# Learning Objectives

-   Learn what email analysis is and why it still matters.
-   Learn the email header sections.
-   Learn the essential questions to ask in email analysis.
-   Learn how to use email header sections to evaluate an email.
-   Learn to use additional tools to discover email attachments and conduct further investigation.
-   Help the Elf team investigate the suspicious email received.

# What is Email Analysis?

Email analysis extracts the email header information to expose the email file details. The email header contains the technical details of the email, like sender, recipient, path, return address and attachments. Usually, these details are enough to determine if there is something suspicious/abnormal in the email and decide on further actions on the email, like filtering/quarantining or delivering. This process can be done manually and with the help of tools.

A common security issue regarding emails is Phishing attacks.

**Phishing:** Phishing is a sub-section of social engineering delivered through email to trick someone into either revealing personal information and credentials or executing malicious code on their computer.

# Important Email Header Fields for Quick Analysis

![](https://miro.medium.com/max/835/1*rDmcOlSJ8S_r8UqPG1syqQ.png)

## emlAnalyzer

![](https://miro.medium.com/max/609/1*GTPL49aLPDgUh3opO_b6WQ.png)

Now use the given sample and execute the given command.

emlAnalyzer -i Urgent\:.eml --header --html -u --text --extract-all

## Tools for further investigations

![](https://miro.medium.com/max/718/1*Cz4WYlcao1LuDQF4mPxhSQ.png)

**IMPORTANT NOTES:**

-   **Given the email, the sample contains a malicious attachment.**
-   **Never directly interact with unknown email attachments outside of an isolated environment.**

To learn more, check out the Day 6.

Let’s get started!

1.  What is the email address of the sender?

Using the following command:

emlAnalyzer -i ./Desktop/Urgent:.eml --header --html -u --text --extract-all

![](https://miro.medium.com/max/854/1*g0X9PlZOI7TjRPn9ruueEg.png)

Answer: chief.elf@santaclaus.thm

2. What is the return address?

From the previous output, you can find the Return address.

![](https://miro.medium.com/max/794/1*QWx-RvV-djW_RhRUkb_1Hw.png)

Answer: murphy.evident@bandityeti.thm 

3. On whose behalf was the email sent?

From the previous output, you can check the From field value.

![](https://miro.medium.com/max/875/1*vtXotexq-VlEPD9OsTqNOw.png)

Answer: chief elf

4. What is the X-spam score?

![](https://miro.medium.com/max/846/1*hLTpOsjw9hjp7oFsAmEzJg.png)

Answer: 3

5. What is hidden in the value of the Message-ID field?

Since Message ID cannot be in Base64 format, we must decode it and find the hidden value.

![](https://miro.medium.com/max/835/1*fOSOE17Cso6mwBjqlJThmw.png)

QW9DMjAyMl9FbWFpbF9BbmFseXNpcw==

To decode, we can use this website: [https://www.base64decode.org/](https://www.base64decode.org/)

![](https://miro.medium.com/max/875/1*CEqhTMKkT5xurLORPc1y9g.png)

Answer: AoC2022_Email_Analysis

6. Visit the email reputation check website provided in the task. What is the reputation result of the sender’s email address?

We can check the reputation of the sender’s email address using the following website:

[

## Simple Email Reputation

### Illuminate the reputation behind an email address.

emailrep.io

](https://emailrep.io/)

![](https://miro.medium.com/max/875/1*ySXoMvNQ648qYezKc8Xc_Q.png)

Answer: RISKY

7. Check the attachments. What is the filename of the attachment?

From the earlier output, we can check for the extracted attachments.

![](https://miro.medium.com/max/875/1*Mh1ueU_YjqtIhLz5HVKOsg.png)

Answer: Division_of_labour-Load_share_plan.doc

8. What is the hash value of the attachment?

The attachment file is stored in the eml_attachments folder in the current directory. We can confirm this using the ls command and navigate to this folder, and you can use the cd command.

![](https://miro.medium.com/max/875/1*kKltGHpLOHbbvQgCJO9CjQ.png)

Using the following command:

sha256sum Division_of_labour-Load_share_plan.doc

![](https://miro.medium.com/max/875/1*WQFdbmtIXdI1ltJPbVyPfw.png)

Answer: 0827bb9a2e7c0628b82256759f0f888ca1abd6a2d903acdb8e44aca6a1a03467

9. Visit the Virus Total website and use the hash value to search. Navigate to the behaviour section. What is the second tactic marked in the MITRE ATT&CK section?

Open [the VirusTotal website](https://www.virustotal.com/gui/home/search), paste the hash value we found, and click on search.

![](https://miro.medium.com/max/875/1*dWhcxl3cZ7V-zgbbDYdV-A.png)

Navigate to the Behavior section.

![](https://miro.medium.com/max/875/1*TkucaZHeeUvY_aELCCtt8A.png)

Scroll down, and you can see that the second tactic marked in the MITRE ATT&CK section is Defense Evasion.

![](https://miro.medium.com/max/875/1*aRP-GbIJ8s6wT_kbQVO1tQ.png)

Answer: Defense Evasion

10. Visit the InQuest website and use the hash value to search. What is the subcategory of the file?

Open [the InQuest website](https://labs.inquest.net/) and navigate to INDICATOR LOOKUP.

![](https://miro.medium.com/max/875/1*NgkSmCZhIh2Tl7fV-3rqPg.png)

Paste the hash value and click on the Lookup button.

![](https://miro.medium.com/max/708/1*vHEyUvB3fKnpZBVjNS93xA.png)

Click on the SHA256 hash value for further investigation.

![](https://miro.medium.com/max/801/1*LPq0YxJ8_iqnbE6UEJElVw.png)

Since the question asked for a subcategory, you only have to look for that.

![](https://miro.medium.com/max/875/1*MaBPv2IH91Q_1mk5iF8phg.png)

Answer: macro_hunter

11. If you want to learn more about phishing and analysing emails, check out the [Phishing](https://tryhackme.com/module/phishing) module!

Answer: No answer needed

# Closure

Today’s task covered components of email and how to analyze an email. We discussed using various tools and websites to find malicious attachments and emails.

![](https://miro.medium.com/max/624/1*ON4RLgOXGOBpSTH8gXBH_A.jpeg)

Way to go!  
Keep up the hard work, and don’t give up!  

> _Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.