## Go - Conditionals and Loops

## Introduction

Welcome back to this **part 4** of the **Go lang** series. In **part 3**, we covered pointers and user input. Check it out: [https://vchiranjeeviak.hashnode.dev/go-pointers-user-input](https://vchiranjeeviak.hashnode.dev/go-pointers-user-input) if you missed it. In this one let's see conditionals and loops in go.

## Conditionals

Generally, programming is all about writing some logic in the form of code so that machine can understand. One of the most vital part of writing logic is to deal with some conditions. We may want our machine to react differently in different situations. In those cases, we specify those situations as conditions and write how machine needs to work in those situations. We do this using conditionals.

We can write conditions in **2** ways. They are:
1. **if-else**.
2. **switch-case**.


### 1. if-else

- We write the code which we want to be executed if a specific condition is met is written inside **if** block along with a condition.
- The code which we want to get executed when that condition is not met is written inside **else** block.

The syntax to use **if-else** is:
```go
if <condition> {
    // code which needs to be executed if above condition is met
} else {
    // code which needs to be executed when above condition is not met
}
```

#### Condition

A condition in an **if-else** syntax can be any combination of **logical** operation and **relational** operation.

There are many types of operators in Go lang and **logical**, **relational** operators are two of them.

Before going into it, there is something we need to know about operands. An **operand** is a variable or value on which the operator performs the operation.

#### Logical operators

An operation done using logical operators is called logical operation. There are **3** logical operators. They are **AND (&&)**, **OR (||)** and **NOT (!)**. These logical operators are applied on operands which can be evaluated to a boolean value (true or false). Both **AND** and **OR** are binary operators (refer: **Part 3** for this) take two operands on either sides of the operator. **AND** evaluates **true** only when both the operands are true or **false** in any other case. **OR** evaluates **true** when at least one of them is true or **false** in any other case.

| operand 1 | operator | operand 2| result |
|---|---|---|---|
| True | AND | True | True |
| True | AND | False | False |
| False | AND | True | False |
| False | AND | False | False |
| True | OR | True | True |
| True | OR | False | True |
| False | OR | True | True |
| False | OR | False | False |

**NOT** takes only one of the boolean values and gives back the other one.

| Operator | Operand | Result |
|---|---|---|
| NOT | True | False |
| NOT | False | True |

Okay.... This is fine, but where do we get these **True** or **False** from?

That's where **relational** operators come into picture. We usually give an expression which contains relational operators and which is evaluated to one of the boolean values.

#### Relational operators

**Relational** operators are operators which check if the given relationship between two operands is true or not. Let's say, if there is an expression which says "5 is greater than 6", it is giving relationship between two operands and it is obviously false in this case.

There are **6** relational operators. They are:

| Operand 1 | Operator | Operand 2 | Result |
|---|---|---|---|
| 5 | == (**equals to**) | 6 | False |
| 5 | != (**not equals to**) | 6 | True |
| 5 | > (**greater than**) | 6 | False |
| 5 | >= (**greater than or equals to**) | 6 | False |
| 5 | < (**less than**) | 6 | True |
| 5 | <= (**less than or equals to**) | 6 | True |

#### Program to illustrate if-else

We are writing a program to check if the user given integer is in the range **[0, 100)**. Depending on the input, we will print a unique message accordingly. This representation says that the number should be between 0 and 100, and can be equal to 0 but not equal to 100. One of our relational expression should be `our number >= 0` and other one should be `our number < 100`. And, we need to combine both of them with an `AND (&&)` because both of them are necessary checks.

```go
package main

import "fmt"

func main() {

    var someNumber int

    fmt.Println("Enter an integer:")

    fmt.Scan(&someNumber)

    if ((someNumber >= 0) && (someNumber < 100)) { // Condition
        fmt.Println("In our range") // Comes here only when the condition is true
    } else {
        fmt.Println("Not in our range") // Comes here only when the condition is false
    }
} 
```

### switch-case

I don't want to complicate **switch-case** because it is as simple as a real switch board. We can design a digital switch board just like how we have a unique switch for fan, light, bulb etc..

Syntax for **switch-case**:
```go
switch (<variable/value>) {
    case <some value>:
        // code
    case <some other value>:
        // code
    default:
        // code
}
```
#### Program to illustrate switch-case

This example is enough to understand **switch-case**. We take a string input from user. If it is a "fan" given as input, we print "switched fan on". If the input is "light", we print "switched light on". If it is anything else, we print "Press the correct switch".

```go
package main

import "fmt"

func main() {
    
    var userInput string

    fmt.Println("Give input:")
    fmt.Scan(&userInput)

    switch (userInput) {
        case "fan":
            fmt.Println("switched fan on")
        case "light":
            fmt.Println("switched light on")
        default:
            fmt.Println("Press the correct switch")
    }
}
```
Note: I am not giving outputs in this article. Please run by yourself and comment if you find any errors in code.

- We can write the same code using **if-else** also. Try doing that yourself and comment if you faced any difficulty. I know this is basic stuff if you are coming from other programming language background, but this can be challenging for someone who started coding.

## Loops

There might be some situations where we want to run some block of code multiple times. And, the number of times can be decided by a condition or an event. An example situation can be "Taking a string input from user until it is `special`" or "Printing numbers from `1 to 100`, etc. Wherever we see repetition of task, we can apply loops there.

Unlike many famous programming languages, Go has only one type of loop, which is **for** loop. The syntax of **for** loop is:
```go
for <condition> {
    // repetitive task
}
```
Until the condition is satisfied (evaluates to True), the code written inside keeps running again and again.

Whenever we think of conditions, we should remember logical and relational operators. Because, most of the times, conditions contain only them.

### Program to take user input until we get `special` as input

Let's declare a variable to store input, and write a Scan statement inside for loop. But, we have to think of condition that satisfies our situation. We need to stop this loop only when we receive `special`. So, we need to make it run until the input is not `special`. And let us also print a line after loop to show that the program control came out of it.

```go
package main

import "fmt"

func main() {
    var userInput string

    for userInput != "special" {
        fmt.Scan(&userInput)
    }
    fmt.Print("Outside loop")
}
```
This will keep running until you give `special` as input.

### Program to print numbers in [1, 100) range

We can have a variable initialised to `1`. When gone inside loop, print the variable, update it by increasing its value by 1 every time. We can stop when our variable value is greater than 99 or equal to 100.
```go
package main

import "fmt"

func main(){
    number := 1
    for number <= 99 {
        fmt.Println(number)
        number++
    }
}
```
`++` is a unary operator which increases the value of the variable by `1`.

- Every time we go inside a loop, we call it an **iteration**. This is an important terminology to know for next topics.

We are initialising a variable outside loop, writing a condition on it, and updating its value inside loop just print its value in the loop. It can become tough if the code in file is huge to keep track of this particular variable. So, it is better handle this kind of variables inside `for` parameters. The syntax is:

```go
for (<initialisation>; <condition>; <updation>) {
    //code
} 
```

Lets see how above code can be converted into this method.

```go
package main

import "fmt"

func main() {
    for (number := 1; number <= 99; number++) {
        fmt.Println(number)
    }
}
```
This can be much more readable and cleaner.

### Infinite loops

An **infinite loop** is a loop which doesn't stop running and runs forever either until the memory is full or power is disconnected. Most modern programming languages and their run time environments or compilers handle this carefully without letting your system get hanged. Yeah, that's what happens when your RAM is full of apps. How can we invoke an infinite loop? It is very simple to do. We just need to give a condition (check syntax of loop) in loop which is never going to false. One such condition can be `0 > 10`. This condition will always be false no matter how the variables in the program change. Or we can just give `true` (boolean) as condition as anyway any condition we give at last is evaluated to either true or false.

#### Program to print 1 infinite times

```go
package main

import "fmt"

func main() {
    for true {
        fmt.Println(1)
    }
}
```
This might give a warning that `true` is not required to provide as if we don't give anything, it considers as `true`.
So, a corrected perfect program can be:
```go
package main

import "fmt"

func main() {
    for {
        fmt.Println(1)
    }
}
```
I encourage you to run this and see how an infinite loop prints if you are a beginner. If you are not a beginner, I am sure that you must have seen this a lot of times.

- If we had given `false` instead of `true`, the loop doesn't even run once.

Can we run finite loops without giving a condition? The answer is partially yes. Because, we still give a condition but not at the usual place we give. We provide a condition when to stop running inside the loop but not outside loop. We do this using `break` and `continue`.

### Break and Continue

**break** and **continue** are two keywords in most programming languages and so in Go. When a loop is running, if we want to stop running that loop at a particular iteration and not run further, we use `break`. When a loop is running, if we want to skip one particular iteration and run remaining iterations normally, we use continue.

#### Program to print [1, 100) using break

```go
package main

import "fmt"

func main(){
    number := 1
    for {
        if (number == 100) {
            break
        }
        fmt.Println(number)
        number++
    }
}
```
This program also prints 1, 99. But the difference is in how we wrote the loop and base condition.

#### Program to print [1, 100) but don't print 10

```go
package main

import "fmt"

func main(){
    number := 1
    for {
        if (number == 10) {
            continue
        }
        if (number == 100) {
            break
        }
        fmt.Println(number)
        number++
    }
}
```

- If you think this will print 1 to 99, then you are wrong. Why? Because, when the number is `10`, it goes into `if` block and executes `continue`, which will take it directly out of loop and enters back into the loop from top. It will never execute `number++` line, which means the number value is not going to move from 10 and will keep rotating for loop which makes it an infinite loop.

To make it work as we intend to, we need to make a small change:

```go
package main

import "fmt"

func main(){
    number := 1
    for {
        if (number == 10) {
            continue
            number++ // new added line
        }
        if (number == 100) {
            break
        }
        fmt.Println(number)
        number++
    }
}
```
- This newly added line makes sure that the number value is increasing even when it hits `continue`.

## Conclusion

That's it for this one... Like and share this if you loved it. Follow me for the future content.

Let's connect on: [Twitter](https://twitter.com/VChiranjeeviAK) [LinkedIn](https://www.linkedin.com/in/chiranjeevi-tirunagari/) [Showwcase](https://www.showwcase.com/vchiranjeeviak)
