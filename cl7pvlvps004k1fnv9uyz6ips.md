## Go - Arrays and Slices

## Introduction

Welcome back to the **Part 5** of Go lang series. In **Part 2**: [https://vchiranjeeviak.hashnode.dev/go-conditionals-and-loops](https://vchiranjeeviak.hashnode.dev/go-conditionals-and-loops), we saw what datatypes are and how many types are there in Go. Those are primitive datatypes meaning that they are basic. In this one, let's see about **arrays** and **slices** which are **non-primitive datatypes** in Go.

## Non-Primitive datatypes

A datatype which is a group of variables of any **primitive** or **non-primitive** datatypes is called **non-primitive** datatype. Revisit this line after reading below **non-primitive** datatypes. You will get a clear picture of this line then.

There are **4** non-primitive datatypes in Go. They are:

1. Arrays.
2. Slices.
3. Maps.
4. Structs.

Let's see **maps** and **structs** in the next article.

### 1. Arrays

An **array** is a collection or group of values where each value belongs to the **same** type. In other words, all variables or items present in an array should be of same datatype.

An array in Go has a **fixed size** which is specified during the time of declaration or initialisation. And, its size is fixed can't be modified during program execution.

#### Program to illustrate declaring and initialising arrays
```go
package main

import "fmt"

func main() {
    var arr1 [10]int // Declaring an array of size 10
    arr2 := [10]int{1, 2, 3, 4, 5} // Initialising an array of size 10 with {1, 2, 3, 4, 5} values.
    fmt.Printf("This is array 1: %v", arr1)
    fmt.Printf("This is array 2: %v", arr2)
}
```
**Output**:
![Output](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jf6qod1gyfodg7764gxq.png)

Since, we haven't given any values in arr1, it is taking all values as default values, which is 0 in case of int. In arr2, the first 5 values are given by us and remaining 5 are default values.

#### Program to add an item at 6th position in an array of size 10

We can specify a particular position of an array using **index** (`[]`) operator. Inside these `[]`, we give the index number. `Index number = Position - 1`. So, to specify 6th position of an array, we use `[5]` according to above expression. We use this index operator right beside the array name.

```go
package main

import "fmt"

func main() {
    arr := [10]int{1, 2, 3, 4, 5} // Initialising array
    fmt.Println(arr) 
    arr[5] = 6 // Adding an item at position 6, a.k.a index 5
    fmt.Println(arr)
}
```
**Output**:

![Output](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/hxltfec1u2kzxghs13o4.png)

A negative point of an array is that its size is fixed and cannot grow or shrink automatically depending on the situation. For example, in the above array of size 10, you can't add a 11th item into it. It throws an error. So, we need to know the maximum length of the array that we require in that program.

What if it is not possible to know the maximum length of array in prior? What if we want our array to grow or shrink according to the needs? That is where **slices** come in handy.

### 2. Slices

A **slice** is very similar to an array. The only difference between a slice and an array is that there is **no fixed size** for a slice. Its size can grow or shrink depending on the situation.

Declaration or initialisation of a slice is similar to an array except that we don't specify any size like we do in the case of an array.

#### Program to declare and initialise a slice
```go
package main

import "fmt"

func main() {
    var slice1 []string // Declaring a slice of type string
    slice2 := []string{"chiranjeevi", "golang"}
    fmt.Println(slice1)
    fmt.Println(slice2)
}
```
**Output**:

![Output](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/n896q4g76t7y7oh7g0v6.png)

#### Program to add a new string at the end of a slice

We can't add a new item at a specific position of a slice like we did in array. We can only add a new item at the end of the slice. We do that using a function called `append`. This is a default function. It takes 2 arguments. One is the slice, and other one is the item we want to add. This function returns a new slice with new item added to the old slice.
```go
package main

import "fmt"

func main() {
    slice1 := []string{"chiranjeevi", "golang"}
    fmt.Println(slice1)
    slice1 = append(slice1, "devops") // Assigning it to the old slice again
    // Bcoz the append function only return new slice
    // It doesn't change the old slice.
    fmt.Println(slice1)
}
```
**Output**:

![Output](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/b1jk1uz6uxk5rlj5nl0t.png)

### Updating value at a position in array and slice

We can update an already present value in an array and a slice. Specify that position using index operator and assign a value to it. We did this while adding item to an array. There we assigned item to a position where there is nothing assigned already. So, it is adding an element. If we try to do the same when there is an item present there already, it is updating an item.

#### Program to update value at a position in array

```go

package main

import "fmt"

func main() {
    arr := [5]int{1, 2, 3, 4, 5}
    fmt.Println(arr)
    arr[3] = 400 // Updating value of 4 (index 3) to 400
    fmt.Println(arr)
    // arr[5] = 500 //Trying to assign value to position not present
    // This throws an error if uncommented above line.
}
```
**Output**

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/j4ws2yv6un5ihbxgvtb2.png)

**Output if uncommented the error line**

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/x6icndmhv3sw0wbjcvu6.png)


We didn't use index operator while adding an item to a slice. It is because, we can't access a position which is not part of an array or slice. In case of an array, we know the size of it while declaring, so we can add any item as far as we are adding to a position which is present in the array. But, when it comes to slice, we don't know the size that a slice currently possessing. If we try to update or access a position which is not already present in the array or slice, it throws an error. We can get size or current length of an array or a slice using **len** function.

#### Program to update a value in slice

```go
package main

import "fmt"

func updateSlice(slc []int, pos int, val int) []int {
    if (pos >= len(slc)) {
        fmt.Println("Slice index out of bound")
    } else {
        slc[pos] = val
    }
    return slc
}

func main() {
    slc := []int{1, 2, 3, 4}
    fmt.Println(slc)
    slc = updateSlice(slc, 1, 500)
    fmt.Println(slc)
    slc = updateSlice(slc, 5, 1000)
    fmt.Println(slc)
}
```
**Output**:

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ews7a17uylug1tjtdbrg.png)

### Function - arguments and return type

We discussed about **functions** in the first article of this series, check it out if you missed it: [https://dev.to/vchiranjeeviak/go-hello-world-3ino](https://dev.to/vchiranjeeviak/go-hello-world-3ino). In that one, we saw what function header, arguments and body are. Now, let's see how we actually declare arguments from the above code example.

We declare arguments inside a pair of parenthesis. For each argument, we have to give a name with which we want to call it inside the function succeeded by its datatype.

In above example, we need the slice, the position at which we are updating and the value with which we want to update as arguments. So, we need to declare 3 arguments in total. First one is of type slice with integers, so we declare it as `[]int` preceded by the name. Second is the position which is an integer, so `int` preceded by its name. Third is the value which is also an integer, so `int` preceded by its name. Hence, it boiled down to `(slc []int, pos int, val int)`. That is why when we are calling the function, we used `updateSlice(slc, 1, 500)`. The number of arguments and order should be maintained as it is in the declaration.

Also, there is something after these arguments outside parenthesis. That is called the **return type** of the function. It means that the value which is returned by the function has that type. In our example, we are returning a int slice, so we gave `[]int` as return type. Where does it return to? The value is returned to the place where the function is called. We are calling it inside main function, so it returns the value there. That is the reason why we are re-assigning it to the original slice there.

## Conclusion

That's it for this one. In the next article, lets cover maps and structs.

More on Go lang will be coming soon and do follow me to see them. Make sure you like and share if you felt this good.

Let's connect on: [Twitter](https://twitter.com/VChiranjeeviAK) [LinkedIn](https://www.linkedin.com/in/chiranjeevi-tirunagari/) [Showwcase](https://www.showwcase.com/vchiranjeeviak)