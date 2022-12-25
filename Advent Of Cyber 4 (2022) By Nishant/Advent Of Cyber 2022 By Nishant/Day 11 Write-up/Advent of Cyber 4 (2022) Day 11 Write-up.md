Are you a curious person? And is Sherlock Holmes your inspiration? 💡  
If yes, you came to the right place. Today’s task will be fun, with full investigation and analysis.

Welcome to Day 11 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*xcH4HjYddflwHhvVZWVoEw.png)

# [Day 11] Memory Forensics Not all gifts are nice

Today’s task will cover the basics of memory forensics and analysis. We will discuss using evidence and tracks in volatile memory for our investigation to find clues if anything is kept hidden.

# Learning Objectives

-   Understand Memory Forensics
-   Understand why memory forensics is important
-   What is volatility, and how to use it to analyze an image

# What is Memory Forensics?

Memory forensics is the analysis of the volatile memory that is in use when a computer is powered on. Computers use dedicated storage devices called Random Access Memory (RAM) to remember what is being performed on the computer at the time. RAM is speedy and is the preferred method of storing and accessing data. However, it is limited compared to storage devices such as hard drives. This type of data is volatile because it will be deleted when the computer is powered off. RAM stores data such as your clipboard or unsaved files.

# Introducing Volatility

Volatility is an open-source memory forensics toolkit written in Python. Volatility allows us to analyze memory dumps taken from Windows, Linux, and Mac OS devices and is a top-rated tool in memory forensics. For example, volatility will enable us to:

-   List all processes that were running on the device at the time of the capture
-   List active and closed network connections
-   Use Yara rules to search for indicators of malware
-   Retrieve hashed passwords, clipboard contents, and contents of the command prompt
-   And much, much more!

Once volatility and its requirements (i.e., Python) are installed, volatility can be run using python3 vol.py. The command below displays volatility’s help menu:

python3 vol.py -h

To learn more, check out Day 11.

Let’s get started!

1.  What is the Windows version number that the memory image captured?

You must deploy the machine attached to this task to access the memory dump by pressing the green “Start Machine” button at the top right. The machine should launch in a split-screen view. If it does not, you must press the blue “Show Split Screen” button near the top-right of this page.  
First, navigate to the volatility3 folder as shown below:

![](https://miro.medium.com/max/843/1*-AhFotL3SHsn6cEAZZZtug.png)

Using the following command:

python3 vol.py -f workstation.vmem windows.info

![](https://miro.medium.com/max/835/1*vqtVwOjDfw0yKcyX_15FRQ.png)

Answer: 10

2. What is the name of the binary/gift that secret Santa left?

To find a specific process, use the following command:

python3 vol.py -f workstation.vmem windows.pslist

![](https://miro.medium.com/max/855/1*5i1m7Jvxe8VkGWgYuFJKSA.png)

Answer: mysterygift.ex

3. What is the Process ID (PID) of this binary?

To find the process ID (PID), use the following command:

python3 vol.py -f workstation.vmem windows.psscan | grep "mysterygift.ex"

![](https://miro.medium.com/max/825/1*c0wsetGHoYH2A_riq_pF8Q.png)

Answer: 2040

4. Dump the contents of this binary. How many files are dumped?

Using the following command:

python3 vol.py -f workstation.vmem windows.dumpfiles — pid 2040

![](https://miro.medium.com/max/875/1*Yy_-WhqW8fX0OZgirjTJNQ.png)

Answer: 16

# Closure

Today’s task discussed the basics of memory and why it is essential in forensics and analysis. We also covered a popular tool called volatility to analyze and investigate an image.

![](https://miro.medium.com/max/593/1*pZQNBefCJLpi2Xy-VeBL-w.jpeg)

You Rock! 🔥  
Keep it up, and enjoy the upcoming challenges.

> _Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.