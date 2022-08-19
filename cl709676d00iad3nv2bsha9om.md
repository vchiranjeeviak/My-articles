## Go - Pointers, User input

## Introduction

This is the **part 3** of the **Go lang** series. In the previous part, we saw what variables, constants and datatypes are. Check **[Part 2](https://vchiranjeeviak.hashnode.dev/go-variables-constants-and-datatypes)** if you missed it. In this one lets see what pointers are and how we can take input from the user who is running the program.

## Before going into pointers (very important to understand pointers)

Before understanding pointers, we need to understand how the program execution works. It is different from language to language and it will be similar for some languages. Some programming languages interact with computer memory and some don't. So, "What memory are we talking about?". It is **Random Access Memory** (RAM).

#### Memory

Any high-level program or software is basically stored in hard disk to use it whenever needed. The programs written in these type of languages are loaded into RAM when we want to run and then each line of code starts running there. Any memory needed to run that like storing variables, constants etc is also taken from RAM. Sometimes, some data used by a running program can be stored in cache or in secondary memory which is hard drive depending on few factors.

Some languages like Java, Javascript, Python etc have their own runtime environments. These runtime environments act as an interface between programs and actual memory. They still use primary memory to run but not directly. They actually use something called **virtual memory** which maps to actual main memory of system. The addresses will be different for actual and virtual and can be mapped only by these runtime environments which is a very low level implementation. This is bit out of the way to our intention of this article. So, let's continue with RAM for now since Go doesn't use any runtime environment and directly interacts with system memory.

#### Memory animation

![Untitled_Artwork (1).gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1660886226110/qQAsjVnEf.gif align="left")

### Addresses

So, now that we know that programs especially of C, C++, Go run in RAM and these use some memory to store data required to run. The unit of memory is **bytes**. And `1 byte = 8 bits`. A **bit** can contain either 0 or 1. Each byte in a memory device can be uniquely identified by its **address**. The address will be of the form **Hexadecimal**. Something like `0x324XF432`. And there is an order for these addresses because the memory is continuous.

Can we see the address of a variable programatically? Yes, we can do by using the `&` operator. On a side note, an operator is a symbol which performs a special operation on some data **(operands)**, and the number of operands is dependent on the operator. `&` operator is applied on only one operand, hence, it belongs to **unary operators** group. There are other groups like **binary operators** (2 operands) and **ternary operators** (3 operators). So, the only operand that `&` (ampersand / address) operator takes is the variable name.

#### Program to find address of a variable

An example program to get the address of a variable:

```go
package main

import "fmt"

func main() {
    someVariable := 10

    fmt.Println(someVariable) // This prints value of someVariable
    fmt.Println(&someVariable) // This prints address of someVariable
}
```
Output:

![Screenshot 2022-08-19 at 12.02.03 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660890802406/EbVdLElFC.png align="left")
This output of address will be different for system to system. Even we get different address value every time we run. 

## Pointers

So, now we know how and where data (variables, constants) is being stored. This is where pointers come into picture.

#### Definition

**Pointer** is just another datatype like int, string, boolean. But, what a variable of type pointer stores is **address**. We saw how addresses look like in above output. A pointer stores those kind of address. Whose address they store? We can store addresses of other variables and constants.

#### Questions to keep in mind for future

What is the point of storing addresses? How are pointers useful? Are pointers good or bad? These are valid questions. To know the answers, we need to go deeper into learning this language. We will find out answers to each of these questions in future articles. These questions are highlighted as topics in future articles. So do wait / check if they are already published by me.

#### Pointer of pointer

We saw that a pointer variable stores addresses. So, it is just like any other variable, which means that it is also stored in memory, which means that a pointer variable also has an address, which means that this address value can be stored in other pointer, which is called **pointer of pointer**.

I hope you got an idea on pointers. You will be more confident when you get to know the answers to the above questions. So, just keep this concept in mind.

## User input

Now that we are comfortable with the concept of addresses and how variables are stored, it is a perfect time to know how to take input from user while program is running (run time).

As we discussed in previous articles, even though we are not having a value while writing program and taking that value from user in run time, we need to reserve some space in our program memory to store it when program receives it. And we do that by declaring (not initialising, check **[Part 2](https://vchiranjeeviak.hashnode.dev/go-variables-constants-and-datatypes)**) a variable for this value.

#### Scan

The function we use to take user input is **Scan**. It belongs to the same **"fmt"** package to which **Print** also belongs. If I forgot to convey that **fmt** is short for **format**, now you know.

So, we pass the address (I hope you know how to get address of a variable from above part of article) of the variable in which we want to store the input value to the Scan function. This function pauses the program execution when it reaches that line and waits for user to give the input. Once the user gives input and hits `Enter`, it resumes from there.

#### Program to illustrate user input

An example program which takes a number as input from user and prints the next number to the screen:

```go
package main

import "fmt"

func main() {

    var number int // declaring integer variable

    fmt.Scan(&number) // we pass address using &
    // The program execution pauses here until user provides input and hits enter

    fmt.Println(number+1) // Printing next number
}
```
It will wait like this until you give some number to it and hit `Enter`. If you give other than a (int) number, it throws an error.

![Screenshot 2022-08-19 at 2.28.35 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660899657118/l3dKkwTJe.png align="left")

I gave `122` as input and hit `Enter`. Here is the output.

![Screenshot 2022-08-19 at 2.29.22 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660899691607/Uz9SEYQd9.png align="left")

#### User input in Go/C/C++ vs Python/Java/Javascript

This is how we take user input in run time. We can learn this concept in the introductory class / video / article of languages like python or java. It is because that there is no concept of interacting with memory in them. So, there are no addresses in them. But, Go has this like C/C++ and so we had to learn about addresses first.

## Conclusion

That's it for this one. Next article conditionals and loops in Go.

Do follow me to see them. Make sure you like and share if you felt this good.

Let's connect on: [Twitter](https://twitter.com/VChiranjeeviAK) [LinkedIn](https://www.linkedin.com/in/chiranjeevi-tirunagari/) [Showwcase](https://www.showwcase.com/vchiranjeeviak)