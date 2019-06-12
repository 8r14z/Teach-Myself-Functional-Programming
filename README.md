# Functional Programming
Teach myself functional programming

## What is functional programming? 
"The functional programming paradigm was explicitly created to support a pure functional approach to problem solving. Functional programming is a form of declarative programming. In contrast, most mainstream languages, including object-oriented programming (OOP) languages such as C#, Visual Basic, C++, and Java, were designed to primarily support imperative (procedural) programming."

Even Swift and Objective-C are designed for Imperative Programming. \
All languages that support function pointer can be used to achieve functional programming as well.

> Functional programming is nothing more than using functions to communicate with your co-workers and solve problems.

Different between Imperative and Functional approach
* Imperative: write code that describes in detail the steps that computer must take to accomplish the goal. Create a variable and then change it value (state). Changing value of a variable can make side effects.
```swift
// Sum 2 integers - Imperative approach
let a = 10
let b = 11
let sum = a + b
```
* Functional: compose the problem as a set of functions to be excuted. Define the input and ouput for each function. Self-contained means unit of code or function has its own enviroment and should not know anything about outside, so it can not change any state outside - stateless. So that it won't have any side effects, specially when working in multi-threading enviroment. 
```swift
// Sum 2 integers - Functional approach
let sum = sum(a, b) // Call a func to solve problem
```

### My definition
> The main idea for functional programming is `Mathematical function` that you can not manipulate, just produce an output nothing else, that is something called `stateless` :D Put the same input and always get the same output - no side effects. We don't have to scan whole code file to see whether or not the variable is changed. This is because it's never changed.

### First-class citizens and higher-order functions
In FP, functions are **first-class citizens**. It means that you treat functions like other objects. So that functons can also accept other functions as parameters or return other functions. Functions that accept or return other functions are called **higher-order functions**. The most common higher-order functions in swift are `filter`, `map`, `reduce`.

## Characteristics
| Characteristic | Imperative | Functional |
|----------------|------------|------------|
|Programmer focus|How to perform tasks (algorithms) and how to track changes in state|What information is desired and what transformations are required.|
|Status changes|Important|Non-existent|
|Order of excution|Important|Low importance|
|Primary flow control|Loops, conditionals, function method) calls| Function (method) calls, recursion|
|Pripary manipulation unit|Instances of `struct` or `class`|Functions as first-class objects|

## Advantages
Important keywords are `self-contained` and `stateless`
* Increased readability. This is because each func is designed to solve a specific task and does not reply on any external state.
* Do not repeat works. Increase reusability.
* Easier testing and debugging :D Because funcs can be easly tested in isolation. Do test for seperated unit is much more easier and well-defined.

## Example 
`map`, `compactMap`, `filter`, `reduce` are good examples for implemetation of FP. \
Sort array of integer
#### Imperative approach
```swift
var array = [1,6,12,2,4]
let n = array.count
// Bubble sort
for i in 0..<(n - 1) {
    for j in i+1..<n {
        if array[i] > array[j] {
            let tmp = array[i]
            array[i] = array[j]
            array[j] = tmp
        }
    }
}   
```
* We go through step to step to get the final result.
* State of `array` is changed. The `array` here can be understanded as a property of class.

#### Functional Programming
```swift
let array = [1,6,12,2,4]
let sortedArray = array.sorted()
```
* Just call a function to solve the problem.
* Remain state of `array`.

## Problems
#### 1. Mutable object
Most of objects provided by default are mutable, array, string, dictionary,...
So mutable object can ruin the thing we try to achive in FP, stateless. \
**Solution**: Use immutable objects for doing FP to avoid some mistakes, prevent us from changing. And immutable objects make code safer when dealing with concurrence.
#### 2. Copy, copy, copy a lot
Solving the problem by using `immutable` brings us another problem. We have to make a bunch of copies for an object.

## Combine Functional Programming vs Imperative Programming
We should have the bridge for FP and normally imperative world. Because we have to do something that is not kind of FP actually like write database, update data source for tableview,... In the real world project, it's necessary to combine 2 both of them. So use this `bridge` to update state and keep FP world just be stateless as usual. We can use some data structures to achive this thing. For example, we can use a queue for all updated state requests, add updated request to the queue and the other side of the bidge (live in imperative world) will carry updating stuff.

## Key takeaways
* Instead of thinking about this imperatively, think of it declaratively, i.e. by only thinking about what you want to happen instead of how (step by step). 
* Your declarative (FP) code is easier to read and you can figure out how it works without too much trouble.

## References
* [Functional Programming in 40 minutes](https://www.youtube.com/watch?v=0if71HOyVjY)
* [Introduction to Functional Programming - Raywenderlich](https://www.raywenderlich.com/9222-an-introduction-to-functional-programming-in-swift)


