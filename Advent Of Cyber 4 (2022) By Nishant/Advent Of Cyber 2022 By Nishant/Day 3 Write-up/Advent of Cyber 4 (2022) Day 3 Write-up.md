It’s time to do some OSINT!  
Welcome to Day 3 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*h5bDne_HnpewrNwkh5xqjg.png)

# [Day 3] OSINT Nothing escapes detective McRed

Today’s task will discuss OSINT (Open Source Intelligence), the Google Dorking method, WHOIS lookup, and other tools to extract publicly available information online.

# **Learning Objectives**

-   What is OSINT, and what techniques can extract useful information against a website or target?
-   Using dorks to find specific details on the Google search engine
-   Extracting hidden directories through the Robots.txt file
-   Domain owner information through WHOIS lookup
-   Searching data from hacked databases
-   Acquiring sensitive information from publicly available GitHub repositories

# What is OSINT

OSINT is gathering and analyzing publicly available data for intelligence purposes, which includes information collected from the internet, mass media, specialist journals and research, photos, and geospatial information. You can access the information via the open internet (indexed by search engines), closed forums (not indexed by search engines), and even the deep and dark web. People tend to leave much information on the internet that is publicly available, which later results in impersonation, identity theft, etc.

# Google Dorks

Google Dorking involves using specialist search terms and advanced search operators to find results that are not usually displayed using regular search terms. You can use them to search specific file types, cached versions of a particular site, websites containing specific text, etc.

Some of the widely used Google dorks are mentioned below:

-   **inurl**: Searches for a specified text in all indexed URLs. For example, inurl:hacking will fetch all URLs containing the word “hacking”.
-   **filetype**: Searches for specified file extensions. For example, filetype:pdf “hacking” will bring all pdf files containing the word “hacking”.
-   **site**: Searches all the indexed URLs for the specified domain. For example, site:tryhackme.com will bring all the indexed URLs from tryhackme.com.
-   **cache**: Get the latest cached version by the Google search engine. For example, cache:tryhackme.com.

To dig deeper, refer to [Day 3 of Advent of Cyber 4 (2022)](https://tryhackme.com/room/adventofcyber4).

Let’s get started!

1.  What is the name of the Registrar for the domain santagift.shop?

Using the following command in Kali Linux:

whois santagift.shop

![](https://miro.medium.com/max/875/1*nGpzRniNLCGtmaSO1nTcRQ.png)

Answer: Namecheap Inc.

2. Find the website’s source code (repository) on [github.com](https://github.com/) and open the file containing sensitive credentials. Can you find the flag?

Search for [santagift.shop](http://santagift.shop/) on the [github.com](http://github.com/) website.

![](https://miro.medium.com/max/875/1*PoZuXv5m5aueSZR7wq1h1g.png)

From the results, the first one is more appealing to be related to the [santagift.shop](http://santagift.shop/) website.

![](https://miro.medium.com/max/875/1*f1sy2599a7gDCHmCuDMUrQ.png)

After opening the SantaGiftShop repository, scroll down, and you will notice this message under the Files sections which tells us the config.php contains the credentials we are looking for. Open the config.php and search for the flag.

![](https://miro.medium.com/max/875/1*DNKIV46-h9IjFpL7xAfBZw.png)

Here we’ve found the flag.

![](https://miro.medium.com/max/824/1*mDWNNQBSQjV-ctEcyiwyNA.png)

Answer: {THM_OSINT_WORKS}

3. What is the name of the file containing passwords?

From the previous step, we got to know that config.php contains credentials. If we dig in a bit more, we can see the database’s secret keys (passwords) are stored here.

![](https://miro.medium.com/max/754/1*uniXoJdpB1PdoardfUfFgg.png)

Answer: config.php

4. What is the name of the QA server associated with the website?

In the config.php file, the QA server associated with the website is qa.santagift.shop.

![](https://miro.medium.com/max/743/1*F6VeZlNTRB74_GOEy4smSQ.png)

Answer: qa.santagift.shop

5. What is the DB_PASSWORD that is being reused between the QA and PROD environments?

![](https://miro.medium.com/max/743/1*KsHZ-DZStmeMMeBTpSGnTg.png)

Answer: S@nta2022

6. Check out this [room](https://tryhackme.com/room/googledorking) if you’d like to learn more about Google Dorking!

Answer: No answer needed

# Closure

Today’s task covered the basics of OSINT and different OSINT techniques such as Google Dorking, WHOIS lookup, Robot.txt, Breached Database Search, and Searching GitHub Repos.

![](https://miro.medium.com/max/875/1*5xd4caStabVaxHrJHmM1QA.jpeg)

Yay! You did a great job!

We are done with Day 3 and Day 4 is coming soon. 

> Follow me on LinkedIn: [https://www.linkedin.com/in/nishantverma123/](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.