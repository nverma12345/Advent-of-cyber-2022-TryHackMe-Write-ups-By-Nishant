Are you familiar with Regex? Let’s dive in and learn regex!

Welcome to Day 17 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*hN0CTvj4nCwZ-FhdSmCvTQ.png)

# [Day 17] Secure Coding Filtering for Order Amidst Chaos

Today we will discuss how to improve security using HTML5 and Regex combined. We will cover the basics of regular expressions and learn how to use them to enhance web application security.

# Learning Objectives

-   There needs to be more than understanding input validation.
-   Learn the basics of HTML5 and Regex
-   Implement HTML5 and regex to improvise the security of the web application

# HTML5 and Regex

HTML5’s <input> element provides helpful capabilities for user input validation, such as type filters for email, URL, or file. You can use regex in the “pattern” attribute for more granular control. Examples are:

1. <input type="text" id="uname" name="uname" pattern="[a-zA-Z0-9]+">  
2. <input type="email" id="email" name="email" pattern=".+@tryhackme\\.com">

The first pattern is alphanumeric and case-insensitive; the second requires an email ending with “@tryhackme.com.”

# Regex 101

This section will talk about some regex tips to get you started. To match _any lowercase_ character from the English alphabet, the regex pattern is [a-z]. We can deconstruct it as follows:

-   The square brackets indicate that you’re trying to match _one character_ within the set of characters inside of them. For example, if we’re trying to match any vowel of the English alphabet, we construct our regex as follows: [aeiou]. The order of the characters doesn’t matter, and it will match the same.
-   Square brackets can also accept a range of characters by adding a hyphen, as seen in our original example.
-   You can also mix and match sets of characters within the bracket. [a-zA-Z] means you want to match any character from the English alphabet regardless of case, while [a-z0–9] means you want to match any lowercase alphanumeric character.

![](https://miro.medium.com/max/875/1*2QYIYfmI5I6-LuD-h2hETg.png)

To learn more, check out Day 17.

Let’s dive in!

1.  Filtering for Usernames: How many usernames fit the syntax above?

Press the Start Machine button to start the VM. If not visible, use the Show Split View button at the top-right. Access the regex exercise via the machine.

To practice your regex, first, change your working directory to the RegExPractice folder using the command: cd ~/Desktop/RegExPractice then, you may use _egrep_ via the following syntax: egrep ‘regex_pattern_here’ strings or the _regex_checker.py_ script written for you via python: python3 regex_checker.py.

![](https://miro.medium.com/max/869/1*LEPjWhx-43R0fKBmOvDCTQ.png)

![](https://miro.medium.com/max/875/1*ztw0m5kfUKOhdghpxI6j6w.png)

An alternative way of counting the usernames is using the following command:

egrep '^[a-zA-Z0-9]{6,12}$' strings | wc -l

![](https://miro.medium.com/max/875/1*W_fIOYdtYznu2N4kS4XuPg.png)

Answer: 8

2. Filtering for Usernames: One username consists of a readable word concatenated with a number. What is it?

From the previous output, we got the answer:

![](https://miro.medium.com/max/875/1*RO7w9-aAVByZL68y6DhojQ.png)

Answer: User35

3. Filtering for Emails: How many emails fit the syntax above?

Using the following command:

egrep '.+@.+\.com' strings

![](https://miro.medium.com/max/875/1*S447SOCH1cvPzwMAKs7v3g.png)

Answer: 11

4. Filtering for Emails: How many unique domains are there?

![](https://miro.medium.com/max/875/1*qmFVsJq9xAlUe1fFM-pWbA.png)

Answer: 8

5. Filtering for Emails: What is the domain of the email with the local-part “lewisham44”?

![](https://miro.medium.com/max/875/1*s-nabyVsfSFa09Pst-hdoQ.png)

Answer: amg.com

6. Filtering for Emails: What is the domain of the email with the local-part “maxximax”?

![](https://miro.medium.com/max/691/1*b0CU7hEH8JF50_QWfo8aPA.png)

Answer: fedfull.com

7. Filtering for Emails: What is the local-part of the email with the domain name “[hotmail.com](http://hotmail.com/)”?

![](https://miro.medium.com/max/686/1*DuDTCwVfL8vDkgH7L_uG9w.png)

Answer: hussain.volt

8. Filtering for URLs: How many URLs fit the syntax provided?

Using the following command:

egrep '^http(s)?.{3}(www)?.+\..+$' strings | wc -l

![](https://miro.medium.com/max/875/1*M3-W82B2nQRTXhtKFZuxvg.png)

Answer: 16

9. Filtering for URLs: How many of these URLs start with “https”?

Using the following command:

egrep '^https.{3}(www)?.+\..+$' strings | wc -l

![](https://miro.medium.com/max/875/1*1RRJjnNls60BMSnAurOeHQ.png)

Answer: 7

10. If you feel like you could use more fundamental skills in your life, try the [Linux Fundamentals](https://tryhackme.com/module/linux-fundamentals) module. All rooms are free in that one!

Answer: No answer needed

# Closure

Today’s task taught us that Input validation is a critical security control but continues beyond there. User input may be valid but can still be harmful. Tools and frameworks like HTML5 and regex can help reduce the attack surface. Server-side validation techniques like output escaping and developers should also use parametrized queries. Layering these controls is the best way to approach security.

![](https://miro.medium.com/max/600/0*0VYeAAAUJwssOMXm)

Woo hoo!  
I hope you found this write-up easy and fun to follow.

> Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.