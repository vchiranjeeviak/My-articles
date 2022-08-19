## 51% Attack and Merkle Trees in Bitcoin

## Introduction

In part 1 and part 2 we covered Consensus, State Transition System, Nonce, Mining etc.
These are necessary to understand this part. [Part 1](https://vchiranjeeviak.hashnode.dev/introduction-to-bitcoin) and [Part 2](https://vchiranjeeviak.hashnode.dev/mining-and-nonce-in-bitcoin) are here in case if you want to have a look.

In this part, we are going to cover Algorithm to check if a block is valid or not, 51% Attack and Merkle Trees. So, let's go.

## Algorithm to check validity of a block

#### Steps:


1. Check if the previous block referenced by current block exists and valid.
2. Check the timestamp of current block is greater than that of previous block.
3. Check whether the block is validated by **proof of work**.
4. Let **S[0]** be the state after the previous block is added.
5. Assume TX is the transaction list containing n transactions since the previous block is published. Then, Set the state **S[i+1] = APPLY ( S[i] , TX [i] )**. If this function returns error at any point, exit and return false.
6. Register **S[n]** as the state at the end of the current block returning true.


If it returns true at the end, the block is valid. Otherwise, invalid.

## 51% Attack

- Every part of the block chain is protected by cryptography except one thing which is the order of the transactions.

Consider the following steps done by an attacker:


1. Send 10 BTC to someone in exchange for a product that can be delivered instantly online.
2. Wait until the product is delivered.
3. Generate another transaction using same 10 BTC to themselves. This is possible if the attacker is using the same UTXO numbers.
4. Try to convince the network that the transaction made by attacker to themselves was  the first one.

After these steps:

- By the time the attacker receives the product there will be some blocks already added to the chain.
- So, the UTXO they spent on the product becomes invalid after that block.
- Now, they can't spend the same UTXO again.
- So, now the attacker tries to fork (split) the block chain by creating his own version of it.
- From that point, the attacker needs to mine his own version until it becomes the longest chain, since the longest chain is considered as the genuine one as it shows more proof of work.
- But all other miners are mining the original chain. And, one miner can't outperform all other miners combined.
- So, obviously the original chain remains longer and considered as genuine by whole network.
- This shows that to alter the block chain, the attacker needs atleast 51% of the network's computational power to create longer chain according to their wish. Hence, **51% Attack**.

## Merkle Trees

- As we know, a block contains timestamp, nonce, previous hash and transactions in it.
- The transactions are stored in the form of a special data structure called **Merkle tree**.
- A merkle tree is a type of binary tree where the transactions of a block are the leaf nodes. Every leaf node is hashed which results in hashes of each leaf node.
- Every adjacent two hashes form another hash on the level above them. This process continues until a single root node is formed on top.

![2FAD813B-1673-4D60-9F2D-33152E43C984.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1649051770123/Dum7n12Ff.jpeg)
- Timestamp, nonce, previous hash and root node of the merkle tree are considered as **header** of a block. Actual **transactions** are not part of the header.
- Only header of a block is considered while hashing a whole block.
- A node in the network can download only the header of the block from one source. They download the part of the tree that is relevant to them from another source.
- Even a small change in one transaction leads to a totally different tree and a different block altogether which can't be validated with proof of work. So, it is safe.


## Light nodes

- As of 2014, entire block chain takes 15 GB space and it grows by 1 GB every month.
- Storing this amount of data is possible for computers but not mobiles.
- A protocol known as **Simplified Payment Verification (SPV)** allows for another class of nodes to exist called **Light nodes**.
- They download only block headers, verify proof of work on block headers and then download branches which are relevant to them.
- This makes process easier for the devices with space constraints. 

## Conclusion

That's the end of the Bitcoin part of the Ethereum White Paper Simplified. From next article, we will get into Ethereum part of it.