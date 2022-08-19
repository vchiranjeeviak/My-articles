## Smart Contracts and Solidity Part-1

## Introduction

This article gives an overview on **smart contracts**, **EVM**, **Basic solidity**.

Checkout my previous article on [Ethereum vs Ether](https://vchiranjeeviak.hashnode.dev/ethereum-vs-ether). And checkout my profile for **Ethereum White Paper Simplified** series.

Now let's get into this one.

**Solidity** is an object-oriented, high-level language to implement **smart contracts**.

## Smart contracts

- **Smart contracts** are computer programs which are processed and replicated on all computers in the block chain network.
- They allow us to make transactions when certain conditions are met automatically without any coordinator.
- These smart contracts on etheruem block chain are written using **solidity** programming language.

## Ethereum Virtual Machine (EVM)

- **EVM** (Ethereum Virtual Machine) is a decentralised computational engine which is present in all the devices participating in ethereum network.
- It runs execution and deployment of smart contracts.
- Ethereum has 2 types of accounts  which are **Externally Owned Accounts (EOA)** and **Contract Accounts**. Both of these are treated equally by EVM.
- EOAs are controlled by private keys whereas contract accounts are stored in smart contracts, also known as smart wallets.
- EVM is a runtime environment used for solidity just like JVM for Java, NodeJS for Javascript.

## Solidity Part-1

### Initialising a smart contract

- In the very first line of every solidity file, we need to specify the compiler version that we are going to use to compile that file. 
- We do that using `pragma solidity <version>` 
- Next thing is to specify the name of the contract. A contract in solidity is equivalent to a class in java.
- The syntax to specify a contract is `contract <name> {      }`.

```solidity
pragma solidity ^0.8.10;

contract Example {
    // code
}
```

### Variables and Datatypes

There are 3 types of variables in solidity. They are :


1. **Local** - These are declared inside a function and are not stored on block chain.
2. **State** - These are declared outside a function but inside the contract to maintain the state of the smart contract. These are stored on block chain.
3. **Global** - These are injected by EVM during the runtime. These provide information about block chain such as timestamps, hash, etc.

A few basic datatypes in solidity are:

- **uint (unsigned)**, **int(signed)** - There are multiple sized uint and int like 8, 16, 32, ..., 256 bits.
- **bool** - For boolean values i.e true or false.
- **address** - A special datatype to store ethereum addresses.
- **string** - To store letters or sentences.
- **array** - To store collection of similar other datatype items.

There are some other datatypes as well which are covered in next articles.

- **public** keyword is used to let those variables or functions accessible from the outside of the contract.
- **memory** keyword is used to make the variables available temporarily rather than entire runtime of contract. It is usually used when passing arguments.

#### Arrays

- Arrays are initialised as `<datatype>[] <name>`.
- **push** function is used to add item to an array and **pop** function is used to remove an element from an array.  

### Loops and Control Structures

- Loops are same like in any other programming language. Same while, do-while, for loops.
- if, else, break and continue for control statements

### Functions 

- The syntax to write functions is 

`function <name>(<arguments>) <view/pure> returns (<return type>) { ... }`

- A **view** function is a function which doesn't change the state variables of the contract. View functions doesn't require any **gas**.
- We discuss about pure functions in next article.

An example contract using topics discussed above (check comments in program).

```solidity
pragma solidity ^0.8.10;

contract Example {
    address owner = 0x111122223333444455556666777788889999AAAABBBBCCCCDDDDEEEEFFFFCCCC; // state variable
    function sum (uint num) public view returns (uint) { // A public view function
          uint sum = 0; // local variable
          for(uint i = 0; i <= num; i++) {
              sum = sum + i;
          }
          if(msg.sender == owner) { // msg.sender is global variable
               return sum;
          }
          return 0;
    } // It is a view function because it is not changing the only state variable (owner).
}
```
## Conclusion

That's it for this one. Do follow for more content.

**Like** and **Share** if you feel the content is great. **Thank you** for reading.

** Make sure you follow me on **
- [Twitter](https://twitter.com/VChiranjeeviAK)
- [LinkedIn](https://www.linkedin.com/in/chiranjeevi-tirunagari-685459191/)
- [Showwcase](https://www.showwcase.com/vchiranjeeviak)