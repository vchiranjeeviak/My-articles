---
title: "Number types ( in RUST )"
seoTitle: "Number Types in Rust"
datePublished: Sat Apr 01 2023 15:43:07 GMT+0000 (Coordinated Universal Time)
cuid: clfy57oiu00010al5dcm1hivw
slug: number-types-in-rust
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680363717208/775bb074-265a-4e19-a49b-f452cc50182f.png
tags: news, programming-blogs, coding, rust, web3

---

## Introduction

Welcome to this article in which we are going to cover what is called number datatypes in Rust. Most of the things we will discuss in this article are not just confined to Rust, but they are also evident in other programming languages. But, if you are here to learn Rust, then make sure you take a look at the previous 2 articles in this series which teach writing "Hello World" in 2 different ways.

So, let's get started.

## **A little bit about me...**

Hi reader 🖐. I am Chiranjeevi Tirunagari and I am a software engineer. You can find more about me on [**Linkedin**](https://www.linkedin.com/in/vchiranjeeviak/) and [**Twitter**](http://twitter.com/vchiranjeeviak). Also, subscribe to my [**youtube channel**](https://www.youtube.com/@chiranjeevi_tirunagari) if you are interested in Rust, DevOps and tech in general.

Now, let's really get started.

## Datatype

No matter which programming language you are dealing with, you must have heard one thing definitely which is **Datatype.** I am not getting into explaining data now. If you don't know what data is, then this is probably not for you. Usually, we are required to store some data as part of the application or program that we are writing. This data can be of many types. The names, addresses, and all other text data belong to some types. Numbers belong to some other types. We can create our own types, etc.

What we will see in this article is about **Numbers** related datatypes that are present in Rust.

## Numbers

There are different types of numbers in general when it comes to Mathematics. In programming, we usually have 3 types of numbers. They are **integers (without a fractional part)**, **floating-point (with a fractional part)** numbers, and **complex (with an imaginary part)** numbers.

In most applications, we don't need to use numbers with sharp precision or complex numbers or numbers with huge values. We can use Rust's default numbers. If you think, you need all of these, then it is recommended to use this crate called `num`. Okay, what is a **crate**? Good question. The simplest answer can be a package which provides some functionality out of the box for which we don't need to write code. We will discuss these in future articles.

Now let's see the default number types provided by Rust. But, before that, keep in mind that no matter what type it is, everything is going to be stored inside memory and it occupies some space in the memory.

### Integers

As the name suggests, these are the numbers which can be 0, positive or negative. These numbers don't consist of a fractional part. Examples can be -100, 0, 34, etc. Depending on the range that the value can possess, integers can be classified into two types.

* **Signed Integers - values can be either positive or negative**.
    
* **Unsigned Integers - values can only be positive**.
    

Depending on the space required to store in the memory, integers are classified into multiple types such as 8-bit, 16-bit, 32-bit, 64-bit and 128-bit, the max. So, a 16-bit integer only occupies 16 bits in the memory. That is how it works. But, how does the space required affect the type? It affects the range of the type.

For example, let's consider an integer of 8 bits. We know that a bit can accommodate either 0 or 1. There are 2 possibilities to fill a bit. Then, how many possibilities are there in filling 8 bits?

0 or 1 0 or 1 0 or 1 0 or 1 0 or 1 0 or 1 0 or 1 0 or 1

\_\_\_\_\_ \_\_\_\_\_ \_\_\_\_\_ \_\_\_\_\_ \_\_\_\_\_ \_\_\_\_\_ \_\_\_\_\_ \_\_\_\_\_

2^8 !

which is equal to 256. That means an 8-bit integer's capacity is 256. If it is an unsigned integer, it can hold from 0 to 255 ( total 256 values ). If it is a signed number, it can hold from -128 to 127 ( total 256 values ).

We denote a signed integer with `i` and an unsigned integer with `u`. Usually, these letters are followed by their sizes. For example, `i8`, `i16`, `u32`, `u64`, `i128`, etc.

There are two other types of integers. They are `usize` and `isize`. `u` and `i` denote the same as before, but the size depends on the architecture of the system they are running in. If it is a 32-bit system, it will be of size 32. If it is a 64-bit system, it will be of size 64.

#### Variables

Usually, we assign values to variables. Variables are just names which are bonded with some values. The syntax to create a variable is `let <variable-name>: <datatype> = <value>`. The data type is not necessary when we are initialising it with some value. If we are just declaring the variable, then it is necessary to specify the datatype that the variable is going to accept.

All the variables in Rust are immutable ( value can't be changed ) by default. But, we can make them mutable using the `mut` ( call it mutt or mute, I like to call it mute, because that makes sense ) keyword. So, the syntax looks like `let mut <variable-name> = <value>`.

#### Size interpretation

When we are not initialising a variable along with its data type, then the compiler can interpret the type depending on the value. We can give values like `29u32` or `30_i64` etc. The compiler can parse these and can interpret the values accordingly. Similarly in the case with other datatypes as well. Even if we don't add suffixes like the above, the compiler can still do the job of interpreting the type when the variable or the value inside it is used to do operations such as arithmetic operations, comparisons etc. with other variables or values.

### Floating-Point Numbers

Floating-point numbers consist of a fractional part. For example, `100.45`, `-56.32`, `20.0` are considered a floating-point number. There are two variants of floats in Rust. They are `f32` and `f64`. These types are associated with some constants like Infinity, Negative infinity, Max, Min, etc. for ease. They are also associated with some functions like `sqrt()`, `floor()`, etc.

## Conclusion

In this article, we have just seen the theory part of it. For most of us, this is just basic. In the next article, we will see some code around it.

If you find this read-worthy, please don't forget to like, share your thoughts and share this article with your friends and community because that encourages me a lot. Also, don't forget to connect with me on the socials I mentioned in the intro. Subscribe to my [**youtube channel**](https://www.youtube.com/@chiranjeevi_tirunagari) as well for similar content if you are a visual learner. Let's meet in the next article, bye-bye 👋 until then.