## Go - Hello world

## Introduction to Go

**Go lang** or simply **Go** is a programming language developed by **Google**. No one creates a programming language just like "Hey, I am bored today, so let's create a programming language" (like how I am writing this article). There must be some reason to create a programming language.

And that reason is the growing needs for the advanced infrastructure. Earlier, the servers of applications used to be less efficient when compared to today's. That is because the infrastructure today is distributed and processors are multi-core and multi-threaded. We need to take full advantage of these advanced features to make our applications more efficient.

**What does distributed system and multi-core architecture do?**

They help running applications run in a parallel manner. So, assume that there are 3 operations in an application such as uploading a file, downloading a file and deleting a file. In most modern applications, we can do these 3 operations simultaneously. This is possible by distributed system and multi-core processor.

### Distributed infrastructure

Let's see how such distributed system works. A distributed system is a system in which the different logical parts of that system is located on different machines but still act as a single machine (server). In our example, one machine takes care of uploading files, one for downloading files and other for editing files.

### Multi-core processors

Let's see how a multi-core processor works. Assume that we are downloading 10 files at a time. In case of a single core processor, these files are pushed into a queue. One file is downloaded at a time and one after the other. In case of multi-core processor, each core takes one process, so if there are 10 cores, 10 files can be downloaded in the time of one file download.

This is how the modern applications can leverage the present infrastructure and architecture for high performance.

### Concurrency

But there is one problem that can be faced using distributed architecture. Consider this situation. You shared a file in our application to another user with write permissions. It can be a problem if that user tries to delete a file when you are trying to edit that file. It can be an ambiguous situation. An ideal situation should be that application should only let one user either to delete or edit the file at a time.

This can be achieved through concurrency. Not all programming languages support concurrency by default. But, **Go** supports **concurrency** out of the box.

### Pros of Go

- The **build time** and **run time** (if not aware of difference between build time and run time, will be explained below) of **go** programs is rapid almost same as **C**/**C++**.
- **Simplicity** - It is simple to write programs in go and run them.
- **Go** uses fewer resources (memory and processor) than most other programming languages.

### Go characteristics

- **Go** is used in backend to write services which interact with cloud infrastructures or databases or any other services.
- It is a **compiled** language which means that every program of **Go** is compiled and the compiler produces a **binary** file with **.exe** extension. The time taken to produce a **binary (.env)** file from a given program is called **build time**.
- It is a **platform independent** language. A binary file compiled in one OS can be run in other OS as well. This binary file is what makes the program execution. The time taken to run a program binary file is called **run time**.

Ok, that's it for the basic stuff. Let's dive into the interesting stuff. For that we need two things. A code editor and Go language in our machine.

### Installing VS code

[Link to install VScode](https://code.visualstudio.com/download) - Go to this link and you will see something like this.


![VScode installation pic](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/47rhnd30kigwm8782f6e.png)

Choose according to your operating system and install. Installation should be straight forward.

### Installing Go

[Link to install Go](https://go.dev/doc/install) - Go to this link and select your operating system to install.

![Go installation pic](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9vxd1fu01h690p7lomd4.png)

This installation is also fairly straight forward.

To check successful installation, open terminal / command prompt and type `go` and press `Enter`. If you can see something like this, it means **Go** installed **successfully**.

![go command result](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/p2d71u11ghw32xeeda9m.png)

## Hello world in GO

- Create a new folder or use an existing folder to store our hello world program file. I am naming the folder as `hello-world`

- Open that folder in VScode.

![Open folder](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1cxa6xq2uxq8gojlqv15.png)

- Whenever we are starting a new Go project in a folder, the first thing we need to do is to initialise a project in that folder. The command to do that is `go mod init <project name>`. Execute this command in terminal / command prompt or VScode in-built terminal. It is recommended and a good convention is to have same name for both folder and project.

- What the above command does is that it creates a file called `go.mod`. If you are familiar with **nodeJS** family, it is something similar to `package.json` file. If you are not familiar with it, it's just a file which contains details about the project which contains project name, dependencies, etc.

![Intialisation](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/b64k0w6k6h7xdl95eq8u.png)

- Now create a file and name it whatever you like but with the extension `.go`. I am naming it as `hello.go`

![Extension install](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/r76kz0nexxe2nm6z72vh.png)

- The moment you create a file with `.go` extension for the first time in your VScode, it will recommend some extensions to install like in the above picture and also like in the below picture. Just install all the extensions. Wherever you find `install all`, do that. If not `install` will be there, do that.

![Extension install all](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ed4y57k5joj18osay1pj.png)

- Now we are perfectly ready to write our first program in **Go**. So, let's go.

### Coming to the code

Most programming languages have a starting point from where the program execution starts. Similarly, **go** programs have a starting point which is **main** function.

To simply put, a **function** is an isolated block of code which performs a certain task. A **function** doesn't interact with other parts of program unless we specify it to.

There are 3 parts of a function. They are:

1. Function header
2. Function arguments
3. Function body

#### 1. Function header

It starts with a keyword `func` in go. And a keyword is a specific word which is reserved for a specific purpose and we can't use them for any other purposes. Function header also contains the name of the function with which we want to uniquely identify and call it. The syntax will be like `func <function name>`

#### 2. Function arguments

**Function arguments** are wrapped inside a pair of parenthesis `()`. We use arguments to pass data to a function. Remember from the upper part where we discussed that a function is isolated from other parts of program. So, we use these function arguments as a medium to pass data in order to perform required task. There can be any number of arguments for a single function depending upon the task and requirements of that task. Let's say we have a function which performs addition of two numbers which a user gives in run time. Since they come in run time, we can't hardcode them inside function. The only way is to take input from user while running application and pass those inputs to a function which performs addition. And we pass those inputs to that function using its arguments. So, in this case, our addition function requires two arguments. The arguments syntax look like `(<arg 1>, <arg 2>, ...)`

#### 3. Function body

This is the place where we write actual logic to the task it is specified to do. In above addition example, we want our function to add two given numbers. Hence, the core logic of the function goes inside the body. The body of a function is wrapped inside curly braces `{ }`.

Let's combine everything and write the syntax of entire function.

```go
func <function name> (<arg1>, <arg2>, ...) {
    // function body goes here
}
```

So, coming back to the starting point of program topic. Starting point of a go program is a special function named **main**. And the program execution starts here no matter how many lines of code or how many functions are there in the program.

So, the main function in **hello world** program is going to look like:

```go
package main

import "fmt"

func main() {
    fmt.Print("Hello world")
}
```

Hey, here are two lines those we haven't discussed about.

Yeah... I know.

The line 1 - This is a mandatory line for every program which depicts the package to which the current program belongs to. The name can be anything. I just gave `main`. You can give whatever you want. Any package name doesn't make any difference here but when we work on huge projects, the package names do matter. Just keep that in mind.

The line 2 - Says import a package called **fmt**. Because we are using a function called **Print** to print some text to output terminal and this Print function belongs to fmt package like how our main function belongs to main package. That's why while using the function we are using `fmt.` to specify that it belongs to that package.

So, just give whatever you want to print inside that Print function wrapped in `" "`.

After writing program, save it.

As we talked before, Go is a compiled language, which means that we have to compile which gives an executable file and then run it. We can do that.

But we can also just directly run it and see the output using the command `go run <file name>`. In our case, it is `go run main.go`.

If you ran same code as above, you should be getting output like this in your terminal.

![Hello world](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jmotrzwueauwx2ktmhis.png)

## Conclusion

That's it for this one. More on Go lang will be coming soon and do follow me to see them. Make sure you like and share if you felt this good.

Also, the resource I learnt from is: [Tech world with nana video](https://youtu.be/yyUHQIec83I) - a video from Tech world with Nana.

Let's connect on: [Twitter](https://twitter.com/VChiranjeeviAK) [LinkedIn](https://www.linkedin.com/in/chiranjeevi-tirunagari/) [Showwcase](https://www.showwcase.com/vchiranjeeviak)