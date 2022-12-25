Here we are with another series of TryHackMe write-ups of Advent of Cyber 4 (2022). To check out the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*Dv9BiT9M-zSuwokAu-SYtw.png)

# [Day 1] Frameworks Someone’s coming to town!

Day 1 covers the basics of frameworks and cybersecurity frameworks used in the cybersecurity field. Today’s task will discuss common frameworks focused more on the Unified Kill Chain.

# Learning Objectives

-   Understand what the framework is.
-   Get to know about various common security frameworks
-   Understand Unified Kill Chain.

# Security Frameworks

**Security frameworks** are documented processes that define policies and procedures organizations should follow to establish and manage security controls. They are blueprints for identifying and managing the risks they may face and the weaknesses in place that may lead to an attack.

# Unified Kill Chain

The Unified Kill Chain can be described as the unification of the MITRE ATT&CK and Cyber Kill Chain frameworks. Published by Paul Pols in 2017 (and reviewed in 2022), the UKC provides a model to defend against cyber attacks from the adversary’s perspective.

The Unified Kill Chain describes 18 phases of attack based on Tactics, Techniques, and Procedures (TTPs).

# CYCLE 1: In

The main focus of this series of phases is for an attacker to gain access to a system or networked environment.

Steps:

-   **Reconnaissance**: The attacker performs research on the target using publicly available information.
-   **Weaponization**: Setting up the needed infrastructure to host the command and control center (C2) is crucial in executing attacks.
-   **Delivery**: Payloads are malicious instruments delivered to the target through numerous means, such as email phishing and supply chain attacks.
-   **Social Engineering**: The attacker will trick their target into performing untrusted and unsafe action against the payload they just delivered, often making their message appear to come from a trusted in-house source.
-   **Exploitation**: If the attacker finds an existing vulnerability, a software or hardware weakness, in the network assets, they may use this to trigger their payload.
-   **Persistence**: The attacker will leave behind a fallback presence on the network or asset to make sure they have a point of access to their target.
-   **Defense Evasion**: The attacker must remain anonymous throughout their exploits by disabling and avoiding any security defense mechanisms enabled, including deleting evidence of their presence.
-   **Command & Control**: Remember the infrastructure that the attacker prepared? A communication channel between the compromised system and the attacker’s infrastructure is established across the internet.

# CYCLE 2: Through

Under this phase, attackers will be interested in gaining more access and privileges to assets within the network.

-   **Pivoting:** Remember the system that the attacker may use for persistence? This system will become the attack launchpad for other systems in the network.
-   **Discovery**: The attacker will seek to gather as much information about the compromised system, such as available users and data. Alternatively, they may remotely discover vulnerabilities and assets within the network. This opens the way for the next phase.
-   **Privilege Escalation**: Restricted access prevents the attacker from executing their mission. Therefore, they will seek higher privileges on the compromised systems by exploiting identified vulnerabilities or misconfigurations.
-   **Execution**: With elevated privileges, malicious code may be downloaded and executed to extract sensitive information or cause further havoc on the system.
-   **Credential Access**: Part of the extracted sensitive information would include login credentials stored in the hard disk or memory. This provides the attacker with more firepower for their attacks.
-   **Lateral Movement**: Using the extracted credentials, the attacker may move around different systems or data storages within the network, for example, within a single department.

# CYCLE 3: Out

-   **Collection**: After finding the jackpot of data and information, the attacker will seek to aggregate all they need. By doing so, the assets’ confidentiality would be compromised entirely, especially when dealing with trade secrets and financial or personally identifiable information (PII) that is to be secured.
-   **Exfiltration**: The attacker must get his loot out of the network. They may use various techniques to ensure they have achieved their objectives without triggering suspicion.
-   **Impact**: When compromising the availability or integrity of an asset or information, the attacker will use all the acquired privileges to manipulate, interrupt and sabotage. Imagine the reputation, financial and social damage an organization would have to recover from.
-   **Objectives**: Attackers may have other goals to achieve that may affect the social or technical landscape that their targets operate within. Defining and understanding these objectives helps security teams familiarize themselves with adversarial attack tools and conduct risk assessments to defend their assets.

Let’s get started and solve the given puzzle.  
To start, click the View Site button in the top right corner.  
There are three puzzles for each phase of the Unified Kill Chain. You can drag and drop the puzzles and solve them using the given definitions.

![](https://miro.medium.com/max/716/1*HHr2NA_bg7gFmWBgBFodFg.png)

![](https://miro.medium.com/max/761/1*8cP4ZiuHmUUQ8Ch7D0YFYA.png)

![](https://miro.medium.com/max/723/1*0PdNdWV-aOnBHQzrpHzhQw.png)

After solving all three puzzles, we got the flag and the culprit’s name.

![](https://miro.medium.com/max/826/1*rV2bG713504Sm8-r-auMLw.png)

1.  Who is the adversary that attacked Santa’s network this year?

Answer: The Bandit Yeti!

2. What’s the flag that they left behind?

Answer: THM{IT'S A Y3T1 CHR1$TMA$}

3. Looking to learn more? Check out the rooms on [Unified Kill Chain](https://tryhackme.com/room/unifiedkillchain), [Cyber Kill Chain](https://tryhackme.com/room/cyberkillchainzmt), [MITRE](https://tryhackme.com/room/mitre), or the whole [Cyber Defence Frameworks](https://tryhackme.com/module/cyber-defence-frameworks) module!

Answer: No answer needed

# Closure

In this task, we covered the basics of security frameworks and got familiar with common cybersecurity frameworks. Also, we discussed the Unified Kill Chain and its phases.

![](https://miro.medium.com/max/875/1*aJOByPKKnpC0UoHlWRldPA.jpeg)

Great job for completing the first day!  

> Follow me on LinkedIn: [https://www.linkedin.com/in/nishantverma123/](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.