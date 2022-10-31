# Go - Maps and Structs

## Introduction

Welcome back to the Part - 6 of the Go series. In the last one, we saw two of the non-primitive datatypes (1. Arrays, 2. Slices) in Go. Do check it out if you missed it: [https://vchiranjeeviak.hashnode.dev/go-arrays-and-slices](https://vchiranjeeviak.hashnode.dev/go-arrays-and-slices). In this one, let's see about **3. Maps** and **4. Structs**.

## 3. Maps

We saw how arrays and slices are a collection of other primitive datatype items. Maps are also a collection of items, but here the items are not just of primitive types, they are `(key, value)` pairs. And a key can be any primitive datatype item and same with value. But, the types should be consistent for all `(key, value)` pairs in the map.

**Note**: A **key** should be unique for each pair. In other words, no two pairs should have same **key**. By this assumption, we can uniquely identify a pair using its **key**.

### Declare and Initialising a map

We use `make` function to create a map. `map[primitive]primitive` is a datatype. We are basically trying to say is that "make a map of this type".

#### Program to declare and initialise a map

```go
package main

import "fmt"

func main() {
        // Declaring a map
	var map1 map[int]string // A map in which key is of int type, value is of string type
        // Initialising an empty map
	var map2 = make(map[string]int) // An empty map in which key is of string type, value is of int type
        // Initialising a non-empty map
	map3 := map[float64]int{ // A map in which key is of float type, value is of int type
		0.5: 0,
		1.5: 1,
		2.5: 2,
	}
	fmt.Println(map1)
	fmt.Println(map2)
	fmt.Println(map3)
}
```

**Output**:

![Output 1](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/96t1df2sy7ot5emtrpld.png)

Check the type of the map on your own using `%T` in `Printf` and you will realise why we are using that particular notation to create a map.

### Adding and deleting items in a map

Adding a `(key, value)` pair into a map is straight forward. Using index operator, we give the new `key` into index and assign new `value` to it. It automatically create a new pair.

For deleting a pair, we use `delete` function which takes the `map` and `key` as input and deletes the pair with that particular key.

#### Program to add and delete a pair in map

```go
package main

import "fmt"

func main() {
    // Initialising a map
	map1 := map[int]string{ 
		1: "string1",
		2: "string2",
	}
	fmt.Println("Map initially = ", map1)
    // Adding a new pair
	map1[3] = "string3" 
	fmt.Println("Map after adding (3, string3) = ", map1)
    // Deleting a pair with key 1
	delete(map1, 1)
	fmt.Println("Map after deleting pair with key 1 = ", map1)
}
```

**Output**:

![Output 2](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/gy3ziin15a4192slhht3.png)

## 4. Structs

Struct is a bit different from other non-primitive datatypes. It is not a collection of something like arrays, slices or maps. A **struct** is a complex datatype which is a fusion of other datatypes. It is a user-defined datatype which is a combination of other datatypes.

### Defining a struct type

As I said earlier, it is a user-defined datatype. So, we need to define this type using the syntax `type <name> struct { }`. Inside this, we give other datatypes with their names using syntax `<name> <datatype>`. This is how we create the fusion.

#### Program to declare and initialise a struct type and create a variable of that type and print it

```go
package main

import "fmt"

// Creating a struct1 type struct
type struct1 struct {
	nestedVar1 string
	nestedVar2 int
}

func main() {
	// Declaring a variable of type struct1
	var structVar1 struct1
	// Initialising a variable of type struct2
	structVar2 := struct1{"string1", 10}
	// Assigning value to structVar1
	structVar1 = struct1{"string2", 20}
	// Printing both
	fmt.Println(structVar1)
	fmt.Println(structVar2)
}
```
**Output**:

![Output 3](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/46bq3xfapylrqjiyo3c1.png)

### Accessing nested variable in a struct

In the above case, how can we access the string part of the struct1? We can do that using `.` . `structname.nestedVar` gives that particular value.

#### Program to create a struct variable and accessing a nested variable

```go
package main

import "fmt"

// Creating a struct1 type struct
type struct1 struct {
	nestedVar1 string
	nestedVar2 int
}

func main() {
	//Initialising a struct1 type variable
	structVar1 := struct1{"string2", 20}
	// Printing nested variable
	fmt.Println(structVar1.nestedVar1)
}
```

**Output**:

![Output 4](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/na3bmhtlfhgmeis598pj.png)

## Conclusion

That's it for this one. In the next part, lets see the use-cases of each of these non-primitive datatypes. Also, lets cover iterating through each of these datatypes which is very important.

More on Go lang will be coming soon and do follow me to see them. Make sure you like and share if you felt this good.

Let's connect on: [Twitter](https://twitter.com/VChiranjeeviAK) [LinkedIn](https://www.linkedin.com/in/chiranjeevi-tirunagari/) [Showwcase](https://www.showwcase.com/vchiranjeeviak)