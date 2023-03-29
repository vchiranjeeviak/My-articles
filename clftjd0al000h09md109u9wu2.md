---
title: "Simplest Hello World Ever (in RUST)"
seoTitle: "Introduction to Rust with simplest Hello World"
seoDescription: "An introduction to rust programming with the simplest hello world program ever."
datePublished: Wed Mar 29 2023 10:20:19 GMT+0000 (Coordinated Universal Time)
cuid: clftjd0al000h09md109u9wu2
slug: simplest-hello-world-ever-in-rust
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680091492079/20564bdf-4c84-4dc9-94f6-34be48cb82ca.png
tags: programming-blogs, rust, hello-world, rust-solana-web3, rust-lang

---

---

## Introduction

If this is not your first "Hello World" tutorial, then you probably already know how they start.

* Creating a file.
    
* Writing main function (in some languages).
    
* Writing print statement with "Hello World".
    
* Run it and claps 👏👏👏.
    

This is not going to be one of those. That kind of "Hello World" is coming in the next article, but for this one, it is going to be different and simpler.

## A little bit about me...

Hi reader 🖐. I am Chiranjeevi Tirunagari and I am a software engineer. You can find more about me on [Linkedin](https://www.linkedin.com/in/vchiranjeeviak/) and [Twitter](http://twitter.com/vchiranjeeviak). Also, subscribe to my [youtube channel](https://www.youtube.com/@chiranjeevi_tirunagari) if you are interested in Rust, DevOps and tech in general.

## Setting up

If you check any computer system which is being used by a software engineer for a long period, it is more probable to find a JDK ( may god bless if you don't know what it is, it is worth doing a google search if you don't know ) installed already. Because it is tried by almost everyone in tech at least once.

It is not the case with Rust 🦀 ( this is the last time, I m going to use this emoji, I promise ) though. It is pretty new and only a handful of people got hands-on with it. Hence, you need to install the **rust compiler** (rustc) to continue from here. If you already have one, feel free to skip this part.

How do you check if it is already there? Execute `rustc -V` in your terminal or command prompt. If you get some version numbers, you are good to go. If you see an error then you need to install it.

### Installation (rustup)

If you go here: [https://rustup.rs/](https://rustup.rs/) , you will see the command 👇

```powershell
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Execute this command in your terminal or command prompt which will install **rustup** which is an installer for rust compiler and other rust tools.

After this, you should be able to get your compiler version using `rustc -V`.

## Cargo

rustup installs something called **cargo** along with rustc. To put it in simple terms, cargo is a **package manager ( helps manage packages also called crates in rust )** and a **build tool ( helps convert rust code to binary )** for rust. More about the cargo on some other day. Let's concentrate on the goal of this article which is 👇.

## Hello World

Now that we have our setup ready, let's start with our actual motive. For that, we need to create a project. To do that, we have a cargo command `cargo new <project name>`. Use this command in the terminal to create the project with the name you want. I am creating a project with the name **hello**. So, my command looks like `cargo new hello`.

If you do `ls` in unix/Mac or `dir` in windows, you should see a directory with the name **hello** or whatever name you have given. This directory contains some files which we will discuss in future articles.

For now, let's change to that directory using `cd` command. I am doing `cd hello`.

Now run `cargo run` in the terminal and Tada!! ✨✨

I hope you have seen "Hello, world!" in the terminal. The code for this is written inside `main.rs` file inside `src` sub-directory. When we run `cargo run`, cargo automatically compiles all the rust files in the project and starts running the project. Since, we have only one rust file which prints "Hello, world!", it did just that.

## Thoughts...

We can do the same thing without using cargo by writing a rust file by ourselves without any project and writing the basic code that is required and compiling it and then running it. The reason why I started with cargo is that it is such a useful and powerful tool, so to show the taste of it. The only time I did everything manually without cargo is when I wrote my first hello world ( I m not experienced in rust, lol 😅 ) in Rust. But, it is good to know how things work. So, we will do it in the next article.

## Conclusion

If you find this read-worthy, please don't forget to like, share your thoughts and share this article with your friends and community because that encourages me a lot. Also, don't forget to connect with me on the socials I mentioned in the intro. Subscribe to my [youtube channel](https://www.youtube.com/@chiranjeevi_tirunagari) as well for similar content if you are a visual learner. Let's meet in the next article, bye-bye 👋 until then.