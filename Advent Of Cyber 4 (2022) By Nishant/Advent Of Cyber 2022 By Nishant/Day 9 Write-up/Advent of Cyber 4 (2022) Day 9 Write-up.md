Have you ever heard of pivoting?

Welcome to Day 9 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*IYCjG_Rfh-R3-F77_XWIEw.png)

# [Day 9] Pivoting Dock the halls

Today’s task is one of the most exciting and heart-beating and will discuss dockers and their vulnerabilities. We will exploit a vulnerable docker server using Metasploit and Meterpreter.

# Learning Objectives

-   Using Metasploit modules and Meterpreter to compromise systems
-   Network Pivoting
-   Post exploitation

# What is Docker?

Docker is a way to package applications and the associated dependencies into a single unit called an image. This image can then be shared and run as a container, either locally as a developer or remotely on a production server. A common way to tell if a compromised application is running in a Docker container is to verify the existence of a /.dockerenv file at the filesystem’s root directory.

# What is Metasploit?

Metasploit is a powerful penetration testing tool for gaining initial access to systems, performing post-exploitation, and pivoting to other applications and systems. Metasploit is free, open-source software owned by the US-based cybersecurity firm Rapid7.

# What is a Metasploit session?

After successfully exploiting a remote target with a Metasploit module, a session is often opened by default. These sessions are often Command Shells or Meterpreter sessions, which allow for executing commands against the target. It’s also possible to open up other session types in Metasploit, such as SSH or WinRM — which do not require payloads.

# What is Meterpreter?

Meterpreter is an advanced payload that provides interactive access to a compromised system. Meterpreter supports running commands on a remote target, including uploading/downloading files and pivoting.

To learn more, check out Day 9.

Let’s get started!

1.  Deploy the attached VM, and wait a few minutes. What ports are open?

Using the following command: (You can replace the IP with your target machine IP)

nmap -T4 -A -Pn 10.10.129.42

![](https://miro.medium.com/max/875/1*BYgjHGcKhMUWCHR-dkEUAg.jpeg)

Answer: 80

2. What framework is the web application developed with?

After loading the web application in our browser at [http://10.10.129.42:80](http://10.10.129.42/) (use Firefox on the Kali web-Machine) and inspecting the Network tab, we can see that the server responds with an HTTP Set-Cookie header indicating that the server is running Laravel — a typical web application development framework:

![](https://miro.medium.com/max/875/1*nnHB1Qf014O-vY8akfnsEA.png)

Answer: Laravel

3. What CVE is the application vulnerable to?

Run the Metasploit using the following command:

msfconsole

Search for Laravel in Metasploit using the following command:

search laravel

![](https://miro.medium.com/max/875/1*DZToFa--FqcMlPaW0Z4hew.png)

Then using the info command, you can search for its details as shown below:

![](https://miro.medium.com/max/661/1*y4daY89-ij7ngoTQGyb-VA.png)

Scroll down, and you will find the details regarding the registered CVE for this vulnerability.

Answer: CVE-2021-3129

4. What command can be used to upgrade the last opened session to a Meterpreter session?

We can use Metasploit to verify if the application is vulnerable to this exploit.

![](https://miro.medium.com/max/875/1*DYq8m87PyUHOtJAdP9Em7Q.png)

Now that we’ve confirmed the vulnerability, let’s run the module to open a new session:

![](https://miro.medium.com/max/875/1*e8WP0NgN8DE5acOKybZBFw.png)

The opened shell will be a basic cmd/unix/reverse_bash shell. We can see this by running the background command and viewing the currently active sessions:

![](https://miro.medium.com/max/875/1*-m075PidovSYIXOgX1Akrw.png)

If you are currently in a session — you can run the background command to go back to the top-level Metasploit prompt. To upgrade the most recently opened session to Meterpreter, use the sessions -u -1 command. Metasploit will now show two sessions opened — one for the original shell session and another for the new Meterpreter session:

![](https://miro.medium.com/max/875/1*UDZ3qzYF4EOzVwp-sjEcnQ.png)

Answer: session -u -1

5. What file indicates a session has been opened within a Docker container?

**.dockerenv** or **.env** indicates that the session has been opened within the Docker container.

![](https://miro.medium.com/max/811/1*oijcObrCqCI5z6-q4radkA.png)

Answer: /.dockerenv

6. What file often contains useful credentials for web applications?

By reading the .env file in the session, we’ve found credentials for the web applications.

![](https://miro.medium.com/max/629/1*1WIuXRxje1_NW-7DGv8zIA.png)

Answer: .env

7. What database table contains useful credentials?

We can use Meterpreter to resolve this remote hostname to an IP address that we can use for attacking purposes:  
As this is an internal IP address, it won’t be possible to send traffic to it directly. We can instead leverage the network pivoting support within msfconsole to reach the inaccessible host. To configure the global routing table in msfconsole, ensure you have run the background command from within a Meterpreter session:

![](https://miro.medium.com/max/863/1*yIGuE24gHPNzW_MF9ru1QQ.png)

We can also see, due to the presence of the /.dockerenv file, that we are in a docker container. By default, Docker chooses a hard-coded IP to represent the host machine. We will also add that to our routing table for later scanning:

![](https://miro.medium.com/max/815/1*U8hwceFHT7k_km5k4X_jfw.png)

![](https://miro.medium.com/max/744/1*RvuEuvC9Axk2ou-e3PZ4Pg.png)

With the previously discovered database credentials and the routing table configured, we can start to run Metasploit modules that target Postgres. Beginning with a schema dump, followed by running queries to select information out of the database:

![](https://miro.medium.com/max/875/1*Mx5LAUWqB67FzKkbeRObKg.png)

From the users table, we can get the users’ credentials in the database using the following command:

run postgres://postgres:postgres@172.28.101.51/postgres sql='select * from users'

![](https://miro.medium.com/max/875/1*hzvoqnYIqyRgw7TfpQk3Ng.png)

Answer: users

8. What is Santa’s password?

In the previous step, we found Santa’s password.

Answer: p4$$w0rd


