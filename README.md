# Functional Programming
Teach my self functional programming

## What is functional programming? 
"The functional programming paradigm was explicitly created to support a pure functional approach to problem solving. Functional programming is a form of declarative programming. In contrast, most mainstream languages, including object-oriented programming (OOP) languages such as C#, Visual Basic, C++, and Java, were designed to primarily support imperative (procedural) programming."

Even Swift and Objective-C are designed for Imperative Programming. \
All languages that support function pointer can be used to achieve functional programming as well.

> Functional programming is nothing more than using functions to communicate with your co-workers and solve problems.

Different between Imperative and Functional approach
* Imperative: write code that describes in detail the steps that computer must take to accomplish the goal
```swift
// Sum 2 integers - Imperative approach
let a = 10
let b = 11
let sum = a + b
```
* Functional: compose the problem as a set of functions to be excuted. Define the input and ouput for each function. 
```swift
// Sum 2 integers - Functional approach
let sum = sum(a, b) // Call a func to solve problem
```

### My definition
> The main idea for functional programming is `Mathematical function` that you can not manipulate, just produce an output nothing else, that is something called `stateless` :D Put the same input and always get the same output - no side effects. We don't have to scan whole code file to see whether or not the variable is changed. This is because it's never changed.
### Problems
#### 1. Mutable object
Most of objects provided by default are mutable, array, string, dictionary,...
So mutable object can ruin the thing we tryna to achive in FP, stateless. \
**Solution**: Use immutable objects for doing FP to avoid some mistakes, prevent us from changing. And immutable objects make code safer when dealing with concurrence.
#### 2. Copy
Solving the problem by using immutable brings us another problem. We have to make a bunch of copies for an object.


> We have to have the bridge for fp vs normally imperative programming

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

## References
* [Functional Programming in 40 minutes](https://www.youtube.com/watch?v=0if71HOyVjY)
* [Introduction to Functional Programming - Raywenderlich](https://www.raywenderlich.com/9222-an-introduction-to-functional-programming-in-swift)


