Did you forget to close the door? 😱 You might leave an IDOR❗️

Welcome to Day 14 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*uAmwApuyBMRoX6l32WQUKg.png)

# [Day 14] Web Applications I’m dreaming of secure web apps

Today’s task will cover the basics of Web applications security and its importance. We will discuss one of the popular OWASP tops ten vulnerabilities called Insecure Direct Object Reference (IDOR).

# Learning Objectives

-   Web Applications
-   The Open Web Application Security Project (OWASP) Top 10
-   IDOR

# Web Application

A web application is a piece of software that we can use via a web browser. Unlike computer programs and smartphone applications, a web application does not require any installation on the user’s system to make use of it. To use a web application, we only need a web browser, such as Firefox, MS Edge, Google Chrome, or Safari.

# Access Controls

Access control is a security element that determines who can access certain information and resources. After authentication (covered in Day 5), access control enforces the appropriate access level. In the online shopping example, a vendor should be able to update the prices or descriptions of their products. However, they should not be able to modify the information related to other vendors. A customer, on the other hand, should be able to view but should not be able to alter the data.

# Web Application Vulnerabilities

The OWASP was established to improve software security. The [OWASP Top 10](https://owasp.org/Top10/) list aims to raise awareness regarding common security issues that plague web applications. This list would help software developers avoid common mistakes to build more secure products. Other users, such as penetration testers and bug bounty hunters, can use this list to serve their purposes.

IDOR refers to the situation where a user can manipulate the input to bypass authorization due to poor access control. IDOR was the fourth on the OWASP Top 10 list in 2013 before it was published under Broken Access Control in 2017.

To learn more, check out Day 14.

Let’s get started!

To start the AttackBox and the attached Virtual Machine (VM), click on the “Start the AttackBox” button and click on the “Start Machine” button. Please give it a couple of minutes so that you can follow along.

On the AttackBox, start the Firefox Browser and open the URL `http://MACHINE_IP:8080`. This link should show you a login page. McSkidy has provided us with the following credentials to test the web application:

-   Username: `mcskidy`
-   Password: `devtest`

1.  What is the office number of Elf Pivot McRed?

Open Firefox browser and enter your MACHINE_IP as the URL as shown below:

![](https://miro.medium.com/max/875/1*W4BCSVZ9ngLFFyabtweCSA.png)

Use the given credentials and log in:

![](https://miro.medium.com/max/623/1*QMxC6xX4l-ohZYEEStR_nA.png)

Change/Increment the ID in the URL to find the Elf Pivot McRed user account:

![](https://miro.medium.com/max/849/1*OABKDL8B5FPMYmaKx0VXSA.png)

Keep incrementing the ID. When you reach 105, the Elf Pivot McRed user account will appear as shown below:

![](https://miro.medium.com/max/843/1*WmLhsKu0VtqXSNPWdKskCA.png)

Answer: 134

2. Not only profile pages but also stored images are vulnerable. Start with a URL of a valid profile image; what is the hidden flag?

Right-click on the profile image of McRed and then click on View image as shown below:

![](https://miro.medium.com/max/500/1*87uuZxDosRU50JEpNMcJpg.png)

After incrementing and decrementing the ID finally, you will find the flag as shown below:

![](https://miro.medium.com/max/630/1*9v1At9_L_RBg1jo1J_ANRQ.png)

![](https://miro.medium.com/max/798/1*LrkG10otShoP3hapoCyRig.png)

Answer: THM{CLOSE_THE_DOOR}

3. Do you like IDOR? It’s an Advent of Cyber classic! If you want more, check out the dedicated [room](https://tryhackme.com/room/idor) or the [Corridor](https://tryhackme.com/room/corridor) challenge.

Answer: No answer needed

# Closure

Today we learned about web applications and their security, why a database is used in web applications, what are access controls, what are web applications’ vulnerabilities and IDOR, and how to identify them.

![](https://miro.medium.com/max/500/1*OYf8AbExT3mNQFwTW84bkA.jpeg)

You got it! 👏  
Today’s task was easier than other tasks we have solved.  

> _Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.