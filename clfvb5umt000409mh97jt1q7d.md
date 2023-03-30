---
title: "Traditional Hello World ( in RUST )"
seoTitle: "hello world in rust"
seoDescription: "The best hello world in rust programming tutorial."
datePublished: Thu Mar 30 2023 16:06:21 GMT+0000 (Coordinated Universal Time)
cuid: clfvb5umt000409mh97jt1q7d
slug: traditional-hello-world-in-rust
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680192205617/1efa2431-b3ea-48ed-9ec9-3aba6fee0e27.png
tags: tutorial, newbie, programming-blogs, beginner, rust

---

## Introduction

If you are new to Rust and you are here to know how to write "Hello World", I recommend you to check [Simplest Hello World Ever ( in RUST )](https://vchiranjeeviak.hashnode.dev/simplest-hello-world-ever-in-rust) first and then check this one. Even if you are new to programming, please check the above-mentioned article up to the **Installation (rustup)** part because that install rust compiler which is necessary for this article as well.

## A little bit about me...

Hi reader 🖐. I am Chiranjeevi Tirunagari and I am a software engineer. You can find more about me on [Linkedin](https://www.linkedin.com/in/vchiranjeeviak/) and [Twitter](http://twitter.com/vchiranjeeviak). Also, subscribe to my [youtube channel](https://www.youtube.com/@chiranjeevi_tirunagari) if you are interested in Rust, DevOps and tech in general.

## Context

Okay so now that we have everything ( just the rust compiler ) setup, we can start.

A tradition that is being followed from the ages while learning a new programming language is to write a **Hello World** program that prints the text "Hello World" in the console or terminal from where you have run it.

This is usually the easiest program to write in any language as is in the case of Rust. So, let's do that.

## Hello World

To write a program, we need a file. And, this file's name should end with `.rs` extension which denotes the rust file. We can create files in multiple ways. But, as a programmer ( new or experienced ), it is our birthright to use terminal commands. The command to create a file is `touch <file-name>`. Feel free to name it whatever you want. I am going to name it **hey.rs** . So, the actual command that I need to use is `touch hey.rs`. This will create the file and you can open it using your favourite code editor ( vim/neovim users, I m watching you 😅 ).

### Functions

We will discuss functions in detail in future articles, but let's understand what functions are at the basic level. **Functions** contain some code and we can run that code by calling these functions. In other words, when we call a function, it means that we are running code living inside that function. Different functions can have different names.

But, how do we define a function with a name? write code inside it? and call it?

#### Definition

To define a function, we need to use the keyword `fn` which denotes function and we specify the name using the syntax `fn <function-name>() {}`. We will see about the parenthesis `"()"` later in some other article but this is how we define a function.

Let's define a function with your name. I will do it with my name "Chiranjeevi" 👇

```rust
fn chiranjeevi() {}
```

#### Code

For this article's purpose, we just need to know coding how to print "Hello World". So, let's just do that.

To print anything to the terminal, the easiest way is to use `print!()` or `println!()` macros. We will see what macros are and how they are different from functions later. But, for now, what we need to know is that whatever we give inside the parenthesis `()` for `print!` and `println!` is printed to the terminal. The only difference is that `println!` shifts the cursor to the next line and `print!` keeps it in the same line.

Now, let's try to print "Hello World" using `print!` 👇

```rust
fn chiranjeevi() {
    print!("Hello World");
}
```

You might have observed those quotes `"` inside parenthesis `()` and surrounding our message. So, that's how we do to pass static ( which don't need to change anytime you run ) strings ( spoiler alert: slice / literal ).

And the lines are terminated with the semi-colon `;` .

#### Function Call

To do what we are expecting our function to do which is printing "Hello World", we need to call it. Otherwise, no matter how many functions you write, they are useless and don't do anything unless you call them. We call functions with the syntax `<function-name>();`. So, to call the above function, we have to do `chiranjeevi()`.

But, where do we do it? Let's see now 👇

### Main

**main** is also a function whose name happens to be main which contains the code that needs to be run when the application starts running. This code inside the main can call other functions too which will run some other code and so on. But the important point here is that the main function is where the code execution starts when an application is started running.

Whatever "Hello World" program we are gonna write now is also an application (app). So, it needs to have a main function.

Now you might have understood that we need to call the above-created function inside the main. Let's do that.

```rust
fn chiranjeevi() {
    print!("Hello World");
}

fn main() {
    chiranjeevi();
}
```

### Compilation

To convert the code that we have written in Rust into an **executable file** which can be run to perform what we have written as code, we need to compile the program. The command to compile a program is `rustc <file-name>`. In my case, it is going to be `rustc hey.rs`.

This will generate one or two files depending on your OS. In windows, there will be 2 or 1 in Mac/Unix with the name the same as the file you created. These are the binary files of program that we have written. To run these we need to do `./hey` in Mac/Unix or `.\hey.exe` in windows.

You will see output something like this 👇

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680183685940/e928dca3-7f22-4b38-9959-6013a66b2950.png align="center")

Try to see what the output looks like when `println!` is used instead of `print!`, you will get the difference.

### Small change...

If you see, we don't actually need another function which runs print line. We can directly write that line inside `main` instead of writing in another function and calling that function. There won't be any change in the output, but we can reduce a function call.

So the final program should look like 👇

```rust
fn main() {
    print!("Hello World");
}
```

## Conclusion

Whoaaa!!!! We just completed our "Hello World" without the help of cargo. But, please don't work without cargo when you are dealing with Rust.

If you find this read-worthy, please don't forget to like, share your thoughts and share this article with your friends and community because that encourages me a lot. Also, don't forget to connect with me on the socials I mentioned in the intro. Subscribe to my [**youtube channel**](https://www.youtube.com/@chiranjeevi_tirunagari) as well for similar content if you are a visual learner. Let's meet in the next article, bye-bye 👋 until then.