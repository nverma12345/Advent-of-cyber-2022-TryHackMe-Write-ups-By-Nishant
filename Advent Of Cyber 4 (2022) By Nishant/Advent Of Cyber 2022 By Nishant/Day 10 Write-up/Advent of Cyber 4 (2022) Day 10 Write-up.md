Are you excited to play a game? Of course you are!

Welcome to Day 10 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*7Ujj0y2zqYWT9NQ25K2G6Q.png)

# [Day 10] Hack a game You’re a mean one, Mr. Yeti

Are you excited to play a game? Of course, you are!

Today we will discuss how data in memory is stored and how you can alter it by changing the data values.

# Learning Objectives

-   Learn how data is stored in memory in games or other applications.
-   Use simple tools to find and alter data in memory.
-   Explore the effects of changing data in memory on a running game.

# The Memory of a Program

Whenever we execute a program, the CPU will process all data somehow through the computer’s RAM (Random Access Memory). If you think of a videogame, your HP, position, movement speed, and direction are all stored somewhere in memory and updated as needed as the game goes.

# The Mighty Cetus

Cetus is a simple browser plugin that works for Firefox and Chrome, allowing you to explore the memory space of Web Assembly games that run in your browser. The main idea behind it is to provide you with the tools to quickly find any piece of data stored in memory and modify it if needed. On top of that, it will let you change a game’s compiled code and alter its behaviors if you want, although we won’t need to go that deep for this task.

To learn more, check out Day 10.

Let’s get started!

1.  What is the Guard’s flag?

Follow the step-by-step instruction in the Day 10 task.

![](https://miro.medium.com/max/875/1*GtvJwrzu9Nzy17nnIeAaSw.png)

When you follow all the steps in the instructions, you will save the memory address as a bookmark.

![](https://miro.medium.com/max/674/1*7183mM-Y37re_oUFOnVR3A.png)

Note that Cetus uses hexadecimal notation to show you the numbers. If you need to convert the displayed digits to decimals, you can use [this website](https://www.rapidtables.com/convert/number/hex-to-decimal.html).

With Cetus on the bookmarks tab, talk to the guard again and notice how the random number changes immediately. You can now guess the number:

![](https://miro.medium.com/max/624/1*0cy94o0n0LkLm96pb8ICbw.png)

Convert the hexadecimal value to decimal, and then when the guard asks for the input, type it there and press Enter.

![](https://miro.medium.com/max/875/1*FbhpGLJSTIEXjRXYb9QLBQ.png)

Voila!  
Walk towards the guard and talk to him, and you will get the flag as shown below:

![](https://miro.medium.com/max/875/1*bx67NjU9bqw6wE3qNfmfKA.png)

Answer: THM{5_star_Fl4gzzz}

2. What is the Yeti’s flag?

To find the next flag, we have to cross the bridge. To accomplish this, we must find our HP value in the memory and alter it.  
Start with a differential search, and don’t give any value as input.

![](https://miro.medium.com/max/875/1*-yFPhn-jmcBpYwlYt1PshQ.png)

You can run a second search using the LT operator without setting a value to search:  
Try to get damaged by moving towards the snowballs.

![](https://miro.medium.com/max/660/1*MI_DT1Hs-ZFs-AIJCLhwkg.png)

You could do another search with the GT operator with no value again.

![](https://miro.medium.com/max/668/1*l4f4EOAremTgChKPRVE3Xw.png)

We found the memory address of our HP and changed its value to a high value(e.g., 99999), and we crossed the bridge.

![](https://miro.medium.com/max/875/1*vt2IfFyeTOodj7aHr-KYSA.png)

Interact with Bandit Yeti, and you will get the flag as shown below:

![](https://miro.medium.com/max/804/1*3m1WfXgHr53YJP-EulAQVQ.png)

Answer: THM{yetiyetiyetiflagflagflag}

3. If you liked today’s challenge, the [Walking an Application](https://tryhackme.com/room/walkinganapplication) room is an excellent follow-up!

Answer: No answer needed

# Closure

Today’s task covered how data gets stored in memory and how addresses are assigned to each value. We also learned how third-party tools could modify and alter data.

![](https://miro.medium.com/max/593/1*H5NW0ytVILPHGhXGXtP6qg.png)

I hope you had fun and enjoyed today’s task.  

>_Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.