
# Functional Programming
Teach me functional programming

## What is functional programming? 
"The functional programming paradigm was explicitly created to support a pure functional approach to problem solving. Functional programming is a form of declarative programming. In contrast, most mainstream languages, including object-oriented programming (OOP) languages such as C#, Visual Basic, C++, and Java, were designed to primarily support imperative (procedural) programming."
Even Swift and Objective-C are designed for Imperative Programming. \
All languages that support function pointer can be used to achieve functional programming as well.
> Functional programming is nothing more than using functions to communicate with your co-workers and solve problems.
Different between Imperative and Functional approach
* Imperative: write code that describes in detail the steps that a computer must take to accomplish the goal. Create a variable and then change its value (state). Changing the value of a variable can make side effects.
```swift
// Sum 2 integers — Imperative approach
let a = 10
let b = 11
let sum = a + b
```
* Functional: compose the problem as a set of functions to be executed. Define the input and output for each function. Self-contained means a unit of code or function has its environment and should not know anything about outside, so it can not change any state outside — stateless. So that it won’t have any side effects, especially when working in a multi-threading environment. 
```swift
// Sum 2 integers — Functional approach
let sum = sum(a, b)
```
### My definition
> The main idea for functional programming is `Mathematical function` that you can not manipulate. That is something called `stateless` :D Put the same input and always get the same output — no side effects. We don’t have to scan the whole code file to see whether or not the variable is changed. This is because it’s never changed.

### First-class citizens and higher-order functions
In FP, functions are **first-class citizens**. It means that you treat functions like other objects. So that functions can also accept other functions as parameters or return other functions. Functions that accept or return other functions are called **higher-order functions**. The most common higher-order functions in Swift are `filter`, `map`, `reduce`.

### Concepts in FP
* **Partial functions**: allow you to encapsulate one within another.
```swift
func intersection(with set: Set<Int>) -> (Set<Int>) -> Set<Int> {
    return { integers in
        integers.intersection(set)
    }
}

let findIntersection = intersection(with: [1,2,3])
let intersection = findIntersection([1,3,4])
```
* **Pure functions**: the main idea for FP — same as `Mathematical functions`. This stateless approach helps you write good unit tests for functions. The same input produces the same output; it’s easy to detect error in implementation when having any changes. 
* **Recursion**: in functional languages, recursion replaces many of the looping constructs that you use in imperative languages. Keep in mind that recursive functions have extra memory usage and runtime overhead.

## Characteristics
| Characteristic | Imperative | Functional |
|----------------|------------|------------|
|Programmer focus|How to perform tasks (algorithms) and how to track changes in state|What information is desired and what transformations are required.|
|Status changes|Important|Non-existent|
|Order of excution|Important|Low importance|
|Primary flow control|Loops, conditionals, function method) calls| Function (method) calls, recursion|
|Pripary manipulation unit|Instances of `struct` or `class`|Functions as first-class objects|

## Advantages
Important keywords are `self-contained` and `stateless`.
* Increased readability. This is because each function is designed to solve a specific task and does not rely on any external state.
* Do not repeat works. Increase reusability.
* Easier testing and debugging :D Because functions can be easily tested in isolation. Do test for the separated units are much easier and well-defined.

## Example 
`map`, `compactMap`, `filter`, `reduce` are good examples for the implementation of FP. \
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
* State of `array` is changed. The `array` here can be understood as a property of a class.
#### Functional Programming
```swift
let array = [1,6,12,2,4]
let sortedArray = array.sorted()
```
* Just call a function to solve the problem.
* Remain state of `array`.

## Problems
#### 1. Mutable object
Most of objects provided by default are mutable, array, string, dictionary,…
So mutable objects can ruin the thing we try to achieve in FP, stateless. \
**Solution**: Use immutable objects for doing FP to avoid some mistakes, prevent us from changing. Immutable objects make code safer when dealing with concurrency.
#### 2. Copy, copy, copy a lot
Solving the problem by using `immutable` brings us another problem. We have to make a bunch of copies for an object.

## Combine Functional Programming vs Imperative Programming
We should have the bridge for FP and normally imperative world. Because we have to do something that is not kind of FP actually like write database, update data source for table views,… In the real world project, it’s necessary to combine 2 of them. So use this `bridge` to update state and keep FP world just be stateless as usual. We can use some data structures to achieve this thing. For example, we can use a queue for all updated state requests, add updated request to the queue and the other side of the bridge (live in imperative world) will carry updating stuff.

The root implementation of any functional method actually has the imperative look. It will be great if we can combine both together. Following is how `filter` is implemented in Swift open source at `https://github.com/apple/swift/blob/master/stdlib/public/core/Sequence.swift`.
```swift
@_transparent
  public func _filter(
    _ isIncluded: (Element) throws -> Bool
  ) rethrows -> [Element] {

    var result = ContiguousArray<Element>()

    var iterator = self.makeIterator()

    while let element = iterator.next() {
      if try isIncluded(element) {
        result.append(element)
      }
    }

    return Array(result)
  }
```
It is quite the same as the imperative approach, isn't it? :D YEEEES, it is. It goes step by step. But it's still stateless, persistent and call `isIncluded` function to solve the problem. It should use recursion in this case, but anyway Swift is not a pure functional language so it's ok :D
```swift
func filter(_ isIncluded: (Element) -> Bool) -> [Element] {

    guard let first = first else {
        return []
    }
    
    if isIncluded(first) {
        return [first] + self[1..<endIndex].filter(isIncluded)
    } else {
        return self[1..<endIndex].filter(isIncluded)
    }
}
```

## Key takeaways
* Instead of thinking about this imperatively, think of it declaratively, i.e. by only thinking about what you want to happen instead of how (step by step). 
* Your declarative (FP) code is easier to read, and you can figure out how it works without too much trouble.
* Swift is not purely a functional language, but it does combine multiple programming paradigms. A great place to start working with FP techniques is in your Model layer and anywhere that your app’s business logic appears. You’ve seen how easy it is to create discrete tests for that logic.

## References
* [Functional Programming in 40 minutes](https://www.youtube.com/watch?v=0if71HOyVjY)
* [Introduction to Functional Programming - Raywenderlich](https://www.raywenderlich.com/9222-an-introduction-to-functional-programming-in-swift)
* [Swift Functional Programming Tutorial](https://www.raywenderlich.com/2273-swift-functional-programming-tutorial)
* [Swift and the Legacy of Functional Programming](https://academy.realm.io/posts/tryswift-rob-napier-swift-legacy-functional-programming/)
