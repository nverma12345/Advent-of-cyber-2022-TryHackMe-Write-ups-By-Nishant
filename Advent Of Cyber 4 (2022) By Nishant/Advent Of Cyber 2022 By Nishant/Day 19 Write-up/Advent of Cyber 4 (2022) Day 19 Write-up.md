Have you ever got into 0s and 1s? Does it excite you? 🤔

Time to hack some binary! 😈

Welcome to Day 19 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*A7ErWewZXL_epV1eFTQRlg.png)

# [Day 19] Hardware Hacking Wiggles go brrr

Today’s task will discuss low-level hardware operations, hardware communication protocols, and how to analyze different protocols using different tools and techniques.

# Learning Objectives

-   How data is sent via electrical wires in low-level hardware
-   Hardware communication protocols
-   How to analyze hardware communication protocols
-   Reading USART data from a logic capture

# Welcome to the Matrix

In the world of microchips, we often don’t have this luxury. To make sure our communication protocols are efficient as possible, we need to keep them as simple as possible. To do that, we need to enter the world of 0s and 1s. For hardware communication, we use a Logic Analyzer device to analyze the signals. You can connect this device to the electrical wires used for communication between two devices that will capture and interpret the signals being sent.

# The Electrical Heartbeat

Most hardware components take an approach to turning the power on and off. If the emphasis is on, we are transmitting a digital 1. If the power is off, we are transmitting a digital 0. We call these 1s and 0s bits. To perform communication, we turn the power on and off in a specific sequence to transmit 0s and 1s. If we send 8 bits, we are sending a single byte!

Following are some of the most common protocols:

-   USART
-   SIP
-   I2C

To learn more, check out Day 19.

Let’s get started!

1.  What device can be used to probe the signals being sent on electrical wires between two devices?

Answer: Logic Analyser

2. USART is faster than SPI for communication? (Yea,Nay)

Answer: Nay

3. USART communication uses fewer wires than SPI? (Yea,Nay)

Answer: Yea

4. USART is faster than I2C for communication? (Yea,Nay)

Answer: Nay

5. I2C uses more wires than SPI for communication? (Yea,Nay)

Answer: Nay

6. SPI is faster than I2C for communication? (Yea,Nay)

Answer: Yea

7. What is the maximum number of devices that can be connected on a single pair of I2C lines?

Answer: 1008

8. What is the new baud rate that is negotiated between the microprocessor and ESP32 chip?

Use a logic analyzer tool called [Saleae](https://www.saleae.com/) to analyze the logic data dump. Start the machine; the necessary tools are installed — Double-click the Logic 2 application to open the screen.

![](https://miro.medium.com/max/215/1*9ZVt4NuAOidXeWHWfqR4Pw.png)

![](https://miro.medium.com/max/875/1*1UPugvvmKm1I4FjMz3J3sg.png)

Open a Capture option and select the santa file that is on the Desktop and click Open:

![](https://miro.medium.com/max/260/1*mCM4j_dXNmlJhmvYVB-dhA.png)

![](https://miro.medium.com/max/826/1*O926GMFlCIabGGhsLXcnWw.png)

Ignore the calibration error popup. You’ll see captures after loading. Zoom out with the Left-Ctrl+mouse wheel (or View->X Zoom Out) to see digital signals.

![](https://miro.medium.com/max/875/1*M2ZTibsDa-HsNtgCCBHoTg.png)

D0 and D1 refer to the digital channels of the probed lines. A0 and A1 refer to the analog data from the probers. Hover your mouse over the first thick line on D1 channel one and use Left-Ctrl and the mouse wheel to zoom in again; you should be able to see the entire signal transfer:

![](https://miro.medium.com/max/875/1*UqOHrP9cOdWkmX5zcDnbsA.png)

The analog voltage data corresponding to the digital signal is interesting about this screen. A1 Channel 1 vs. D1 Channel 1 shows slight breaks in analog data corrected in the digital channel. Use a logic analyzer to read data — click the Analyzers tab to the right.

![](https://miro.medium.com/max/469/1*eMHhmGX6SJxJZyWiP0BmPQ.png)

Alter your configuration to match the following and click Save:

![](https://miro.medium.com/max/649/1*dXa99ab8wWPsA-S5qo7sOw.png)

Click the little terminal Icon, and we can read the transmitted data!

![](https://miro.medium.com/max/385/1*ftkikqpkrP0qwDWxk4HpMg.png)

We see the initialization sequence of the serial line and then three lines of data being sent:

-   ACK REBOOT
-   CMDX195837
-   9600

![](https://miro.medium.com/max/373/1*UOZYMmOWRJ5jPCsnCrAVIg.png)

Click the plus icon next to Analyzers and add another Async Serial analyzer with the same configuration, except for Channel 0:

![](https://miro.medium.com/max/379/1*ptoY-aNR2MTJB74HSVSy4g.png)

![](https://miro.medium.com/max/639/1*GSIquyDoGdpbHKtENHygFw.png)

Once added, click the Trash icon in the bottom right to remove all terminal data. Once done, click on the three dots next to each analyzer and select Restart. Your terminal should now look something like this:

![](https://miro.medium.com/max/404/1*5E1dOwMjsqI0l1f7SFo4MQ.png)

Answer: 9600

9. What is the flag that is transmitted once the new baud rate was accepted?

Modify the baud rate of Channel 0 to get the flag:

![](https://miro.medium.com/max/395/1*jvQPXkRpQ5oRrRQyJFi4Ow.png)

![](https://miro.medium.com/max/639/1*Eihn8hVfxi3JR9lg0VuxDw.png)

![](https://miro.medium.com/max/370/1*09pP7538l-PLnYuYJhwSSg.png)

Answer: THM{Hacking.Hardware.Is.Fun}

10. Looking for a challenge? Try our [Recent Threats](https://tryhackme.com/module/recent-threats) module!

Answer: No answer needed

# Closure

Today’s task taught us about different hardware communication protocols. We learned how to analyze analog and digital signals for further investigation.

![](https://miro.medium.com/max/593/1*XfP2huF_12GMGptmLpb3TA.jpeg)

Excellent job; five more days to go!

> Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.