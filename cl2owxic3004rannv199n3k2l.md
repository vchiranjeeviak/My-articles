## Gas in Ethereum

## Introduction

Hey reader, this article covers all about gas in Ethereum block chain. Checkout my previous article on [Solidity Part-1](https://vchiranjeeviak.hashnode.dev/smart-contracts-and-solidity-part-1) if you are into development side or [Ethereum Vs Ether](https://vchiranjeeviak.hashnode.dev/ethereum-vs-ether) if you are just learning about cryptos.

Let's get into this one.

## Gas

- For a transaction to be written on block chain, there must be some miner node mining that block. 
- Mining a block requires some computational power to do it. So, to compensate these miners for using their computational power, they are incentivized with some fees. This is called **gas fees**. 
- The **computational power** they spend is considered as **gas**. 

## Gas fees calculation

- It is important to know how the gas is calculated especially if you are a developer. Because, when writing smart contracts, we write many operations which require gas. So, in order to optimize the gas utilization, we need to be aware how gas fees is calculated.
- After the **London upgrade** in 2021, the way gas fees is calculated is changed. So, let's break this into 2 parts. **Pre-London upgrade** and **Post-London upgrade**. 

 ### Pre-London upgrade

- Before London upgrade, the gas fees is calculated using a very simple formula      `GAS FEES = GAS SPENT * GAS PRICE `
- Here, gas price is the amount of ether that the user is willing to pay per gas unit. 
- Gas prices are denominated using **'Gwei'(Giga wei)** - a denomination of ETH. `      1 Gwei = 0.000000001 ETH or 1 ETH = 10^9 Gwei `
- The cheapest transaction in terms of gas on Ethereum block chain is transfer of ETH from one account to other. 
- The gas price that an user want to spend can be decided by the user. But the transactions with higher gas price have higher priority than the transactions with lower priority.
- Wallets like metamask usually estimate the gas that is required for those transacations depending on the network situation. 

  #### Gas calculation at hardware level 

- The smart contracts we write using solidity (in ethereum) is compiled into **bytecode** which boils it down to the **opcodes**. 
- Opcodes are nothing but **basic** operations (ADD, SUB, MUL, DIV, LOAD etc) that can be run on hardware. 
- A large operation in solidity is **divided** into multiple simple opcode operations. 
- Each **opcode** has a **fixed gas price**. So, gas cost of an operation in solidity is equal to the sum of gas cost of all of it's opcodes. 
- Therefore, operations which require more opcodes require more gas than the operations which require less opcodes. 

  #### Gas limit 

- Ethereum supports very complex operations other than just transfering ETH. The operations may contain loops, require user inputs, control structures etc.. 
- It is hard to estimate gas requirements of these operations due to their logic. 
- So, wallets support the feature called **Gas limit**. We specify the **maximum amount of gas fees** we want to spend for that transaction. 
- If the transaction actually uses below that limit, the remaining amount is **refunded** into our account. If the transaction requires more than our limit, the transaction gets **cancelled**. 

 ### Post-London upgrade

- Before the london upgrade, wallets like metamask used to provide gas estimations based on the previous blocks. Metamask especially used to scan previous 1000 blocks to estimate the gas fees. 
- After the london upgrade, **every block** was set to have a **base gas price fees**. This is the **mandatory** fees need to be paid by the user to get their transaction included in the block. 
- Along with that the user needs to be include a **priority fees**. This can be set by the user or wallet provides some recommended estimates. Higher the priority fees, earlier the transaction is included in the block. 
- So, `GAS FEES = GAS SPENT * (BASE GAS FEES + PRIORITY FEES)`. 

   #### Variable block sizes

- Prior to London upgrade, the block gas limit was **same** for each block. It used to be 15M gas for each block. 
- After London upgrade, the block gas limit can be **varied** depending on the demand and can go upto **30M**. But the **base limit** is **15M**. 
- The base gas fees of a block is calculated depending on the gas limit of the previous block. 
- If the previous block limit is **greater** than 15M, the base gas fees of the present block is **increased** and if the previous block limit is **lesser** than 15M, the base gas fees of current block is **decreased**. 
- The amount of increase or decrease **depends on how above or below** the limit of previous block is from 15M point. 

## A huge advantage of gas

- Smart contracts in Ethereum are programmed using a programming language called solidity.  
- It is very common to have bugs in a program like **infinite loops**. 
- These are **very costly** in block chain as they use lot of gas and new blocks keep getting added until the loop ends. But it doesn’t end as it is an infinite loop. This creates a ruckus in the block chain. 
- The **limit** we put on gas fees helps in avoiding this. If the gas limit is hit by our contract, then the execution stops automatically, which prevents infinite time of execution. 

## Reducing gas fees

- A complaint on using Ethereum is **high gas fees** when compared to other block chains. This is going to be addressed in **Ethereum2.0**. 
- Apart from that, we can also use **Layer 2**, which performs heavy tasks on other similar platform and publish the end result on the main. This results in lower gas fees and faster executions. 

## Conclusion

That's it for this one. Do follow for more content.

**Like** and **Share** if you feel the content is great. **Thank you** for reading.

** Make sure you follow me on **
- [Twitter](https://twitter.com/VChiranjeeviAK)
- [LinkedIn](https://www.linkedin.com/in/chiranjeevi-tirunagari-685459191/)
- [Showwcase](https://www.showwcase.com/vchiranjeeviak)
