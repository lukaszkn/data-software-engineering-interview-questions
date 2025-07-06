# Kotlin Basics
Basic syntax, functions, variables, classes, conditional expressions, loops, ranges, collections, nullable values

* [### Program entry point](#Program-entry-point)
* [### Package definition and imports](#Package-definition-and-imports)
* [### Print to the standard output](#Print-to-the-standard-output)
* [### Read from the standard input](#Read-from-the-standard-input)
* [### Functions declaration](#Functions-declaration)
* [### Unit Functions (Functions with no return value)](#Unit-Functions-Functions-with-no-return-value)
* [### Single-expression functions](#Single-expression-functions)
* [### Default and named arguments](#Default-and-named-arguments)
* [### Function with varargs (variable number of arguments)](#Function-with-varargs-variable-number-of-arguments)
* [### Higher-order functions](#Higher-order-functions)
* [### Anonymous (lambda) functions](#Anonymous-lambda-functions)
* [### Extension functions](#Extension-functions)
* [### Variables﻿](#Variables)
* [### Type inference](#Type-inference)
* [### Declaring variables without initialization](#Declaring-variables-without-initialization)
* [### Nullable variables](#Nullable-variables)
* [### Constant variables](#Constant-variables)
* [### Creating classes and instances](#Creating-classes-and-instances)
* [### Primary constructor](#Primary-constructor)
* [### Secondary constructor](#Secondary-constructor)
* [### Initializer block `init`](#Initializer-block-init)
* [### Properties with custom getters and setters](#Properties-with-custom-getters-and-setters)
* [### Inheritance](#Inheritance)
* [### Data classes](#Data-classes)
* [### Comments﻿](#Comments)
* [### Best practices for comments](#Best-practices-for-comments)
* [### String templates](#String-templates)
* [### Escaping `$` in strings](#Escaping-in-strings)
* [### Multiline strings with string templates](#Multiline-strings-with-string-templates)
* [### `if` expression](#if-expression)
* [### `when` expression](#when-expression)
* [### `else` and `else if`](#else-and-else-if)
* [### `for` loop](#for-loop)
* [### `for` loop: range with step](#for-loop-range-with-step)
* [### `for` loop: iterating in reverse order](#for-loop-iterating-in-reverse-order)
* [### Iterating over an array or a list](#Iterating-over-an-array-or-a-list)
* [### Iterating with indices](#Iterating-with-indices)
* [### `forEach` loop](#forEach-loop)
* [### Breaking and continuing in a loop](#Breaking-and-continuing-in-a-loop)
* [### `while` loop﻿](#while-loop)
* [### `do-while` loop](#do-while-loop)
* [### Breaking out of a `while` loop](#Breaking-out-of-a-while-loop)
* [### Skipping `while` iterations with continue](#Skipping-while-iterations-with-continue)
* [### Ranges﻿](#Ranges)
* [### Iterating over a range](#Iterating-over-a-range)
* [### Checking if a value is in a range](#Checking-if-a-value-is-in-a-range)
* [### Exclusive ranges (`until`)](#Exclusive-ranges-until)
* [### Character ranges](#Character-ranges)
* [### Checking if a range is empty](#Checking-if-a-range-is-empty)
* [### Progressions](#Progressions)
* [### Collections﻿](#Collections)
* [### Collections﻿: List](#Collections-List)
* [### Collections﻿: Set](#Collections-Set)
* [### Collections﻿: Map](#Collections-Map)
* [### Common collection operations](#Common-collection-operations)
* [### Collection immutability](#Collection-immutability)
* [### Nullable values](#Nullable-values)
* [### Null checks: Safe call `?.`](#Null-checks-Safe-call)
* [### Null checks: Elvis operator `?:`](#Null-checks-Elvis-operator)
* [### Null checks: Non-null assertion `!!`](#Null-checks-Non-null-assertion)
* [### Null checks: Safe cast `as?`](#Null-checks-Safe-cast-as)
* [### Nullability in functions](#Nullability-in-functions)
* [### Smart casts](#Smart-casts)
* [### `let` with safe call](#let-with-safe-call)
* [### Chaining safe calls](#Chaining-safe-calls)
* [### `takeIf` and `takeUnless`](#takeIf-and-takeUnless)
* [### Type checking with `is`](#Type-checking-with-is)
* [### Type casts with `as`](#Type-casts-with-as)
* [### Smart casts in `when` expressions](#Smart-casts-in-when-expressions)
* [### Combining type checks with `&&`](#Combining-type-checks-with)
* [### Smart cast limitations](#Smart-cast-limitations)
* [### `is` with nullable types](#is-with-nullable-types)

## ### Program entry point
In Kotlin, the entry point of a program is the `main` function. Here's a simple example of a program's entry point:

```kotlin
fun main() {
    println("Hello, Kotlin!")
}
```
### Explanation:
- The `main` function is the entry point where the Kotlin program starts execution.
- The function doesn't need any parameters, but if you want to accept command-line arguments, you can define it as:
```kotlin
fun main(args: Array<String>) {
    println("Command-line arguments: ${args.joinToString()}")
}
```
Here, `args` is an array of strings, allowing you to pass and handle command-line arguments.

## ### Package definition and imports
The package definition and imports are similar to other languages like Java. The package declaration is optional but recommended, especially in larger projects, to organize code. Imports allow you to bring in external classes or functions from other packages.

### Package definition
A Kotlin file starts with an optional package declaration. If no package is specified, the default package is used.

Example of package declaration:
```kotlin
package com.example.myapp
```
Here, `com.example.myapp` is the package where this Kotlin file resides.

### Imports
Imports are used to bring in classes, functions, or other declarations from other packages. Kotlin allows single or wildcard imports.

Single import example:
```kotlin
import kotlin.math.PI
```

Wildcard import example:
```kotlin
import kotlin.math.*
```
The `*` is a wildcard that imports all functions or properties from the `kotlin.math` package. Kotlin automatically imports some common packages like `kotlin.*`, `kotlin.io.*` and `kotlin.collections.*`, so you don't need to explicitly import them.

## ### Print to the standard output
Printing to the standard output can be done using the `println()` or `print()` functions.
- `println()` prints the message and adds a newline at the end.
- `print()` prints the message without adding a newline.

### Example:
```kotlin
fun main() {
    println("Hello, Kotlin!")  // Prints with a newline
    print("This is Kotlin.")   // Prints without a newline
    print("Still printing on the same line.")
}
```
### Output:
```no
Hello, Kotlin!
This is Kotlin. Still printing on the same line.
```
Both `println()` and `print()` are part of Kotlin’s standard library, so there's no need to import anything to use them.

## ### Read from the standard input
You can read from the standard input using the `readLine()` function. This function reads a line of input from the user and returns it as a nullable string `String?`. You can also convert or cast the input to other data types as needed.

Example 1: Reading a string from standard input
```kotlin
fun main() {
    println("Enter your name:")
    val name = readLine() // Reads input as a string
    println("Hello, $name!")
}
```
Example 2: Reading an integer from standard input
```kotlin
fun main() {
    println("Enter your age:")
    val age = readLine()?.toIntOrNull() // Converts input to an Int, safely handling nulls
    if (age != null) {
        println("You are $age years old.")
    } else {
        println("Invalid input, please enter a valid number.")
    }
}
```
Explanation:
- `readLine()` reads input from the standard input (console) as a string.
- The safe call operator `?.` ensures that `readLine()` is only called if the input is not null.
- `toIntOrNull()` converts the input to an integer or returns `null` if the conversion fails.

For reading other types like floats or doubles, you can use similar conversion methods like `toFloatOrNull()` or `toDoubleOrNull()`.

## ### Functions declaration
Functions are first-class citizens, meaning you can define, pass, and return them as variables. They can have parameters, return types, default arguments, and even be declared as anonymous (lambda functions). Here’s a breakdown of function usage in Kotlin.

### Basic function declaration
```kotlin
fun functionName(parameter1: Type, parameter2: Type): ReturnType {
    // Function body
    return value
}
```
Example of a basic function
```kotlin
fun greet(name: String): String {
    return "Hello, $name!"
}

fun main() {
    println(greet("Alice"))  // Output: Hello, Alice!
}
```

## ### Unit Functions (Functions with no return value)
The `Unit` type is similar to void in Java, but it can be omitted since it's the default return type when there’s no return value.

```kotlin
fun greet(name: String) {
    println("Hello, $name!")
}

fun main() {
    greet("Bob")  // Output: Hello, Bob!
}
```

## ### Single-expression functions
If a function consists of a single expression, you can simplify it by using the `=` operator:

```kotlin
fun add(a: Int, b: Int): Int = a + b

fun main() {
    println(add(3, 4))  // Output: 7
}
```

## ### Default and named arguments
Kotlin allows you to specify default parameter values. When calling the function, you can either omit the argument (and the default will be used) or specify the argument by name.

```kotlin
fun greet(name: String = "Guest") {
    println("Hello, $name!")
}

fun main() {
    greet()              // Output: Hello, Guest!
    greet("Charlie")      // Output: Hello, Charlie!
}
```
Function with named arguments
```kotlin
fun displayInfo(name: String, age: Int) {
    println("Name: $name, Age: $age")
}

fun main() {
    displayInfo(age = 25, name = "David")  // Output: Name: David, Age: 25
}
```

## ### Function with varargs (variable number of arguments)
The vararg keyword allows a function to accept a variable number of arguments.

```kotlin
fun printNumbers(vararg numbers: Int) {
    for (number in numbers) {
        println(number)
    }
}

fun main() {
    printNumbers(1, 2, 3, 4, 5)  
}
```

## ### Higher-order functions
Kotlin supports higher-order functions, meaning you can pass functions as arguments or return them from other functions.

Example of passing a function as a parameter:
```kotlin
fun operate(x: Int, y: Int, operation: (Int, Int) -> Int): Int {
    return operation(x, y)
}

fun main() {
    val sum = operate(4, 5, ::add)
    println(sum)  // Output: 9
}
```
In this example, `operate` takes another function operation as a parameter and applies it to `x` and `y`.

## ### Anonymous (lambda) functions
Lambda functions are concise ways to declare functions inline.

```kotlin
val multiply = { a: Int, b: Int -> a * b }

fun main() {
    println(multiply(3, 4))  // Output: 12
}
```

## ### Extension functions
You can add functions to existing classes using extension functions without modifying their source code.

```kotlin
fun String.addExclamation(): String {
    return this + "!"
}

fun main() {
    val message = "Hello"
    println(message.addExclamation())  // Output: Hello!
}
```
This function adds `addExclamation` to the `String` class, allowing any string to use it as if it were a method of `String`.

## ### Variables﻿
In Kotlin, variables are declared using two keywords: `val` and `var`. The difference between them is mutability -`val` is for read-only (immutable) variables, while var is for mutable variables that can be reassigned.

1. Immutable variables (`val`)

`val` is used to declare a read-only variable. Once a value is assigned to a `val` variable, it cannot be changed. It is equivalent to a `final` variable in Java.

```kotlin
val name: String = "Alice"
name = "Bob"  // Error: Val cannot be reassigned
```
- You must assign the value to a `val` at the time of its declaration.
- The type can be inferred, so specifying the type is optional.

```kotlin
val age = 25  // Type inferred as Int
```

2. Mutable Variables (`var`)

`var` is used to declare a mutable variable, meaning its value can be changed later.
```kotlin
var count: Int = 10
count = 20  // No error: var can be reassigned
```
- Like val, the type can also be inferred.

```kotlin
var greeting = "Hello"
greeting = "Hi"
```

## ### Type inference
Kotlin can automatically infer the type of a variable based on the assigned value. Explicit type declaration is optional if the compiler can infer the type.

```kotlin
val message = "Hello, Kotlin!"  // Type inferred as String
val number = 42  // Type inferred as Int
```

## ### Declaring variables without initialization
You can declare a variable without initializing it immediately, but you must specify the type in that case.

```kotlin
val age: Int
age = 30  // Now initialized
```

## ### Nullable variables
In Kotlin, you must explicitly declare whether a variable can hold `null` values by adding a `?` to the type. By default, variables are non-nullable.

```kotlin
val name: String? = null  // Nullable String
```
You need to use safe operations or null checks when working with nullable variables.

Example:
```kotlin
fun main() {
    // Immutable variable
    val language = "Kotlin"
    // language = "Java"  // Error: Val cannot be reassigned

    // Mutable variable
    var score = 10
    score += 5  // score is now 15

    // Nullable variable
    val nullableName: String? = null
    println(nullableName?.length)  // Safe call, won't crash if nullableName is null
}
```

## ### Constant variables
If you want to declare a constant that is known at compile-time and will never change, you can use `const val`. This is typically used at the top level or inside objects and companion objects.

```kotlin
const val PI = 3.14159
```
This declares PI as a constant that cannot be changed and is known at compile time.

## ### Creating classes and instances
In Kotlin, creating classes and instances is simple and concise. Kotlin provides features like primary and secondary constructors, properties, and default values, making it more compact than languages like Java.

### Defining a basic class
A class in Kotlin is defined using the `class` keyword.
```kotlin
class Person {
    var name: String = ""
    var age: Int = 0
}
```
This is a basic class with two properties: `name` and `age`.

### Creating an instance of a class
You can create an instance of a class using the `new` keyword is not required in Kotlin (unlike Java). You can simply instantiate it like this:
```kotlin
fun main() {
    val person = Person()
    person.name = "Alice"
    person.age = 25
    println("${person.name} is ${person.age} years old.")
}
```

## ### Primary constructor
Kotlin allows you to define a primary constructor directly in the class declaration.

```kotlin
class Person(val name: String, var age: Int)
```
In this example:
- `name` is a `val`, meaning it is read-only.
- `age` is a `var`, meaning it can be reassigned.

### Example:
```kotlin
class Person(val name: String, var age: Int)

fun main() {
    val person = Person("Alice", 25)
    println("${person.name} is ${person.age} years old.")
}
```

## ### Secondary constructor
In addition to the primary constructor, a class can have one or more secondary constructors. These are useful if you need to provide different ways to instantiate a class.

```kotlin
class Person(val name: String) {
    var age: Int = 0

    // Secondary constructor
    constructor(name: String, age: Int) : this(name) {
        this.age = age
    }
}
```
### Example:
```kotlin
fun main() {
    val person1 = Person("Alice")
    val person2 = Person("Bob", 30)

    println("${person1.name} is ${person1.age} years old.")  // Output: Alice is 0 years old.
    println("${person2.name} is ${person2.age} years old.")  // Output: Bob is 30 years old.
}
```

## ### Initializer block `init`
You can also use an init block to execute some code when the class is instantiated. The init block is executed after the primary constructor.

```kotlin
class Person(val name: String, var age: Int) {
    init {
        println("$name is created with age $age.")
    }
}

fun main() {
    val person = Person("Alice", 25)  // Output: Alice is created with age 25.
}
```

## ### Properties with custom getters and setters
You can define custom getters and setters for properties in Kotlin.

```kotlin
class Person(val name: String) {
    var age: Int = 0
        get() = field
        set(value) {
            if (value >= 0) field = value
        }
}
```
- `field` is a special keyword that refers to the backing field of the property.

### Example:
```kotlin
fun main() {
    val person = Person("Alice")
    person.age = 25
    println("${person.name} is ${person.age} years old.")  // Output: Alice is 25 years old.
    person.age = -5  // Will not change the age due to custom setter logic
    println("${person.name} is ${person.age} years old.")  // Output: Alice is 25 years old.
}
```

## ### Inheritance
Kotlin classes are `final` by default (cannot be inherited). To make a class inheritable, you need to use the `open` keyword.

```kotlin
open class Person(val name: String, var age: Int)

class Student(name: String, age: Int, val grade: String) : Person(name, age)
```
In this example, the `Student` class inherits from the `Person` class.

### Example:
```kotlin
fun main() {
    val student = Student("Alice", 20, "A")
    println("${student.name} is ${student.age} years old and got grade ${student.grade}.")
}
```

## ### Data classes
Kotlin provides **data classes** for classes whose primary purpose is to hold data. These classes automatically generate useful methods like `toString()`, `equals()` and `hashCode()`.

```kotlin
data class Person(val name: String, var age: Int)
```

### Example:
```kotlin
fun main() {
    val person = Person("Alice", 25)
    println(person)  // Output: Person(name=Alice, age=25)
}
```

## ### Comments﻿
In Kotlin, comments are similar to those in many other programming languages, such as Java or C++. There are two types of comments: single-line and multi-line.

1. Single-line comments

Single-line comments start with `//` and extend to the end of the line.

```kotlin
// This is a single-line comment
val name = "Alice"  // This comment explains the variable
```

2. Multi-line comments
Multi-line comments start with `/*` and end with `*/`. These can span multiple lines and can also be nested.

```kotlin
/* 
   This is a multi-line comment.
   It spans multiple lines.
*/
val age = 25

/* Nested comments are also allowed.
/* This is a nested comment. */
*/
val city = "New York"
```

## ### Best practices for comments
1. **Keep comments concise and relevant**: Use comments to explain why something is done rather than what is being done if the code is already self-explanatory.

2. **Avoid over-commenting**: Comment only where necessary, especially if the code is straightforward.

3. **Use TODO comments**: Kotlin has special support for `TODO()` function which throws `NotImplementedError`. It’s useful for marking areas of the code that need to be implemented later.

```kotlin
fun getData(): String {
    TODO("Not yet implemented")
}
```
Kotlin IDEs like IntelliJ IDEA highlight TODO comments, making it easier to track unfinished work.

## ### String templates
In Kotlin, string templates allow you to embed variables or expressions directly within a string, which makes string handling more concise and readable. Kotlin uses the `$` symbol to indicate a variable or expression within a string.

1. Embedding variables

You can embed variables directly into a string using the `$` symbol before the variable name.

```kotlin
val name = "Alice"
val greeting = "Hello, $name!"
println(greeting)  // Output: Hello, Alice!
```

2. Embedding Expressions

You can embed expressions inside curly braces `{}` within a string template. This is useful when you want to compute a value or call a function inside the string.

```kotlin
val age = 25
val message = "In 5 years, you will be ${age + 5} years old."
println(message)  // Output: In 5 years, you will be 30 years old.
```
You need to use curly braces `{}` for expressions, but for simple variables, you can use `$variableName` without braces.

## ### Escaping `$` in strings
If you need to print a literal `$` symbol in the string (instead of using it as a template), you can escape it with a backslash `\`.

```kotlin
val price = "The total cost is \$50."
println(price)  // Output: The total cost is $50.
```

## ### Multiline strings with string templates
You can use triple-quoted strings `"""` for multiline strings, and string templates still work inside these.

```kotlin
val name = "Charlie"
val multilineMessage = """
    Hello, $name!
    Welcome to Kotlin string templates.
"""
println(multilineMessage)
```

## ### `if` expression
In Kotlin, `if` is an expression, meaning it returns a value, unlike in many other languages where it's just a statement. This makes it more flexible.

### Basic `if` statement:
```kotlin
val a = 10
val b = 20

if (a > b) {
    println("a is greater than b")
} else {
    println("b is greater than or equal to a")
}
```

### `if` as an expression:
```kotlin
val max = if (a > b) a else b
println("Max is $max")  // Output: Max is 20
```
Here, the if expression returns the larger of a or b and assigns it to the max variable.

### if-else if-else chain:
```kotlin
val number = 5
val result = if (number < 0) {
    "Negative"
} else if (number == 0) {
    "Zero"
} else {
    "Positive"
}
println(result)  // Output: Positive
```

## ### `when` expression
The `when` expression in Kotlin is similar to `switch` in other languages but is more powerful. It can be used for matching conditions and returning values.

### Basic `when` example:
```kotlin
val x = 3

when (x) {
    1 -> println("x is 1")
    2 -> println("x is 2")
    3 -> println("x is 3")
    else -> println("x is unknown")
}
```

### `when` as an expression:
```kotlin
val result = when (x) {
    1 -> "One"
    2 -> "Two"
    3 -> "Three"
    else -> "Unknown"
}
println(result)  // Output: Three
```

### Multiple conditions in `when`:
You can check multiple conditions in a single when branch.
```kotlin
when (x) {
    0, 1 -> println("x is 0 or 1")
    else -> println("x is neither 0 nor 1")
}
```

### `when` with arbitrary conditions:
The when expression can also evaluate arbitrary conditions (not just values of a single variable).
```kotlin
val y = -5
val category = when {
    y < 0 -> "Negative"
    y == 0 -> "Zero"
    y > 0 -> "Positive"
    else -> "Unknown"
}
println(category)  // Output: Negative
```
In this example, when is used without a specific value to evaluate general conditions.

## ### `else` and `else if`
Kotlin supports `else` and `else if` for handling alternate conditions. These are used similarly to other languages:

```kotlin
val time = 18

val greeting = if (time < 12) {
    "Good morning"
} else if (time < 18) {
    "Good afternoon"
} else {
    "Good evening"
}
println(greeting)  // Output: Good evening
```

## ### `for` loop
In Kotlin, the `for` loop is used to iterate over ranges, arrays, collections, or any iterable objects. Here's a detailed explanation of how to use it.

### Iterating over a range
The most common use of the `for` loop in Kotlin is to iterate over a range of numbers.

```kotlin
for (i in 1..5) {
    println(i)
}
```
- This will print the numbers from 1 to 5, inclusive.
- The `..` operator creates a range from the first value to the second.

## ### `for` loop: range with step
You can control the step of the iteration using the step keyword.

```kotlin
for (i in 1..10 step 2) {
    println(i)
}
```
- This will print the numbers 1, 3, 5, 7, 9.
- The `step` function allows you to increment by a value other than 1.

## ### `for` loop: iterating in reverse order
To iterate in reverse order, you can use the `downTo` keyword.

```kotlin
for (i in 5 downTo 1) {
    println(i)
}
```
- This will print the numbers 5, 4, 3, 2, 1.

You can also combine `downTo` with step:

```kotlin
for (i in 10 downTo 0 step 2) {
    println(i)
}
```
- This will print 10, 8, 6, 4, 2, 0.

## ### Iterating over an array or a list
You can iterate over arrays, lists, or any other collections in Kotlin.

```kotlin
val numbers = arrayOf(1, 2, 3, 4, 5)
for (num in numbers) {
    println(num)
}
```

Similarly, with a list:
```kotlin
val fruits = listOf("Apple", "Banana", "Cherry")
for (fruit in fruits) {
    println(fruit)
}
```

## ### Iterating with indices
If you want to access the index of each element while iterating over a collection, you can use the `indices` property or the `withIndex()` function.

### Using `indices`:
```kotlin
val fruits = listOf("Apple", "Banana", "Cherry")
for (i in fruits.indices) {
    println("Fruit at index $i is ${fruits[i]}")
}
```

### Using withIndex():
```kotlin
for ((index, fruit) in fruits.withIndex()) {
    println("Fruit at index $index is $fruit")
}
```
- withIndex() provides both the index and the value in each iteration.

## ### `forEach` loop
You can also use the `forEach` higher-order function to iterate over collections.

```kotlin
val fruits = listOf("Apple", "Banana", "Cherry")
fruits.forEach { fruit ->
    println(fruit)
}
```

## ### Breaking and continuing in a loop
You can use `break` to exit a loop and `continue` to skip the current iteration.

```kotlin
for (i in 1..5) {
    if (i == 3) break
    println(i)  // Prints 1, 2
}

for (i in 1..5) {
    if (i == 3) continue
    println(i)  // Prints 1, 2, 4, 5
}
```

## ### `while` loop﻿
In Kotlin, the while loop is used to repeatedly execute a block of code as long as a specified condition is true. Kotlin supports two types of while loops: `while` and `do-while`.

### `while` loop
The `while` loop checks the condition before executing the block of code. If the condition is `true`, the loop will execute the code block. The loop continues until the condition becomes `false`.

### Syntax:
```kotlin
while (condition) {
    // Code to execute
}
```

Example:
```kotlin
var i = 1
while (i <= 5) {
    println(i)
    i++
}
```
- This will print the numbers 1 to 5.
- The condition `i <= 5` is checked before the loop body is executed.

## ### `do-while` loop
The `do-while` loop is similar to the `while` loop, but the difference is that the condition is checked after the block of code has been executed. This means that the loop is guaranteed to run at least once, even if the condition is initially `false`.

### Syntax:
```kotlin
do {
    // Code to execute
} while (condition)
```

Example:
```kotlin
var i = 1
do {
    println(i)
    i++
} while (i <= 5)
```
- This will also print the numbers 1 to 5.
- The condition `i <= 5` is checked after the loop executes, so the code block is executed at least once.

## ### Breaking out of a `while` loop
You can use the `break` statement to exit a `while` loop prematurely when a certain condition is met.

### Example:
```kotlin
var i = 1
while (i <= 10) {
    if (i == 6) {
        break  // Exit the loop when i is 6
    }
    println(i)
    i++
}
```
- This will print numbers from 1 to 5 and then break the loop when `i` equals 6.

## ### Skipping `while` iterations with continue
You can use the `continue` statement to skip the current iteration and proceed to the next iteration of the loop.

### Example:
```kotlin
var i = 1
while (i <= 5) {
    if (i == 3) {
        i++
        continue  // Skip the rest of the loop when i is 3
    }
    println(i)
    i++
}
```
- This will print the numbers 1, 2, 4, and 5, skipping 3.

## ### Ranges﻿
In Kotlin, ranges are an essential feature that allows you to work with sequences of values in a concise and readable manner. A range is essentially a progression of values, which can be used in loops, conditions, and other situations where you need a sequence of numbers or characters.

### Creating a range
You can create a range using the `..` operator. A range is inclusive, meaning both the start and the end values are part of the range.

### Example:
```kotlin
val range = 1..5
println(range)  // Output: 1..5
```
- This range includes the numbers 1, 2, 3, 4, and 5.

## ### Iterating over a range
You can easily iterate over a range with a `for` loop.

### Example:
```kotlin
for (i in 1..5) {
    println(i)  // Output: 1 2 3 4 5
}
```

## ### Checking if a value is in a range
You can check whether a value belongs to a range using the `in` operator.

### Example:
```kotlin
val num = 3
if (num in 1..5) {
    println("$num is in the range.")
} else {
    println("$num is not in the range.")
}
// Output: 3 is in the range.
```

## ### Exclusive ranges (`until`)
The `..` operator creates an inclusive range. If you want an exclusive range (where the end value is excluded), you can use the `until` function.

### Example:
```kotlin
for (i in 1 until 5) {
    println(i)  // Output: 1 2 3 4
}
```
- The range `1 until 5` includes 1, 2, 3, and 4, but excludes 5.

## ### Character ranges
Ranges are not limited to numbers; you can also create ranges for characters.

### Example:
```kotlin
for (ch in 'a'..'d') {
    println(ch)  // Output: a b c d
}
```

## ### Checking if a range is empty
You can check if a range is empty using the `isEmpty()` function. This is useful when dealing with ranges where the start value might be greater than the end value (for example, in descending ranges).

### Example:
```kotlin
val range = 5..1
println(range.isEmpty())  // Output: true
```

In reverse ranges, use `downTo` to prevent empty ranges:
```kotlin
val range = 5 downTo 1
println(range.isEmpty())  // Output: false
```

## ### Progressions
A progression in Kotlin is a sequence defined by a starting value, an ending value, and a step. It is the underlying mechanism for ranges with steps and reverse ranges.

```kotlin
val progression = 1..10 step 3
println(progression.toList())  // Output: [1, 4, 7, 10]
```

## ### Collections﻿
In Kotlin, collections are used to store groups of related data. Kotlin provides a rich set of collection types, and it supports both immutable and mutable collections. The key types of collections are:

- **List**: Ordered collection of elements.
- **Set**: Collection of unique elements.
- **Map**: Collection of key-value pairs.

## ### Collections﻿: List
A List is an ordered collection of elements that can contain duplicates. There are two types of lists in Kotlin:

- **Immutable list**: Read-only, elements cannot be added, removed, or modified.
- **Mutable list**: You can modify the list by adding, removing, or updating elements.

### Immutable list:
```kotlin
val numbers: List<Int> = listOf(1, 2, 3, 4, 5)
println(numbers)  // Output: [1, 2, 3, 4, 5]
println(numbers[0])  // Access element at index 0: Output: 1
```
- The listOf() function creates an immutable list.

### Mutable list:
```kotlin
val mutableNumbers: MutableList<Int> = mutableListOf(1, 2, 3)
mutableNumbers.add(4)
mutableNumbers[0] = 10
println(mutableNumbers)  // Output: [10, 2, 3, 4]
```
- The mutableListOf() function creates a mutable list that can be modified.

### Iterating over a list:
```kotlin
val fruits = listOf("Apple", "Banana", "Cherry")
for (fruit in fruits) {
    println(fruit)
}
```

## ### Collections﻿: Set
A Set is an unordered collection of unique elements. It does not allow duplicate values.

### Immutable set:
```kotlin
val numbers: Set<Int> = setOf(1, 2, 3, 3, 4)
println(numbers)  // Output: [1, 2, 3, 4] (duplicates are removed)
```
- The `setOf()` function creates an immutable set.

### Mutable set:
```kotlin
val mutableNumbers: MutableSet<Int> = mutableSetOf(1, 2, 3)
mutableNumbers.add(4)
mutableNumbers.add(2)  // Duplicate, will be ignored
println(mutableNumbers)  // Output: [1, 2, 3, 4]
```
- The `mutableSetOf()` function creates a mutable set.

## ### Collections﻿: Map
A Map is a collection of key-value pairs. Each key must be unique, but values can be duplicated. Like other collections, maps can be immutable or mutable.

### Immutable Map:
```kotlin
val map: Map<String, Int> = mapOf("Alice" to 25, "Bob" to 30)
println(map["Alice"])  // Output: 25
```
- The `mapOf()` function creates an immutable map.
- Keys are accessed using square brackets: `map["key"]`.

### Mutable Map:
```kotlin
val mutableMap: MutableMap<String, Int> = mutableMapOf("Alice" to 25)

mutableMap["Bob"] = 30  // Adding a new key-value pair
mutableMap["Alice"] = 26  // Modifying an existing value

println(mutableMap)  // Output: {Alice=26, Bob=30}
```
- The `mutableMapOf()` function creates a mutable map that can be modified.

## ### Common collection operations
### Filtering:
You can filter elements from collections based on a condition using `filter()`.

```kotlin
val numbers = listOf(1, 2, 3, 4, 5)

val evenNumbers = numbers.filter { it % 2 == 0 }

println(evenNumbers)  // Output: [2, 4]
```

### Mapping:
You can transform each element in a collection using the `map()` function.

```kotlin
val numbers = listOf(1, 2, 3)

val squares = numbers.map { it * it }

println(squares)  // Output: [1, 4, 9]
```

### Checking membership:
`contains()` Checks if a specific element is in the collection.
```kotlin
val numbers = listOf(1, 2, 3)

println(numbers.contains(2))  // Output: true
```

### Finding elements:
`find()` Returns the first element that matches the condition.
```kotlin
val numbers = listOf(1, 2, 3, 4, 5)

val foundNumber = numbers.find { it > 3 }

println(foundNumber)  // Output: 4
```

### Sorting:
You can sort elements using `sorted()`, `sortedBy()` or `sortedDescending()`.
```kotlin
val numbers = listOf(5, 3, 1, 4, 2)

println(numbers.sorted())  // Output: [1, 2, 3, 4, 5]

println(numbers.sortedDescending())  // Output: [5, 4, 3, 2, 1]
```

## ### Collection immutability
In Kotlin, collections are immutable by default. This helps enforce immutability and makes the code more predictable. If you need a mutable collection, you must explicitly create one using `mutableListOf()`, `mutableSetOf()` or `mutableMapOf()`.

Immutable vs mutable:
```kotlin
val list = listOf(1, 2, 3)  // Immutable List

// list.add(4)  // Error: Cannot add elements to an immutable list

val mutableList = mutableListOf(1, 2, 3)  // Mutable List
mutableList.add(4)  // Works fine
```

## ### Nullable values
In Kotlin, nullable values and null checks are an essential part of handling null safely. Kotlin’s type system distinguishes between nullable types and non-null types, making your code safer by preventing `NullPointerException (NPE)`.

### Nullable types
In Kotlin, you can explicitly declare a type as nullable by appending a question mark `?` to the type. This indicates that the variable can hold either a non-null value or `null`.

Example:
```kotlin
var name: String? = "Kotlin"
name = null  // This is allowed because it's nullable
```
- `String?` is a nullable type. It can either hold a `String` value or `null`.

If you don't append `?`, the type is non-nullable, and it will never hold `null`:
```kotlin
var name: String = "Kotlin"
// name = null  // Compilation error: Null can not be a value of a non-null type String
```

## ### Null checks: Safe call `?.`
You can use the safe call operator `?.` to call methods or access properties on a nullable object. If the object is `null`, the expression will return `null` instead of throwing an exception.

```kotlin
val length: Int? = name?.length

println(length)  // Prints the length if `name` is not null, otherwise prints `null`
```
In the above example, if name is `null`, the result of `name?.length` will be `null`. If `name` is not null, it returns the length of the string.

## ### Null checks: Elvis operator `?:`
The Elvis operator `?:` provides a default value in case the expression on the left is `null`.

```kotlin
val length: Int = name?.length ?: 0

println(length)  // If `name` is null, it prints 0; otherwise, it prints the length
```
This is very useful for providing fallback values.

## ### Null checks: Non-null assertion `!!`
You can use the **non-null assertion operator** `!!` to forcibly assert that a nullable value is not `null`. However, if the value is actually null, this will result in a `NullPointerException`.

```kotlin
val length: Int = name!!.length
```
**Use this cautiously**, as it can lead to crashes if you're wrong about the nullability of the value.

## ### Null checks: Safe cast `as?`
If you want to cast a value to a specific type, but you're not sure if the cast is possible, you can use the **safe cast operator** `as?`. It will return `null` if the cast fails, rather than throwing a `ClassCastException`.

```kotlin
val obj: Any = "Hello"

val str: String? = obj as? String

println(str)  // Prints "Hello"

val number: Int? = obj as? Int

println(number)  // Prints `null` because obj is not an Int
```

## ### Nullability in functions
You can declare function parameters and return types as nullable by adding the `?` symbol.

### Example:
```kotlin
fun greet(name: String?): String {
    return name ?: "Guest"
}

println(greet("John"))  // Output: John
println(greet(null))    // Output: Guest
```
In this case, the function `greet()` accepts a nullable `String?` and uses the Elvis operator to provide a default value.

## ### Smart casts
Kotlin automatically handles null checks and performs smart casts, meaning if you check for `null`, the compiler knows it's safe to use the non-null version of the variable in the following code.

### Example:
```kotlin
val name: String? = "Kotlin"

if (name != null) {
    println(name.length)  // Smart cast to non-nullable String
}
```

## ### `let` with safe call
You can use the `let` function to execute a block of code only if the value is not `null`. It's often used in conjunction with the safe call operator `?.`

Example:
```kotlin
val name: String? = "Kotlin"

name?.let {
    println("The length of the name is ${it.length}")
}
```
The code inside the `let` block will only execute if `name` is not `null`. Inside `let`, it refers to the non-null value of `name`.

## ### Chaining safe calls
You can chain multiple safe calls to navigate through a series of nullable properties without needing to check for `null` at every level.

### Example:
```kotlin
class Address(val city: String?)

class Person(val address: Address?)

val person: Person? = Person(Address("New York"))

println(person?.address?.city)  // Prints "New York"

val unknownPerson: Person? = null

println(unknownPerson?.address?.city)  // Prints `null`
```
If any part of the chain is `null`, the whole expression evaluates to `null` without throwing an exception.

## ### `takeIf` and `takeUnless`
The `takeIf` function returns the object if it matches a given condition or `null` if it doesn't. This can be useful for conditional null handling.

```kotlin
val name: String? = "Kotlin"

val validName = name?.takeIf { it.isNotBlank() }

println(validName)  // Prints "Kotlin"
```
Similarly, `takeUnless` does the opposite, returning the object if the condition is `false`.

## ### Type checking with `is`
Kotlin provides the is operator to check whether an object is of a certain type.

### Example:
```kotlin
val obj: Any = "Kotlin"

if (obj is String) {
    println(obj.length)  // Smart cast to String
}
```
In this example, `is` checks if `obj` is of type `String`. If true, Kotlin automatically casts `obj` to `String` inside the if block.

### Negating type check with `!is`
You can use `!is` to check if an object is not of a certain type.

```kotlin
val obj: Any = 123

if (obj !is String) {
    println("Not a string")  // Prints: Not a string
}
```

## ### Type casts with `as`
If you are sure about the type of a variable, you can explicitly cast it using the `as` operator.

### Example:
```kotlin
val obj: Any = "Kotlin"

val str: String = obj as String

println(str.length)  // Output: 6
```
The `as` operator casts `obj` to `String`. If the cast is invalid (e.g., if obj is not actually a `String`), it throws a `ClassCastException`.

## ### Smart casts in `when` expressions
In Kotlin, when expressions are commonly used with type checks. The smart cast feature also applies here. After checking the type using `is` inside a `when` expression, the variable is automatically cast to that type within the corresponding branch.

### Example:
```kotlin
fun describe(obj: Any): String {
    return when (obj) {
        is String -> "String of length ${obj.length}"  // Smart cast to String

        is Int -> "Integer: $obj"  // Smart cast to Int

        else -> "Unknown type"
    }
}

println(describe("Hello"))  // Output: String of length 5

println(describe(42))       // Output: Integer: 42

println(describe(3.14))     // Output: Unknown type
```
In the `when` expression, once the type is checked with `is`, Kotlin smartly casts the object to the corresponding type within that branch.


## ### Combining type checks with `&&`
You can combine type checks with other conditions in a single statement. Kotlin will still perform smart casting if the type check succeeds.

### Example:
```kotlin
fun printLengthIfValid(obj: Any?) {
    if (obj is String && obj.length > 0) {
        println("String length: ${obj.length}")  // Smart cast to String
    } else {
        println("Invalid or empty string")
    }
}

printLengthIfValid("Kotlin") // Output: String length: 6

printLengthIfValid("") // Output: Invalid or empty string

printLengthIfValid(null) // Output: Invalid or empty string
```
In this example, after checking `obj is String && obj.length > 0`, the compiler automatically casts `obj` to `String` inside the `if` block.

## ### Smart cast limitations
There are some limitations to smart casting in Kotlin. If the variable can be modified after the type check, the compiler cannot guarantee that the type will remain the same, so smart casting won't occur.

### Example:
```kotlin
fun checkType(obj: Any?) {
    if (obj is String) {
        // `obj` is smart-cast to String here
        println(obj.length)
    }
}

var obj: Any? = "Kotlin"
if (obj is String) {
    obj = null  // Modifying obj makes smart cast unsafe

    // println(obj.length)  // Error: Smart cast to String is not possible
}
```
Since `obj` is mutable and could change between the type check and its usage, the compiler cannot smart-cast it after a modification.

## ### `is` with nullable types
When you use the `is` operator with nullable types, smart casting is also applied. However, if the value is `null`, the smart cast does not happen.

### Example:
```kotlin
fun checkNullable(obj: Any?) {
    if (obj is String) {
        println("String length: ${obj.length}")  // Smart cast to String
    } else {
        println("Not a string or null")
    }
}

checkNullable("Hello") // Output: String length: 5

checkNullable(null) // Output: Not a string or null
```
