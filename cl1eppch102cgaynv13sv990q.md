## Introduction to Bitcoin

## Introduction

This is an attempt to simplify Ethereum White Paper and this is the part 1 of it. My main motive is to make it understandable to beginners. Even I am a beginner, so I know the pain.

In part 1, I am covering half of the Introduction to Bitcoin and other existing topics like History and Bitcoin as State Transition System. These are necessary premises to the Ethereum.

If you want to know **basics of block chain**, you can read  [my article on Basics of Block chain](https://vchiranjeeviak.hashnode.dev/what-is-block-chain).

or 

If you want to know **how Web3 is different from Web2**, you can read [this article on Web1.0 Vs Web2.0 Vs Web3.0](https://vchiranjeeviak.hashnode.dev/web-10-vs-web-20-vs-web-30)

## History

There were many attempts made before Bitcoin to create an alternative currency. The reason for this is out of the context of this article. It's some complex economics. This article deals with technical part of it.

All of those attempts were failed for different reasons.

- In 1998, **b-money** became the first proposal to introduce the idea of creating money through solving computational puzzles. It failed as it couldn't implement decentralised consensus.
- **Decentralised consensus** is a set of rules used to verify a transaction on the block chain. These are the rules on which everyone in the network are agreed upon.
- In 2005, a concept called **Reusable proofs of work** was introduced which uses the idea from b-money along with the computationally difficult puzzles to create a concept of cryptocurrency.
- It was failed as it couldn't find a way to make this entire process secure in the backend.
- In 2009, Satoshi Nakamoto implemented the first decentralised currency by combining the established primitives for managing the ownership through public key cryptography with a consensus algorithm for keeping track of who owns the coins, known as **proof of work**

## Proof of Work and Proof of Stake

- Bitcoin initially used **Proof of Work** consensus algorithm.
- As said earlier, a **consensus algorithm** is an agreed set of rules on how the state of block chain can change.
- **Proof of Work** also provides a mechanism of deciding who gets to influence the consensus or decision making power in simple terms.
- This decision making power depends on the weight of a node.
- According to **Proof of Work**, the weight of a node is decided by the computational power that the node brings in to the network.
- Let's see below example to understand this better.

Assume a random event 'X' is happened in the network. There are only 2 options here. Either 'X' is true or 'X' is false.

If more than 50% of the computational power agrees to 'X', then it is true. Else, it is false.

- Later, an alternative approach was proposed called **Proof of Stake**.
- According to **Proof of Stake**, the weight of a node is decided by the currency it holds.
- So, in the above example, if nodes with more than 50% of the currency when combined decides a random event 'X' as true, then it is true. Else, it is false.
 
## Bitcoin As A State Transition System

- The ledger of a cryptocurrency such as bitcoin can be thought as a **State Transition System**.
- A ledger in general, is nothing but keeping track of all transactions.
- The **state** consists of **ownership** status of all existing bitcoins.
- The **state** changes whenever a new transaction is made.
- The **State Transition Function** decides what happens when a transaction is initialised.

```

STF (S, TX)   ->   S'   or   Error

here, STF  =  State Transition Function 
              S  =  Current State (consider as bank account)
            TX  =  Transaction 
             S'  =  New State
``` 
- A **State Transition Function** takes the **Current State** and **Transaction** as input and gives a new **New State** or **Error** as output.
- The state in Bitcoin is the collection of all coins that have been minted and not yet spent. These are called **Unspent Transaction Outputs** or **UTXO** (consider as currency notes). 
- Each **UTXO** has a denomination (like how we have in our physical money) and owner.
- A transaction contains one or more input UTXO and a cryptographic signature (like how we sign a cheque) produced by the private key of owner produces one or more output UTXO.

### Transaction Status

- The **State Transition Function** modifies the state only when the transaction is valid.

A transaction is valid only when it satisfies all the following conditions:

1.  All the input UTXO should be present in Current State (S) (every note you are sending should belong to you).
2. The signature of the transaction should match the owner of all input UTXO (like how the signature on the cheque should match the owner of that account).
3. The sum of denominations of all input UTXO should not be less than sum of denominations of all output UTXO (your account should have the amount in the first place to send it to some one else. If you want to send 10k to someone, your account should contain more than 10k right).


- If any of the above conditions are not met, the transaction is invalid and **State Transition Function** returns an **error**.
- If a transaction is valid, then **State Transition Function** returns a **New State (S')**
- In the **New State (S')**, the input UTXO of previous transaction are removed and output UTXO from **State Transition Function** are added.

### Unspent Transaction Outputs (UTXO)

- A UTXO can be considered as a currency note in physical money.
- An UTXO that is not present in **Current State (S)** is equivalent to a fake currency note.
- In physical money, there is no concept of ownership. Whoever possesses it, they are the owner.
- In Bitcoin, every UTXO has an owner, and the ownership changes only when the owner agrees.


## Conclusion

That's it for this one. In the next article we will cover Mining and Merkle Trees.

Share this one if you find it worth reading.

If you want the notes version of it, follow me on LinkedIn, I will post it there or DM me on Twitter. (links are below)

- Twitter: [VChiranjeeviAK](https://twitter.com/VChiranjeeviAK)
- LinkedIn: [Chiranjeevi Tirunagari](https://www.linkedin.com/in/chiranjeevi-tirunagari-685459191/)
- Showwcase: [Chiranjeevi Tirunagari](https://www.showwcase.com/vchiranjeeviak)