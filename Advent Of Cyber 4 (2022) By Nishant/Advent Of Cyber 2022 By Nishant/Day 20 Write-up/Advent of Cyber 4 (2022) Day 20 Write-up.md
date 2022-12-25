We hacked the wires; time to hack the firmware! 👩🏻‍💻

Welcome to Day 20 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*c-VKJpYPDtii_vreqQjFmA.png)

# [Day 20] Firmware Binwalkin’ around the Christmas tree

Today’s task will cover the basics of firmware, firmware reverse engineering, and various techniques for extracting code from firmware and modifying it as needed. We will learn how to use these techniques to hack encrypted firmware for further investigations.

**Learning Objectives**

-   What is firmware reverse engineering
-   Techniques for extracting code from the firmware
-   Extracting hidden keys from an encrypted firmware
-   Modifying and rebuilding a firmware

# What is Firmware Reverse Engineering

Every embedded system, such as cameras, routers, smart watches, etc., has pre-installed firmware with instructions running on the processor. It enables the hardware to communicate with other software. To avoid exploitation or data leakage, firmware reverse engineering extracts the original code from the binary and verifies it for security reasons. Consider a smartwatch sending all messages to a specific IP address without user indication.

# Types of Firmware Analysis

Firmware analysis is carried out through two techniques, Static & Dynamic.

## Static Analysis

Static analysis involves:

-   An essential examination of the binary file contents.
-   Performing its reverse engineering.
-   Reading the assembly instructions to understand the functionality.

## Dynamic Analysis

Firmware dynamic analysis involves running the firmware code on actual hardware and observing its behavior through emulation and hardware/ software based debugging. One of the significant advantages of dynamic analysis is to analyze unintended network communication for identifying data pilferage.

To learn more, check out Day 20.

Let’s get started!

1.  What is the flag value after reversing the file firmwarev2.2-encrypted.gpg?

Click Start Machine at the top right of the task. Click Show Split View if the machine doesn’t load. Wait 1–2 mins for the machine to load. If the page refreshes, the machine appears restarted, but progress is not lost. Use password _Santa1010_ if prompted for **a sudo** password.

## Step 1: Verifying Encryption

Open the terminal and run the `dir` command. You will see the following directories:

![](https://miro.medium.com/max/719/1*klx72nyUyodUg0cQtwHXjg.png)

Change the directory to bin using the cd bin command, and then verify encryption of firmwarev2.2-encrypted.gpg using the following command:

binwalk -E -N firmwarev2.2-encrypted.gpg

![](https://miro.medium.com/max/860/1*VisEfGY_A_ZwwBRA970g_w.png)

## Step 2: Finding Unencrypted Older Version

The unencrypted version is located in the bin-unsigned folder. Use the cd command to navigate to the bin-unsigned directory.

![](https://miro.medium.com/max/830/1*CB8IuNyWzSJ9Z-jiWNhA0g.png)

Extract the firmware using the following command:

extract-firmware.sh firmwarev1.0-unsigned

Enter Santa1010 as the password when prompted, as shown below:

![](https://miro.medium.com/max/851/1*8hDkX0bax-Y7BzZUUOPVSw.png)

## Step 3: Finding Encryption Keys

The original firmware is protected with [GPG](https://en.wikipedia.org/wiki/GNU_Privacy_Guard) requiring a public and private key and passphrase to decrypt. Extracted, unencrypted firmware is stored in the fmk folder. The easiest way to find keys is with the grep command, -i flag for case-insensitivity, and -r for recursive search in the current directory and subdirectories.

Using the following command:

grep -ir key

![](https://miro.medium.com/max/859/1*BX9FHC5zcAzw5oDluqOGwQ.png)

Let’s find the paraphrase through the same grep command:

grep -ir paraphrase

![](https://miro.medium.com/max/765/1*__yj-T7zmk9GyZq8Lr9MKw.png)

## Step 4: Decrypting the Encrypted Firmware

Import the keys using the following command:

gpg --import fmk/rootfs/gpg/private.key

While importing the private key, you will be asked to enter the paraphrase. Enter the one you found in Step 3. Santa@2022

![](https://miro.medium.com/max/830/1*RVebm9WJErgY0fujKM5gow.png)

Importing the public key using the following command:

gpg --import fmk/rootfs/gpg/public.key

![](https://miro.medium.com/max/844/1*g7SW54BX0zOIY3wZCynKjw.png)

We can list the secret keys using the following command:

gpg --list-secret-keys

![](https://miro.medium.com/max/785/1*uAJsBy8duXBxDyuHzWas0w.png)

Again change the directory by entering the command cd .. and then cd bin.  
Decrypt the firmware using the following command:

gpg firmwarev2.2-encrypted.gpg

Enter Santa@2022 as a paraphrase. Then list the files using the ls command.

![](https://miro.medium.com/max/843/1*DPPQCEGWohYJB6rmKawyPA.png)

## Step 5: Reversing the Original Encrypted Firmware

Extract the code from the firmware using either binwalk or fmk. Here we are using fmk by the following command:

extract-firmware.sh firmwarev2.2-encrypted

Use Santa1010 as the password.

![](https://miro.medium.com/max/795/1*Iu3m_TQOrN8xHxTeMHWPmQ.png)

The Camera folder in the fmk/rootfsdirectory will contain all the necessary files we will use in the next task.  
Navigate to the /home/test/bin/fmk/rootfs to find the flag:

![](https://miro.medium.com/max/781/1*R3m6uRi_fscvIKK1jax-cw.png)

Answer: THM{WE_GOT_THE_FIRMWARE_CODE}

2. What is the Paraphrase value for the binary firmwarev1.0_unsigned?

We found the paraphrase value in step 3 as Santa@2022.

Answer: Santa@2022

3. After reversing the encrypted firmware, can you find the build number for rootfs?

Search for the rootfs build number using the following command:

ls -lah * | grep build

![](https://miro.medium.com/max/834/1*u57wwleoE1QajD04W5enuw.png)

Answer: 2.6.31

# Closure

We discussed firmware and firmware reverse engineering. We learned how to extract code snippets from encrypted firmware and modify them.

![](https://miro.medium.com/max/600/0*cD4g1LNNPHlKlMD8)

Way to go!

I hope you have read my write-ups and found them easy to follow.  

>  Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.