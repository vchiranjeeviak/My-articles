## Go - Variables, Constants and Datatypes

## Introduction

This is the part **2** of the **Go lang** series. Do checkout the first one if you missed it. Here is the link to it: [Part 1](https://vchiranjeeviak.hashnode.dev/go-hello-world). We discussed Pros and characteristics of Go, Functions in general, Starting point of Go programs (main function), Hello world program in that article.

In this one, let's go through variables, constants and datatypes in Go.

## Context

Consider a situation where in our program, we are using a sentence again and again in multiple lines. We are writing/typing the whole sentence every time we are using it. It is a repetitive and hectic task. And imagine writing a spelling mistake in one place. It would be difficult to identify that place. Or imagine we want to change that sentence a bit, it would be required to go and change every where.

Instead of hardcoding the sentence every where, what if we can write the sentence once and use some shortcut to fill it every where else. Let's say our sentence is **"Fear of missing out"**. And we need to print this sentence 5 times to the terminal. This is how program looks like:
```go
package main

import "fmt"

func main() {
    fmt.Println("Fear of missing out")
    fmt.Println("Fear of missing out")
    fmt.Println("Fear of missing out")
    fmt.Println("Fear of missing out")
    fmt.Println("Fear of missing out")
}
```
**Note**: In our previous article, we saw **Print** function which prints to the terminal. But here we are using a different function from same package (fmt) which is **Println**. The difference is that **Print** prints every time in the same line, which means in the above example 5 **"Fear of missing out"**s would come in same line side by side. **Println** prints in a new line every time. Try running both yourselves.

The above would print **"Fear of missing out"** 5 times.

### Variables

Instead of writing it every where we want, it would be nice if we can just write **"FOMO"** and it automatically considers it as **"Fear of missing out"**.

This is where we use variables. In the above example, **"FOMO"** is a variable and **"Fear of missing out"** is its value.

The syntax to initialise a variable is `var <variable name> = <value>`.

The above program can be changed into:

```go
package main

import "fmt"

func main() {
    var FOMO = "Fear of missing out"

    fmt.Println(FOMO)
    fmt.Println(FOMO)
    fmt.Println(FOMO)
    fmt.Println(FOMO)
    fmt.Println(FOMO)
}
```
If we are hardcoding like in our first program, we wrap what we want to print inside `" "`. If we are using variables inside the print function we don't wrap them inside `" "`.

### Constants

**Variables** are good to use when the data we are storing is not fixed. For example, we are storing a value whose value is going to be changed during the program execution, we store them in variables because variables value can be changed/varied.

**Constants** are good to use when the data we are storing should not be changed during program execution and should be fixed. For example, we are writing a program to find radius of a circle for which we need **pie** value which is **3.14**. This value of pie never changes and should not change especially while program is running. We store such values as **constants**. Syntax to store constants is `const <constant name> = <value>`.

Program to find area of a circle with radius 5 units:

```go
package main

import "fmt"

func main() {
    var radius = 5
    const pie = 3.14

    var area = pie * radius * radius
    fmt.Printf("The area is %v square units", area)
}
``` 
This prints **The area is 78.5 square units**

Here, we are using another function to print something to terminal which is **Printf**. It means that print formatted. We are embedding some variable's value into our string. We can do this same thing with **Println** or **Print** also in below way.

```go
Println("The area is ", area, " square units")
```

But using formatted way looks little cleaner. Also, we can embed any number of variables in similar way. Wherever we want to insert, put a `%v` there and give the variable names at the end after `,` in the order you want them to appear.

## Datatypes

In above examples, we are storing text form of data in variables and constants. Apart from that we can store other forms of data as well and we have specific names to them.

All these different types of data that can be stored are called **datatypes**.

**Datatypes** in **Go** are:

### 1. Boolean

- Keyword for boolean = `bool`
- Possible values = `true` or `false`

### 2. String

- Keyword for string = `string`
- Possible values = any possible combination of all characters
- Examples = `"a"`, `"hello"`, `"flksflkjsf"`

### 3. Integer

- Keyword for integer = `int`
- Possible values = `-2^63` to `2^63-1`
- Examples = `-42535`, `0`, `353564`

### 4. Float

- Keyword for float = `float32`, `float64`
- Examples = `-234.254`, `575.33`

### 5. Complex

- Keyword for complex = `complex64`, `complex128`
- Examples = `-5 + 6i`, `7 - 2i`

In float and complex types there are 32, 64, 128 numbers in their types. It denotes the number of bits it takes to store the binary format of their values.

`int` has also other forms like `int8`, `int16`, `int32`, `int64`. But `byte` is another name for `int8` and `rune` is another name for `int32`.

These are the types of data that we can store in variables and constants in **Go**.

Let's write a program to initialise few variables and get their datatypes programatically.

```go
package main

import "fmt"

func main() {
    var var1 = false
    var var2 = 13
    var var3 = -234.11
    var var4 = "Chiru"

    fmt.Printf("var1 is %T", var1)
    fmt.Printf("var2 is %T", var2)
    fmt.Printf("var3 is %T", var3)
    fmt.Printf("var4 is %T", var4)
}
```
When we use `%v`, we used to get the value of variables. When we use `%T`, we get the datatypes of those variables.

## Declaration Vs Initialisation

If we carefully observe, the word we used above examples to store data in variables is **initialisation**. It means that we are creating a variable and giving some value to it at the same time.

We can also create variables without giving value to them at that time. This is called **declaring** a variable. But, we have to give some value to it before the program ends and use it somewhere, else **Go** compiler gives error saying that variable is not used.

### Why don't we initialise instead of declaring at all times?

In any program, we initialise or declare all the variable we need at the top of the function or program. This we do to keep the code clean and maintainable. But we don't always have data available to initialise all the variables. If we want to get some data from a third-party API or from user as input while program is running and store it in a variable, we can't initialise such variables. But, we need some variables reserved to store such data at the top of function. This is why we declare variables and store value inside them later.

Let's consider this example where in a program, the user which runs it gives it their name and the program greets the user with their name.

In this situation, we can't hardcode the user name because we don't know the user which runs it. So, we need to take input from user and store it and greet them. To take input and store it, we need some variable reserved for it. Let's not take user input but just emulate it.

But to declare a variable, we need to specify the type of data that variable is going to receive further in the program. Otherwise, the compiler doesn't accept declaration.

```go
package main

import "fmt"

func main() {
    var userName string // variable declaration with type
    
    fmt.Println("Enter your name:")
    // Let's assume we take input and it is "Chiranjeevi"
    userName = "Chiranjeevi"

    fmt.Println("Welcome, %v", userName)
}
```

## Walrus operator

We can initialise variables without `var` keyword. We can do that using **walrus** operator. The walrus operator looks like **:=** .

Let's initialise a variable using walrus operator and print it.

```go
package main

import "fmt"

func main() {
    number := 20

    fmt.Print(number)
}
```

**Note**: Constants can't be initialised using walrus operator.

## Conclusion

That's it for this one. Next article covers pointers, user input, arrays and slices.

Do follow me to see them. Make sure you like and share if you felt this good.

Let's connect on: [Twitter](https://twitter.com/VChiranjeeviAK) [LinkedIn](https://www.linkedin.com/in/chiranjeevi-tirunagari/) [Showwcase](https://www.showwcase.com/vchiranjeeviak)