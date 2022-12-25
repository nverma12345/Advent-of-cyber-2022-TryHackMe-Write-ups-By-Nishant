Did you know that contracts became smart?

Welcome to Day 8 of Advent of Cyber 4 (2022) write-up. To check the room, [click here](https://tryhackme.com/room/adventofcyber4).

![](https://miro.medium.com/max/875/1*M3RPIMj_3CRfm5PaWbxKIA.png)

# [Day 8] Smart Contracts Last Christmas I gave you my ETH

Today’s task will cover the overview of blockchain and cryptocurrency. We will also discuss smart contracts and their role in blockchain and cryptocurrency transactions. Ultimately, we will get to know a common vulnerability in smart contracts and do a small practice on it.

# Learning Objectives

-   Explain what smart contracts are, how they relate to the blockchain, and why they are essential.
-   Understand how contracts are related, what they are built upon, and standard core functions.
-   Understand and exploit a common smart contract vulnerability.

# What is a Blockchain?

By definition, a blockchain is a digital database or ledger distributed among nodes of a peer-to-peer network. The blockchain is distributed among “peers” or members with no central servers, hence “decentralized.” Due to its decentralized nature, each peer is expected to maintain the integrity of the blockchain.

# Introduction to Smart Contracts

Smart contracts are most commonly used as the backbone of DeFi applications (Decentralized Finance applications) to support a cryptocurrency on a blockchain. DeFi applications facilitate currency exchange between entities; a smart contract defines the details of the exchange. A smart contract is a program stored on a blockchain that runs when pre-determined conditions are met.

To learn more, refer to Day 8.

Let’s get started!

1.  If not already completed, download the zip folder attached to this task, and open Remix in your preferred browser.

Answer: No answer needed

2. What flag is found after attacking the provided EtherStore Contract?

Open [https://remix.ethereum.org/](https://remix.ethereum.org/).

You will need to import the task files to get started with the task. To do this, navigate to _file explorer → default_workspace → load a local file into the current workspace_. From here, you can select the necessary .sol files to be imported. We have provided you with an EtherStore.sol and Attack.sol file that functions as we introduced in this section.

![](https://miro.medium.com/max/875/1*EZ_A2uCYz9SL-8an6zFbWg.png)

## **Compiling the Contracts**

The next step is to compile the contracts, navigate to the _solidity compiler_, and select 0.8.10+commitfcxxxxxx from the dropdown _compiler_ menu. Now you can compile the contract by pressing the _compile_ button. You can ignore any _warnings_ you may receive when compiling.

![](https://miro.medium.com/max/875/1*n6I7VSrw-VfcWrKex2WR1w.png)

![](https://miro.medium.com/max/875/1*iuAKgrpuSqmFTphOpqApyQ.png)

Now that we have the contracts compiled, they are ready to be deployed from the deployment tab. To the right is a screenshot of the deployment tab and labels we will use to reference menu elements as we move throughout the deployment process.

First, we must select a contract for deployment from the _contract_ dropdown (_label 6_). We should deploy the EtherStore contract or target contract to begin. You only need to press the _deploy_ button (_label 7) for deployment._

![](https://miro.medium.com/max/391/1*o8RHu4o_fiJWgyx076CufA.png)

We can now interact with the contract underneath the _deployed contracts_ subsection. To test the contract, we can deposit Ether into the contract to be added to the total balance. To deposit, insert a value in the _value_ textbox (_label 4_).

![](https://miro.medium.com/max/369/1*nEEoMDqLEcKpqdBV4EOq-A.png)

and select the currency denomination at the dropdown under _label 5._ Once setup is complete, you can deposit by pressing the deposit button (_label 10_).

![](https://miro.medium.com/max/461/1*mb71dIQHiM_W-iI0fc9Ulg.png)

Note: when pressing the deposit button, this is a public function we are calling just as if it were another contract calling the function externally.

We’ve now successfully deployed our first contract and used it! You should see the _Balance_ update (_label 9_).

![](https://miro.medium.com/max/373/1*rG6D7g1H2GabJ5wX_e8l-g.png)

Now that we have deployed our first contract, switch to a different account (dropdown _label two_ and select a new account) and repeat the same process. This time you will be exploiting the original contract and should see the exploit actively occur! Below is a summary of the steps to deploy and interact with a contract.

**Step 1:** Select the contract you want to deploy from the _contract_ dropdown menu under _label 6_.

**Step 2:** Deploy the contract by pressing the deploy button.

Note: you need to reference the contract you are targeting before deploying the attack contract. To accomplish this, copy the address for _EtherStore_ from _label 11_ and paste the value in the textbox under _label 8_.

**Step 3:** Confirm the contract was deployed and the attack function can be seen from the _deployed contracts_ subsection.

![](https://miro.medium.com/max/394/1*J7iArqTKb-F7-68T7wjmJg.png)

**Step 4:** Execute and interact with the contract’s function; note that most functions require some form of valuable input to execute a function properly.

![](https://miro.medium.com/max/875/1*5FgPtCDj9qHq3wqoS_QVKA.png)

Answer: flag{411_ur_37h_15_m1n3}

3. Are you up for a little challenge to celebrate Day 8? Try your hand at these easy challenge rooms: [Quotient](https://tryhackme.com/room/quotient) and [Agent T](https://tryhackme.com/room/agentt)!

Answer: No answer needed

# Closure

Today’s task taught about Blockchain, cryptocurrency, and secret contracts. We also learned about a common vulnerability in smart contracts and practiced a practical application.

![](https://miro.medium.com/max/593/1*6xdCfhPhyQG6KhmlPQzQbA.jpeg)

You did an amazing job!

> _Follow me on LinkedIn:_ [_https://www.linkedin.com/in/nishantverma123/_](https://www.linkedin.com/in/nishantverma123/)

Thank you for reading.