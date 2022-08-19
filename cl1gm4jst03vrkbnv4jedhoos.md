## Mining and Nonce in Bitcoin

## Introduction

This is part 2 of the Ethereum White Paper Simplified. You can check the part 1 [here](https://vchiranjeeviak.hashnode.dev/introduction-to-bitcoin). Part 1 covers History, Proof of Work and Proof of Stake, State Transistion System of Bitcoin and UTXO.

To understand this part, part 1 is a prerequisite.  So, do check it out before this.

or If you want to know basics of block chain, you can read this [short article](https://vchiranjeeviak.hashnode.dev/what-is-block-chain)

Now let's get into this one.

## Stage for mining

- The main motive behind Bitcoin is to build a decentralised currency system.
- We already saw how Bitcoin state transition system works in part 1.
- To make it secure and stable, we need a **consensus system** to ensure that everyone agrees to how state transition system making changes to bitcoin's state by adding transactions or simply the order of transactions.
- Let's see how a block looks like:


![925A0EF7-2EB0-4917-B0B9-1DE6D4BDDE5A.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1648828087551/StZUChYyx.jpeg)

Here,

1. Time = Time stamp at which that block was created.
2. Nonce = A random number which is the heart of proof of work. ( more on this later).
3. Prevhash = The hashed value of previous block. Every block has hash of previous block to connect as a chain.
4. Transactions = List of transactions.

## Mining

- In a block chain network, there will be thousands of nodes.
- Whatever exchange happens between the nodes in network is called a transaction.
- In case of bitcoin, it is just currency. But in case of other block chains like ethereum, it can be data, tokens (NFTs, contracts etc) that we can exchange on network.
- In the network, every node contains the image of block chains's current state.
- A new block is created or mined by **miners** whenever a certain number of transactions are done after the previous block was mined.
- This number changes from chain to chain.
- The time taken to create a new block from the addition of previous block to the chain is called **block time**.
- The **block time** for bitcoin is **10 minutes**. It means, for every 10 minutes, a new block is added to the bitcoin block chain.
- Creation of a block is done by **miners**.

### Task of Miners

- Miners are also nodes in the network but containing enough computational power to solve cryptographic puzzles.
- After a miner node creates a new block, it is sent to all other nodes in the network so that they can add it to the block chain in their machine.
- There will be multiple nodes competing to create/mine a block simultaneously.
- This is because the miner of a block receives incentive in exchange for their computational power.
- Whoever miner manages to create the block first gets the incentive and their block is added to the block chain.

Let's assume a scenario where all the nodes in the network have equal computational power and are trying to create/mine a block at a time.

Are all the miners manage to mine the same block at the end?

To find the answer to this, we need to know about **Nonce**.

### Nonce

- **Nonce** is a pseudo-random number. It is pseudo-random because, once a number is used as **nonce** in a block, it is not used again.
- Hash value of every block is calculated so that it can be used in next block to chain them.
- According to proof of work, the hash of a block should start with a certain number of zeroes. This number changes from time to time.
- So, a miner node task is to hash a block such that the resulting hash is smaller than a variable number  (**2^187** , at the time of Ethereum white Paper was published. This also implies that it should have a certain number of zeroes at the starting of hash).
- Bitcoin uses **SHA256** algortihm to hash the block. If by using **SHA256**, the miner couldn't get the hash value smaller than the given number, then the miner has to change the input.
- But we can't change the time, previous hash and transactions of a block. That is the reason why the concept of **nonce** was introduced.
- To change the input to achieve a hash with particular features, we need a variable in input. And **nonce** is that variable.
- So, miners keep applying **SHA256** to the block buy changing the **nonce** value each time until they get a hash value less than a particular number.
- There can be multiple **nonce** values which can make this possible.

So, according to this, even if all the mining nodes with equal computational power try to mine at a time, they can mine different blocks having different **nonce** values as multiple nonce values are possible for same block to satisfy that zeroes condition.

## Conclusion 

That's a wrap for this article. Like and share this if it helped you some way.

** Make sure you follow me on **
- [Twitter](https://twitter.com/VChiranjeeviAK)
- [LinkedIn](https://www.linkedin.com/in/chiranjeevi-tirunagari-685459191/)
- [Showwcase](https://www.showwcase.com/vchiranjeeviak)