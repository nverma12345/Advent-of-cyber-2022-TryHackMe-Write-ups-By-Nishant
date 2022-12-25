Injections hurt! 💉😱

Welcome to Day 16 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*1MtNbbduI1ErdgGCfBDZZg.png)

# [Day 16] Secure Coding SQLi’s the king, the carolers sing

In today’s task, we will learn about SQL Database (MySQL), PHP coding, and how developers can use both to secure the website. We will also discuss SQL injection and ways to avoid it.

# Learning Objectives

-   Understand what SQL is
-   Learn how to read PHP code
-   How to secure PHP code to prevent SQL injections

# SQL Refresher

**Structured Query Language (SQL)** is the traditional language used to ask databases for information. When you build any application that relies on a database, the app will need to create SQL sentences on the fly and send them to the database engine to retrieve the required information for your app to work. Luckily for you, developers built SQL with simplicity in mind, and its syntax is supposed to resemble straightforward English sentences to make it easier for programmers to understand.

MySQL stores information in structures called tables. Think of them as any table in a spreadsheet document where you have columns and rows.

To learn more, check out Day 16.

Let’s get started!

1.  What is the value of Flag1?

Armed with all this knowledge, we are ready to fix the app. You’ll have access to a simple editor to modify the app’s source code during this task. Any changes you make in the editor will go live instantly if you save your changes (by pressing CTRL+S). If you are using a VPN connection, you can access the code editor from any browser of your preference. If you use the AttackBox instead, Firefox is installed and available on the machine’s desktop. To get to the code editor, point your browser to the following address:

[http://10-10-77-182.p.thmlabs.com/](http://10-10-77-182.p.thmlabs.com/) (**Note:** Replace your machine IP with the given IP before .p.thmlabs.com/)

To enter the code editor, use the following credentials:

-   Username: coder
-   Password: coder

![](https://miro.medium.com/max/875/1*YtqZGmG4l5mGSN_4u3dskw.png)

Change the query in the elf.php to the given command just by adding the intval() function:

$query="select * from users where id=".intval($_GET['id']);

Then click on the Run Checks:

![](https://miro.medium.com/max/875/1*mx5jRD8G72KYeWGaUz97FA.png)

Voila! We got the first flag.

![](https://miro.medium.com/max/875/1*2961bOIs7zl4s7zFOp3PJw.png)

Answer: THM{McCode, Elf McCode}

2. What is the value of Flag2?

Open search-toy.php in the code editor and change the code to the given below:

$q = "%".$_GET['q']."%";  
$query="select * from toys where name like ? or description like ?";  
$stmt = mysqli_prepare($db, $query);  
mysqli_stmt_bind_param($stmt, 'ss', $q, $q);  
mysqli_stmt_execute($stmt);  
$toys_rs=mysqli_stmt_get_result($stmt);

Now click on the Run Checks again, and you will get the second flag:

![](https://miro.medium.com/max/875/1*DPgrKfID-JCqUYoXVkEKwg.png)

Answer: THM{KodeNRoll}

3. What is the value of Flag3?

From the McExploit report, we can learn that toy.php has a vulnerability, as shown below:

![](https://miro.medium.com/max/875/1*8iEeRnFOfrEf-JW4S43cnQ.png)

Since there is a vulnerability in toy.php, navigate to it and change the following lines and get the flag:

![](https://miro.medium.com/max/875/1*bseXxW-ggmOEMIbXnEk7-w.png)

![](https://miro.medium.com/max/875/1*otU_AJVVGk1mX_Ixbxm6RA.png)

Answer: THM{Are we secure yet?}

4. What is the value of Flag4?

Again from the McExploit report, we got to know that login.php is vulnerable:

![](https://miro.medium.com/max/875/1*O8ACCKhkhFgv8dR44dTJcg.png)

Apply the following changes and click on Run Checks:

$query="select * from users where username=? and password=?";  
$stmt = mysqli_prepare($db, $query);  
mysqli_stmt_bind_param($stmt, 'ss', $username, $password);  
mysqli_stmt_execute($stmt);  
$users_rs=mysqli_stmt_get_result($stmt);

![](https://miro.medium.com/max/875/1*Gbo2GUZ6bkQY0mEty1BLMw.png)

Answer: THM{SQLi_who???}

5. If you’d like more SQLi in your life, check out this [room](https://tryhackme.com/room/sqlinjectionlm)!

Answer: No answer needed

# Closure

Today’s task taught us about SQL queries and PHP code. We learned how to use secure coding techniques to implement defense mechanisms to avoid SQL injections.

![](https://miro.medium.com/max/625/0*fvOdpbRx-N8zD0SV)

You rock!

> Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.