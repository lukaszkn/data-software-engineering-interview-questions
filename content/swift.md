# Swift Basics
The basics, string and characters, collection types, control flow, functions, closures, enumerations, structures and classes, properties, methods

* [What is a `weak` reference?](#What-is-a-weak-reference)
* [What is an `unowned` reference?](#What-is-an-unowned-reference)
* [Key differences between `unowned` and `weak` references](#Key-differences-between-unowned-and-weak-references)
* [What is ARC?](#What-is-ARC)
* [What is strong reference?](#What-is-strong-reference)
* [What is Strong Reference Cycle?](#What-is-Strong-Reference-Cycle)
* [What is implicitly unwrapped optional property?](#What-is-implicitly-unwrapped-optional-property)
* [Why use implicitly unwrapped optionals?](#Why-use-implicitly-unwrapped-optionals)
* [How to resolve Strong Reference Cycle in closure?](#How-to-resolve-Strong-Reference-Cycle-in-closure)
* [What are common kinds of data types?](#What-are-common-kinds-of-data-types)
* [What is tuple?](#What-is-tuple)
* [Accessing tuple elements](#Accessing-tuple-elements)
* [Named elements in a tuple](#Named-elements-in-a-tuple)
* [Returning tuples from functions](#Returning-tuples-from-functions)
* [Decomposing tuples](#Decomposing-tuples)
* [What is optional type?](#What-is-optional-type)
* [How to declare constants and variables?](#How-to-declare-constants-and-variables)
* [How to provide type annotation?](#How-to-provide-type-annotation)
* [How to print constant or variable?](#How-to-print-constant-or-variable)
* [What is type safety and type inference?](#What-is-type-safety-and-type-inference)
* [How to define numeric literal?](#How-to-define-numeric-literal)
* [What is type alias?](#What-is-type-alias)
* [What is optional binding?](#What-is-optional-binding)
* [What is force unwrapping?](#What-is-force-unwrapping)
* [What is optional chaining?](#What-is-optional-chaining)
* [What is nil-coalescing operator?](#What-is-nil-coalescing-operator)
* [How to do error handling?](#How-to-do-error-handling)
* [How to debug with assertions in Swift?](#How-to-debug-with-assertions-in-Swift)
* [What is `preconditionFailure` and `fatalError`](#What-is-preconditionFailure-and-fatalError)
* [What are comparison operators?](#What-are-comparison-operators)
* [What are range operators?](#What-are-range-operators)
* [What is String interpolation?](#What-is-String-interpolation)
* [What are String indices?](#What-are-String-indices)
* [What are Substrings?](#What-are-Substrings)
* [What are primary collection types?](#What-are-primary-collection-types)
* [What are fundamental `Set` operations?](#What-are-fundamental-Set-operations)
* [What are the available loops?](#What-are-the-available-loops)
* [What is `stride` used or?](#What-is-stride-used-or)
* [What's the difference in switch statements between Swift and Objective-C?](#What-s-the-difference-in-switch-statements-between-Swift-and-Objective-C)
* [What is switch case value binding?](#What-is-switch-case-value-binding)
* [What is deferred action?](#What-is-deferred-action)
* [How to check API availability?](#How-to-check-API-availability)
* [How to define a function?](#How-to-define-a-function)
* [How can you use function as type?](#How-can-you-use-function-as-type)
* [How to omit function argument label?](#How-to-omit-function-argument-label)
* [What is variadic parameter?](#What-is-variadic-parameter)
* [What is `inout` parameter?](#What-is-inout-parameter)
* [What is closure?](#What-is-closure)
* [What is trailing closure?](#What-is-trailing-closure)
* [How a closure can capture values?](#How-a-closure-can-capture-values)
* [What are strong and weak references in closures?](#What-are-strong-and-weak-references-in-closures)
* [What is an escaping closure?](#What-is-an-escaping-closure)
* [How to define stored closure?](#How-to-define-stored-closure)
* [What is autoclosure?](#What-is-autoclosure)
* [`@autoclosure` and `@escaping`](#autoclosure-and-escaping)
* [What are associated values?](#What-are-associated-values)
* [What is recursive enumeration?](#What-is-recursive-enumeration)
* [What's the difference between `struct` and `class`?](#What-s-the-difference-between-struct-and-class)
* [Compare inheritance between `struct` and `class`](#Compare-inheritance-between-struct-and-class)
* [Compare mutability between `struct` and `class`](#Compare-mutability-between-struct-and-class)
* [Compare memory management between `struct` and `class`](#Compare-memory-management-between-struct-and-class)
* [Compare identity between `struct` and `class`](#Compare-identity-between-struct-and-class)
* [When to use structs vs. classes?](#When-to-use-structs-vs-classes)
* [What are identity operators?](#What-are-identity-operators)
* [What is lazy stored property?](#What-is-lazy-stored-property)
* [What are use cases of lazy stored properties?](#What-are-use-cases-of-lazy-stored-properties)
* [What is computed property?](#What-is-computed-property)
* [Whare are advantages of computed properties?](#Whare-are-advantages-of-computed-properties)
* [What are property observers?](#What-are-property-observers)
* [What is `mutating` keyword used for?](#What-is-mutating-keyword-used-for)
* [What are type methods?](#What-are-type-methods)
* [Compare type methods in structs, enums and classes](#Compare-type-methods-in-structs-enums-and-classes)
* [How to prevent overrides?](#How-to-prevent-overrides)
* [What is designated initializer?](#What-is-designated-initializer)
* [What are rules for designated initializers?](#What-are-rules-for-designated-initializers)
* [How to indicate that a function, method, or initializer can throw an error?](#How-to-indicate-that-a-function-method-or-initializer-can-throw-an-error)
* [How to specifying an error type?](#How-to-specifying-an-error-type)
* [What is `guard` used for?](#What-is-guard-used-for)
* [What is type casting?](#What-is-type-casting)
* [What are available type casting operators?](#What-are-available-type-casting-operators)
* [Example of using the `is` operator](#Example-of-using-the-is-operator)
* [Example of using the `as?` operator (safe downcasting)](#Example-of-using-the-as-operator-safe-downcasting)
* [Example of using the `as!` operator (forced downcasting)](#Example-of-using-the-as-operator-forced-downcasting)
* [Example of using the `as` operator (upcasting and type bridging)](#Example-of-using-the-as-operator-upcasting-and-type-bridging)
* [What is `try?` used for?](#What-is-try-used-for)
* [What is `try!` used for?](#What-is-try-used-for)

## What is a `weak` reference?
A `weak` reference in Swift is a way of referencing an object without increasing its reference count, thereby preventing strong reference cycles (also known as retain cycles) and allowing for proper memory management in situations where two objects might reference each other.

```swift
class Apartment {
    weak var tenant: Person?
}
```

## What is an `unowned` reference?
An `unowned` reference in Swift is a reference to an object that, like a `weak` reference, does not increase the reference count of the object it points to. However, unlike a `weak` reference, an `unowned` reference is non-optional and does not automatically become `nil` when the referenced object is deallocated. Because of this, `unowned` references must be used carefully, as they assume the referenced object will always exist as long as the `unowned` reference is used.

### Example of unowned usage
Consider a scenario where you have two classes, `Owner` and `Asset`. An `Asset` always has an `Owner`, and it should not exist without one. Here, you might use an unowned reference for the owner property in `Asset`:

```swift
class Owner {
    var name: String
    var asset: Asset?

    init(name: String, assetName: String) {
        self.name = name
        self.asset = Asset(name: assetName, owner: self)
    }

    deinit {
        print("\(name) is being deinitialized")
    }
}

class Asset {
    var name: String
    unowned var owner: Owner

    init(name: String, owner: Owner) {
        self.name = name
        self.owner = owner
    }

    deinit {
        print("\(name) is being deinitialized")
    }
}

var owner: Owner? = Owner(name: "John", assetName: "Laptop")
print("\(owner?.asset?.owner.name ?? "") owns a \(owner?.asset?.name ?? "")")
// Output: John owns a Laptop

owner = nil
// Both `Owner` and `Asset` are deallocated without causing a memory leak
```
Explanation:
- **`unowned var owner: Owner`**: The `Asset` holds an `unowned` reference to its `Owner`. This means that the `Owner` can be deallocated without causing the `Asset` to be kept in memory (no strong reference cycle). However, it assumes that the `Owner` will outlive the `Asset`.

- **`No memory leaks`**: When the owner variable is set to `nil`, both the `Owner` and the `Asset` are properly deallocated because there’s no strong reference cycle.

## Key differences between `unowned` and `weak` references
1. Non-optional:

- An `unowned` reference is non-optional, meaning it does not hold a `nil` value. You declare it as a regular reference (`SomeClass`) rather than an optional (`SomeClass?`).

- A `weak` reference, on the other hand, must be optional because it automatically becomes nil when the referenced object is deallocated.

2. No automatic nil assignment:

- With `unowned`, if the referenced object is deallocated and you try to access it through the `unowned` reference, your app will crash because the reference points to memory that has been freed.

- A `weak` reference, by contrast, safely becomes `nil` when the referenced object is deallocated, preventing crashes due to dangling pointers.

3. Usage Scenario:

- Use `unowned` when you know the referenced object will outlive the reference, meaning the object will always be valid while the `unowned` reference is in use.

- Use `weak` when the lifecycle of the referenced object is uncertain or when it might be deallocated while the reference still exists.

## What is ARC?
ARC or Automatic Reference Counting is a memory management feature in Swift (and Objective-C) that automatically handles the allocation and deallocation of memory for objects. ARC ensures that memory is efficiently managed, preventing memory leaks and ensuring that objects are deallocated when they are no longer needed.

### How ARC works

ARC operates by keeping track of the number of strong references to an object. Each time you create a strong reference to an object, ARC increments the reference count for that object. Conversely, when a strong reference is removed or goes out of scope, ARC decrements the reference count. When the reference count drops to zero, ARC automatically deallocates the object, freeing up the memory.

## What is strong reference?
A strong reference is the default type of reference used when one object holds a reference to another. When you create a strong reference to an object, the reference count of that object is incremented. As long as at least one strong reference to the object exists, the object will not be deallocated, meaning its memory is retained.

### How strong references work

When you assign an instance of a class to a variable, constant, or property, Swift creates a strong reference by default. This strong reference increases the reference count of the object, ensuring that the object remains in memory.

## What is Strong Reference Cycle?
A strong reference cycle (also known as a retain cycle) occurs when two or more objects hold strong references to each other, preventing any of them from being deallocated. This happens because the reference counts of the objects involved never drop to zero, causing them to remain in memory indefinitely. As a result, this can lead to memory leaks, where memory that is no longer needed is not released.

### How a Strong Reference Cycle occurs
When you create a reference to an object, by default, it is a strong reference. The reference count of the object is incremented by one for every strong reference made to it. For the object to be deallocated and its memory freed, all strong references to it must be removed, causing its reference count to drop to zero.

A strong reference cycle occurs when two objects reference each other strongly, like this:

1. Object A holds a strong reference to Object B.
2. Object B holds a strong reference to Object A.

Because both objects hold strong references to each other, neither object can be deallocated, even if there are no other references to them.

## What is implicitly unwrapped optional property?
An implicitly unwrapped optional is a type that can contain either a value or `nil`, similar to a regular optional, but it is automatically unwrapped when accessed. This means you can use it as if it were a non-optional type, without needing to manually unwrap it using `!` or `?`. However, if you try to access an implicitly unwrapped optional that contains `nil`, it will cause a runtime crash.

### Syntax
You define an implicitly unwrapped optional by appending an exclamation mark `!` to the type rather than a question mark `?` which is used for regular optionals.

```swift
var name: String! // Implicitly unwrapped optional
```

### Usage
Implicitly unwrapped optionals are useful when a property is known to have a value after it is initially set but cannot be initialized with a value during object creation. They are often used during initialization when the value will be assigned after the object is created but before it is used.

Example:
```swift
class Person {
    var name: String!
    
    init() {
        // Initially, the name is not set, so it's an optional
    }

    func setName(_ newName: String) {
        name = newName // Assign a value to the implicitly unwrapped optional
    }

    func printName() {
        print(name) // Automatically unwraps the optional
    }
}

let john = Person()
john.setName("John") // Now the name is set
john.printName() // Prints: John
```
In this example:
- `name` is declared as an implicitly unwrapped optional `String!`. It starts as `nil` but can later hold a value.

- Once a value is assigned to `name`, it can be used without needing to unwrap it explicitly.

## Why use implicitly unwrapped optionals?
- **Convenience**: It allows you to avoid explicit unwrapping throughout your code, making it cleaner when you know the value will be set before use.

- **Interoperability**: It's particularly useful when working with Objective-C APIs that use `nil` to represent absence but don't use Swift's optionals.

### Risks
While convenient, using implicitly unwrapped optionals comes with risks. If you try to access the value of an implicitly unwrapped optional when it is `nil`, the application will crash:

```swift
let john = Person()
john.printName() // Runtime crash! name is nil and we're trying to access it.
```
To mitigate this risk, use implicitly unwrapped optionals only when you are certain that the variable will always have a value before it is accessed. If there's any uncertainty, it is safer to use a regular optional and unwrap it safely with if let or guard let.

## How to resolve Strong Reference Cycle in closure?
To resolve strong reference cycles in closures, you can use capture lists with weak or unowned references. A capture list is a way to explicitly control how values are captured by a closure.

Using a weak reference:
```swift
class Person {
    var name: String
    var greeting: (() -> Void)?

    init(name: String) {
        self.name = name
    }

    func setupGreeting() {
        greeting = { [weak self] in
            guard let self = self else { return }
            print("Hello, \(self.name)!")
        }
    }

    deinit {
        print("\(name) is being deinitialized")
    }
}

var john: Person? = Person(name: "John")
john?.setupGreeting()
john = nil // Now the Person instance is deallocated correctly
```
In this case:
- The closure captures `self` as a `weak` reference, meaning it does not retain `self`.

- Before using `self` inside the closure, you safely unwrap it using `guard let` to ensure self is still available.

## What are common kinds of data types?
1. Basic/Primitive Data Types
- **Int**: Represents integer values. It can hold both positive and negative whole numbers.
  ```swift
  let age: Int = 30
  ```
- **UInt**: Represents unsigned integer values (only positive whole numbers or zero).
  ```swift
  let count: UInt = 10
  ```

- **Float**: Represents a 32-bit floating-point number (decimal number).
  ```swift
  let pi: Float = 3.14
  ```

- **Double**: Represents a 64-bit floating-point number, providing more precision than Float.
  ```swift
  let pi: Double = 3.141592653589793
  ```

- **Bool**: Represents a Boolean value, which can be either true or false.
  ```swift
  let isActive: Bool = true
  ```

- **Character**: Represents a single character.
  ```swift
  let letter: Character = "A"
  ```

- **String**: Represents a sequence of characters, used for text.
  ```swift
  let name: String = "John"
  ```

2. Collection Types
- **Array**: An ordered collection of values of the same type.
  ```swift
  let numbers: [Int] = [1, 2, 3, 4, 5]
  ```

- **Dictionary**: An unordered collection of key-value pairs, where keys are unique.
  ```swift
  let studentGrades: [String: Int] = ["John": 90, "Jane": 85]
  ```

- **Set**: An unordered collection of unique values.
  ```swift
  let uniqueNumbers: Set<Int> = [1, 2, 3, 4, 5]
  ```

## What is tuple?
A tuple is a compound type that groups multiple values into a single, ordered, and fixed-size entity. Each element in a tuple can be of any type, and the types of the elements can vary within the same tuple. Tuples are useful for temporarily grouping related values together and returning multiple values from a function.

### Creating tuples
You create a tuple by enclosing multiple values in parentheses, separated by commas. For example:

```swift
let person = ("John", 30)
```
In this example:
- `person` is a tuple containing two elements: a `String` ("John") and an `Int` (30).

## Accessing tuple elements
You can access the elements of a tuple by their index (starting from zero):

```swift
let name = person.0 // Accesses the first element: "John"

let age = person.1  // Accesses the second element: 30
```

## Named elements in a tuple
You can also name the elements of a tuple when you create it, making it easier to access them:

```swift
let person = (name: "John", age: 30)

let name = person.name // Accesses "John"

let age = person.age   // Accesses 30
```

## Returning tuples from functions
Tuples are often used to return multiple values from a function:

```swift
func getPerson() -> (String, Int) {
    return ("John", 30)
}

let person = getPerson()
print("Name: \(person.0), Age: \(person.1)")
```
Or with named elements:

```swift
func getPerson() -> (name: String, age: Int) {
    return ("John", 30)
}

let person = getPerson()
print("Name: \(person.name), Age: \(person.age)")
```

## Decomposing tuples
You can also decompose a tuple into separate constants or variables:

```swift
let (name, age) = person
print("Name: \(name), Age: \(age)")
```
### Example usage
Tuples are useful in scenarios where you need to group multiple related values together but don't necessarily want to create a custom type like a struct or class. For instance:

```swift
let httpError = (404, "Not Found")
print("Error \(httpError.0): \(httpError.1)")
```

## What is optional type?
An optional is a type that can either hold a value or represent the absence of a value `nil`. Optionals are used to handle situations where a variable might not have a value, which helps prevent runtime errors by forcing you to safely manage the presence or absence of data.

### Declaring optionals
You declare an optional by appending a question mark `?` to the type of the variable. This indicates that the variable can either hold a value of that type or `nil`.

```swift
var name: String? // This is an optional String
```
In this example:
- `name` can either be a `String` or `nil`.

### Assigning and accessing optionals
You can assign a value or `nil` to an optional:

```swift
name = "John"  // name now holds a String value

name = nil     // name now holds nil
```
When accessing the value of an optional, you need to safely unwrap it because the optional might be `nil`.

## How to declare constants and variables?
Constants and variables are fundamental building blocks used to store values. You can declare them using the `let` keyword for constants and the `var` keyword for variables. Here's how you can declare and use them:

### Declaring constants
A constant is a value that, once set, cannot be changed. You declare constants using the `let` keyword.

```swift
let pi = 3.14159
let name = "John"
```
- `pi` is a constant with the value `3.14159`. Since it's a constant, you cannot change its value later in the code.
- `name` is a constant with the value `"John"`.

If you try to change the value of a constant, the Swift compiler will generate an error:
```swift
pi = 3.14 // Error: Cannot assign to value: 'pi' is a 'let' constant
```

### Declaring variables
A variable is a value that can change after it has been set. You declare variables using the `var` keyword.

```swift
var age = 25
var city = "New York"
```
- `age` is a variable initially set to `25`. You can change its value later in the code.
- `city` is a variable initially set to `"New York"`.

You can modify the value of a variable like this:
```swift
age = 26
city = "Los Angeles"
```

## How to provide type annotation?
You can provide a type annotation to explicitly specify the type of a constant, variable, function parameter, or return value. Type annotations are useful when you want to clarify the intended type or when Swift's type inference isn't enough to determine the type you want.

The syntax for type annotation is simple: you place a colon `:` followed by a space and the type after the variable or constant name.

### Examples of type annotations
When declaring constants or variables, you can provide a type annotation to specify the type explicitly:

```swift
let pi: Double = 3.14159
var name: String = "John"
var age: Int = 30
```
In these examples:
- `pi` is explicitly declared as a `Double`.
- `name` is explicitly declared as a `String`.
- `age` is explicitly declared as an `Int`.

## How to print constant or variable?
You can print the value of a constant or variable using the `print()` function. This function sends the output to the console, which is useful for debugging or displaying information to the user.

### Basic usage
```swift
let greeting = "Hello, World!"
print(greeting) // Outputs: Hello, World!
```
```swift
var age = 25
print(age) // Outputs: 25
```

### Printing multiple values
You can print multiple values at once by separating them with commas:
```swift
let name = "John"
let age = 30
print("Name:", name, "Age:", age) // Outputs: Name: John Age: 30
```
### String Interpolation
String interpolation is another common and powerful way to include the value of constants or variables inside a string. You use the backslash `\` followed by parentheses, placing the constant or variable inside the parentheses:
```swift
let name = "Alice"
let age = 28
print("My name is \(name) and I am \(age) years old.") 
// Outputs: My name is Alice and I am 28 years old.
```
### Print without a newline
By default, `print()` adds a newline character at the end of the output. If you want to print multiple values on the same line, you can set the `terminator` parameter to an empty string:

```swift
print("Hello", terminator: "")
print(" World!") 
// Outputs: Hello World!
```

## What is type safety and type inference?
Type safety and type inference are key features that contribute to the language's robustness and ease of use. These concepts help ensure that your code is reliable and less prone to errors, while also allowing you to write more concise code.

### Type safety
Type safety means that Swift is designed to prevent you from mixing or misusing types in your code. It ensures that you can only work with values in ways that make sense for their type. This helps catch errors at compile time, rather than at runtime, which makes your code safer and more predictable.

For example, if you try to assign a `String` to a variable that expects an `Int`, Swift will raise a compile-time error:

```swift
var age: Int = 25

age = "Twenty-five" // Error: Cannot assign value of type 'String' to type 'Int'
```
Type safety prevents such assignments, ensuring that values are always used in a way that is consistent with their declared types.

### Type inference
Type inference is the feature in Swift that allows the compiler to automatically determine the type of a variable or constant based on the value you assign to it. This means you don’t always need to explicitly specify the type, as Swift can infer it from the context.

For example, when you declare a variable or constant without explicitly providing a type, Swift uses the initial value to infer the type:

```swift
// Swift infers that 'message' is of type 'String'
let message = "Hello, World!"

// Swift infers that 'count' is of type 'Int'
var count = 10
```
In these examples:
- `message` is inferred to be of type `String` because it is assigned a string value.
- `count` is inferred to be of type `Int` because it is assigned an integer value.
Type inference makes your code cleaner and more concise, while still retaining the benefits of strong typing.

## How to define numeric literal?
Numeric literals are values that represent numbers directly in your code. Swift supports a variety of numeric literal formats, allowing you to define integers, floating-point numbers, and even numbers in different bases (binary, octal, hexadecimal).

### Example Code
Here's a small Swift example that shows various numeric literals:

```swift
let decimalInt = 42
let binaryInt = 0b101010
let octalInt = 0o52
let hexInt = 0x2A

let decimalFloat = 3.14159
let scientificFloat = 1.25e2
let hexadecimalFloat = 0xFp2

let largeNumber = 1_000_000
```
In this code:
- `decimalInt`, `binaryInt`, `octalInt` and `hexInt` demonstrate integer literals in different bases.

- `decimalFloat`, `scientificFloat` and `hexadecimalFloat` show floating-point literals in different formats.

- `largeNumber` illustrates the use of underscores to format a large number.

## What is type alias?
A type alias in Swift allows you to provide a new name, or alias, for an existing type. This can make your code more readable, help clarify the purpose of a type, or simplify complex type definitions. Type aliases don't create new types; they just provide an alternative name for an existing one.

### Defining a type alias
You define a type alias using the typealias keyword followed by the alias name and the type it represents.

```swift
typealias NewName = ExistingType
```

### Improving code readability
Type aliases can make code more readable by providing meaningful names:

```swift
typealias UserID = Int
typealias JSONDictionary = [String: Any]

let userId: UserID = 12345

let response: JSONDictionary = ["name": "John", "age": 30]
```
In this example:
- `UserID` is an alias for `Int`, making it clear that a particular integer represents a user ID.

- `JSONDictionary` is an alias for `[String: Any]`, a common type used to represent JSON data.

## What is optional binding?
Optional binding is a technique used to safely unwrap optionals. It allows you to check if an optional contains a value, and if so, assign that value to a temporary constant or variable. This is particularly useful because it ensures that you don't accidentally try to access a `nil` value, which would lead to a runtime error.

### How optional binding works
Optional binding is typically done using `if let` or `if var` statements, though it can also be done with `guard let` or `guard var` in some contexts. Here's how it works:
1. Check if the optional has a value: If the optional contains a value, it is unwrapped and assigned to the new constant or variable.
2. Use the unwrapped value: The unwrapped value can then be used within the block of code that follows the optional binding.

Syntax
```swift
if let constantName = optionalValue {
    // Use 'constantName' here, which is non-optional
} else {
    // The optional was nil
}
```

### Example with `if let`
```swift
let possibleNumber: String? = "123"

if let actualNumber = possibleNumber {
    print("The number is \(actualNumber).")
} else {
    print("The string does not contain a number.")
}
```

### Example with `guard let`
`guard let` is often used when you want to exit early if an optional is `nil`. This is particularly useful in functions:
```swift
func greet(name: String?) {
    guard let unwrappedName = name else {
        print("No name provided!")
        return
    }
    print("Hello, \(unwrappedName)!")
}

// Outputs: Hello, Alice!
greet(name: "Alice")

// Outputs: No name provided!
greet(name: nil)
```

## What is force unwrapping?
Force unwrapping is a way to access the value of an optional variable or constant that is assumed to have a non-nil value.
When you are certain that an optional contains a non-nil value, you can use the force unwrap operator `!` to directly access the value.

Here's a basic example:

```swift
var optionalString: String? = "Hello, world!"

let unwrappedString: String = optionalString!
print(unwrappedString)
```

However, force unwrapping should be used with caution. If the optional is `nil` and you try to force unwrap it, your program will crash with a runtime error.

## What is optional chaining?
Optional chaining allows you to call properties, methods, and subscripts on optionals that might currently be nil:

```swift
var optionalString: String? = "Cats are funny"

let stringLength = optionalString?.count  // stringLength is an Int?
print(stringLength)  // Prints Optional(14)
```

## What is nil-coalescing operator?
The nil-coalescing operator `??` provides a default value if the optional is `nil`:

```swift
var optionalString: String? = nil

let unwrappedString: String = optionalString ?? "Default value"
print(unwrappedString)  // Prints "Default value"
```

## How to do error handling?
Error handling in Swift is a robust and flexible system designed to handle errors gracefully. Swift uses a protocol called `Error` to represent error types.
Define an enumeration that conforms to the `Error` protocol to represent the different errors that might occur:
```swift
enum MyError: Error {
    case fileNotFound
}
```
Functions and methods can throw errors using the `throw` keyword. A function that can throw an error must be marked with the `throws` keyword.

```swift
func readFile(at path: String) throws -> String {
    // Simulating a condition where the file is not found
    throw MyError.fileNotFound
}
```
To handle errors, you use the `do-catch` statement. Within the `do` block, you write the code that can throw an error. The `catch` blocks handle specific errors.

```swift
do {
    let fileContent = try readFile(at: "path/to/file.txt")

    print(fileContent)
} catch MyError.fileNotFound {
    print("File not found")
} catch {
    print("An unexpected error occurred: \(error)")
}
```

### Summary
- Define error types by conforming to the `Error` protocol.
- Use `throw` to throw errors.
- Use `do-catch` to handle errors.
- Use `try` to call functions that can throw errors.
- Use `try?` to convert errors to optional values.
- Use `try!` to disable error propagation (with caution).

## How to debug with assertions in Swift?
Assertions are a powerful tool for debugging. They allow you to check for conditions that must be true at runtime and help catch bugs early in the development process. An assertion will cause your app to terminate if a specified condition evaluates to `false`, providing a message that helps you understand the cause of the failure.

The assert function is used to perform assertions. It takes a condition that must evaluate to true and an optional message that will be displayed if the condition is false.

```swift
let age = -3
assert(age >= 0, "Age cannot be negative")
// This will cause a runtime crash with the message "Age cannot be negative"
```
While `assert` is meant for debugging, precondition is similar but works in both debugging and production builds. Use `precondition` when you want to enforce that a condition must be true in all builds.

## What is `preconditionFailure` and `fatalError`
If you need to unconditionally fail, you can use `preconditionFailure` or `fatalError`. These functions terminate the program and can be used to mark code paths that should never be executed.
```swift
func process(input: String?) {
    guard let input = input else {
        preconditionFailure("Input should not be nil")
    }
    print("Processing \(input)")
}

// This will run normally
process(input: "Hello")

// This will trigger the precondition failure
process(input: nil)      
```

```swift
func unimplementedFunction() {
    fatalError("This function is not yet implemented")
}

// This will trigger the fatal error
unimplementedFunction()
```

### Summary
- `preconditionFailure`: Unconditionally triggers a failure in both debugging and production builds.
- `fatalError`: Unconditionally triggers a failure and indicates that code should not be executed.

## What are comparison operators?
Comparison operators in Swift are used to compare values. They return a Boolean value indicating whether the comparison is true or false. Here's a rundown of the comparison operators available:
1. Equal to (`a == b`) checks if two values are equal.
2. Not equal to (`!=`) checks if two values are not equal.
3. Greater than (`>`) checks if the left value is greater than the right value.
4. Less than (`<`) checks if the left value is less than the right value.
5. Greater than or equal to (`>=`) checks if the left value is greater than or equal to the right value.
6. Less than or equal to (`<=`) checks if the left value is less than or equal to the right value.

Swift allows you to define custom types and overload comparison operators to enable comparisons for your own types. Here's an example:
```swift
struct Person: Comparable {
    var name: String
    var age: Int
    
    static func < (lhs: Person, rhs: Person) -> Bool {
        return lhs.age < rhs.age
    }
    
    static func == (lhs: Person, rhs: Person) -> Bool {
        return lhs.age == rhs.age
    }
}

let person1 = Person(name: "Alex", age: 25)
let person2 = Person(name: "Bob", age: 30)

print(person1 < person2)  // true
print(person1 == person2) // false
```

## What are range operators?
Range operators in Swift are used to create ranges of values. These ranges can be useful in various scenarios such as iterating over a sequence of numbers or specifying a subset of elements in a collection. Swift provides three primary range operators:
- Closed Range (`...`) includes both the lower and upper bounds.
- Half-Open Range (`..<`) includes the lower bound but excludes the upper bound.
- One-Sided Ranges: Extend to one direction as far as possible (e.g., from a point to the end of a collection or from the start to a point).

```swift
let closedRange = 1...5
for number in closedRange {
    // Prints 1, 2, 3, 4, 5
    print(number)
}

let halfOpenRange = 1..<5

let array = [10, 20, 30, 40, 50]
// [30, 40, 50]
let subArray1 = array[2...]
```

## What is String interpolation?
String interpolation in Swift is a powerful and convenient way to construct new strings from a mix of constants, variables, literals, and expressions. Using string interpolation, you can insert values directly into the middle of a string literal, creating a combined string. This is done using a special syntax: wrapping the value or expression to be inserted inside `\(` and `)`.

The basic syntax of string interpolation is as follows:

```swift
let name = "Alice"
let age = 25
let greeting = "Hello, my name is \(name) and I am \(age) years old."

print(greeting)
// Output: Hello, my name is Alice and I am 25 years old.
```
You can also interpolate expressions directly within the string.
```swift
let pi = 3.14159

let formattedString = String(format: "The value of pi is approximately %.2f.", pi)

print(formattedString)
// Output: The value of pi is approximately 3.14.
```

## What are String indices?
Strings are collections of characters, and each character in a string has a specific position or index. However, unlike some other languages, Swift's String type does not use integer-based indices for accessing characters. Instead, it uses String.Index, a special type designed to handle Swift's extended grapheme clusters, which can represent complex characters composed of multiple Unicode scalars.

You can use ranges of indices to create substrings:
```swift
let text = "Hello, world!"
let startIndex = text.startIndex

let endIndex = text.index(startIndex, offsetBy: 5)

// "Hello"
let substring = text[startIndex..<endIndex]
```
### Summary
- String indices in Swift are of type `String.Index` to handle complex Unicode characters.
- Accessing characters requires using methods like `index(_:offsetBy:)`, `index(before:)`, and `index(after:)`.
- Creating substrings can be done using ranges of indices.
- Ensuring index bounds is important to avoid runtime errors.


## What are Substrings?
Substrings are slices of strings that provide a way to work with parts of a string without creating new string instances. This can be more efficient because substrings share storage with the original string, avoiding the overhead of allocating new memory.

You can create substrings using range operations on strings, such as slicing with indices:
```swift
let fullString = "Hello, Swift!"
let start = fullString.startIndex
let end = fullString.index(start, offsetBy: 5)
let substring = fullString[start..<end]
print(substring)  // Output: Hello
```
The type of `substring` in the example above is `Substring`, not `String`. This is important because `Substring` is designed to be a temporary view into the original string, sharing the same underlying storage.

## What are primary collection types?
Collections are essential data structures that allow you to store and manage groups of values. The primary collection types in Swift are:

1. **Arrays**. An array is an ordered collection of values. You can store multiple values of the same type in an array, and you can access them by their index. Arrays can grow and shrink dynamically.
```swift
var numbers: [Int] = [1, 2, 3, 4, 5]
let fruits = ["Apple", "Banana", "Cherry"]

```
2. **Dictionaries**. A dictionary is an unordered collection of key-value pairs. Each key is unique, and you use the key to access its corresponding value. Dictionaries are useful for storing data that needs to be associated with unique identifiers.
```swift
var studentGrades: [String: Int] = ["Alice": 90, "Bob": 85]

let capitals = ["USA": "Washington, D.C.", "France": "Paris"]
```
3. **Sets**. A set is an unordered collection of unique values. Sets are useful when you want to ensure that a collection contains no duplicates and when the order of elements is not important.
```swift
var uniqueNumbers: Set<Int> = [1, 2, 3, 4, 5]

let letters: Set<Character> = ["a", "b", "c"]
```

## What are fundamental `Set` operations?
You can efficiently perform fundamental set operations, such as combining two sets together, determining which values two sets have in common, or determining whether two sets contain all, some, or none of the same values.

- `intersection(_:)` method to create a new set with only the values common to both sets.

- `symmetricDifference(_:)` method to create a new set with values in either set, but not both.

- `union(_:)` method to create a new set with all of the values in both sets.

- `subtracting(_:)` method to create a new set with values not in the specified set.

## What are the available loops?
Swift provides several types of loops to handle different iteration requirements. Here are the primary loops available:
- **`for-in`** loop: Iterates over sequences like arrays, dictionaries, ranges, and strings.
```swift
let fruits = ["Apple", "Banana", "Cherry"]
for fruit in fruits {
    print(fruit)
}
```
- **`while`** loop: Continues as long as a condition is true.
```swift
var count = 1
while count <= 5 {
    print(count)
    count += 1
}
```
- **`repeat-while`** loop: Ensures the loop body is executed at least once.
```swift
var count = 1
repeat {
    print(count)
    count += 1
} while count <= 5
```

Loop control statements:
- **`break`** terminates the loop.
- **`continue`** skips the current iteration.

## What is `stride` used or?
The `stride` function allows for custom increments in loops.
```swift
for number in stride(from: 0, to: 10, by: 2) {
    print(number)
}
// Output:
// 0
// 2
// 4
// 6
// 8
```

## What's the difference in switch statements between Swift and Objective-C?
In Swift, the `switch` statement is more powerful and flexible. Each case can match complex conditions, including tuples, ranges, and where clauses. Also, there's no need for explicit break statements, as each case must terminate in some way (like using `return`, `continue`, or throwing an error).
```swift
let value = 3

switch value {
case 1:
    print("Value is 1")

case 2...5:
    print("Value is between 2 and 5")

case let x where x % 2 == 0:
    print("Value is an even number")

default:
    print("Value is something else")
}
```
In Objective-C, the `switch` statement is simpler and more C-like. Each case must explicitly terminate with a `break` statement (or other control flow statements like `return` or `goto`).

By default, Swift does not allow fallthrough from one case to the next. If you need fallthrough behavior, you must explicitly specify it using the `fallthrough` keyword.

In Objective-C, fallthrough is the default behavior if you do not include a `break` statement at the end of each case.

## What is switch case value binding?
This feature significantly enhances the flexibility of the `switch` statement, enabling you to work with complex data structures and perform pattern matching.

In a switch statement, you can bind values to constants or variables using the `let` or `var` keywords. This allows you to extract values from the matched pattern and use them within the case block.

```swift
let point = (2, 0)

switch point {
case (let x, 0):
    print("On the x-axis at \(x)")

case (0, let y):
    print("On the y-axis at \(y)")

case let (x, y):
    print("Somewhere else at (\(x), \(y))")
}
// Output: On the x-axis at 2
```

Value binding is particularly useful when working with enums that have associated values. Here's an example with an enum representing a barcode:
```swift
enum Barcode {
    case upc(Int, Int, Int, Int)
    case qrCode(String)
}

switch productBarcode {

case .upc(let numberSystem, let manufacturer, let product, let check):
    print("UPC: \(numberSystem), \(manufacturer), \(product), \(check)")

case .qrCode(let productCode):
    print("QR code: \(productCode)")
}

```
You can add conditions to the cases using `where` clauses. This allows for more precise matching based on the values of the variables.
```swift
let point = (3, 3)

switch point {

case let (x, y) where x == y:
    print("On the line x == y at (\(x), \(y))")

case let (x, y) where x == -y:
    print("On the line x == -y at (\(x), \(y))")

case let (x, y):
    print("At point (\(x), \(y))")
}
```

## What is deferred action?
Deferred action is a programming concept used to ensure that a block of code is executed at the end of the current scope, regardless of how the scope is exited. This is commonly achieved using the `defer` statement. The `defer` statement is useful for tasks like cleaning up resources, closing files, or releasing locks.

When you use `defer`, the enclosed block of code is guaranteed to run when the current scope (such as a function or method) exits, whether it exits normally or because of an error. Deferred actions are executed in the reverse order of their appearance in the code.

Here's a simple example to illustrate how defer works:

```swift
func exampleFunction() {
    defer {
        print("This is deferred code")
    }
    print("This is normal code")
}

exampleFunction()
// Output:
// This is normal code
// This is deferred code
```
Common use case is to ensure that temporary states are cleaned up, such as removing temporary files or resetting configurations.

`defer` ensures that cleanup code runs even if an error is thrown within the scope. This makes it particularly useful in functions that perform operations that might throw errors.

## How to check API availability?
You can check for API availability using the `#available` condition, which allows you to conditionally execute code based on the availability of a particular API or operating system version. This is particularly useful for ensuring compatibility with different versions of iOS, macOS, watchOS, or tvOS.

The following example shows how to execute code conditionally based on the iOS version:

```swift
if #available(iOS 14, *) {
    // Code that requires iOS 14 or later
    print("Running on iOS 14 or later")

} else {
    // Fallback code for earlier versions
    print("Running on an earlier version of iOS")
}
```
You can specify availability directly in function definitions to restrict the function to specific versions:

```swift
@available(iOS 14, *)
func useNewFeature() {
    // Code that uses a feature available in iOS 14 or later
}
```
Swift also allows you to use availability checking with property wrappers to ensure properties are only used on supported versions:
```swift
@available(iOS 14, *)
@propertyWrapper
struct AvailableOnlyOnIOS14<T> {
    var wrappedValue: T
}

struct Example {
    @AvailableOnlyOnIOS14 var feature: String = "New feature"
}
```

## How to define a function?
Defining a function in Swift involves specifying the `func` keyword followed by the function name, parameter list, return type (if any), and the function body.

A simple function with no parameters and no return value:

```swift
func greet() {
    print("Hello, World!")
}

// Calling the function
greet()
// Output: Hello, World!
```
A function that takes parameters:
```swift
func greet(person: String) {
    print("Hello, \(person)!")
}

// Calling the function
greet(person: "Alice")
// Output: Hello, Alice!
```
A function that returns a value:

```swift
func add(a: Int, b: Int) -> Int {
    return a + b
}

// Calling the function
let sum = add(a: 3, b: 5)
print(sum)  // Output: 8
```
A function that returns multiple values using a tuple:

```swift
func minMax(array: [Int]) -> (min: Int, max: Int) {
    guard let minElement = array.min(), let maxElement = array.max() else {
        return nil
    }
    return (minElement, maxElement)
}

// Calling the function
if let result = minMax(array: [1, 2, 3, 4, 5]) {
    print("Min is \(result.min), Max is \(result.max)")
}
// Output: Min is 1, Max is 5
```
A function that provides default values for parameters:
```swift
func greet(person: String, from hometown: String = "Unknown") {
    print("Hello, \(person)! From \(hometown).")
}
```

## How can you use function as type?
Functions can be used as types, meaning you can assign them to variables or use them as parameters to other functions.
```swift
func multiply(a: Int, b: Int) -> Int {
    return a * b
}

var mathFunction: (Int, Int) -> Int = multiply

// Calling the function via the variable
let result = mathFunction(3, 4)
print(result)  // Output: 12
```
Function as a parameter:
```swift
func printMathResult(_ mathFunction: (Int, Int) -> Int, _ a: Int, _ b: Int) {
    print("Result: \(mathFunction(a, b))")
}

// Passing a function as a parameter
printMathResult(multiply, 3, 4)
// Output: Result: 12
```

## How to omit function argument label?
If you don’t want an argument label for a parameter, write an underscore `_` instead of an explicit argument label for that parameter.
```swift
func someFunction(_ firstParameterName: Int, secondParameterName: Int) {
    // In the function body, firstParameterName and secondParameterName
    // refer to the argument values for the first and second parameters.
}
someFunction(1, secondParameterName: 2)
```
If a parameter has an argument label, the argument must be labeled when you call the function.

## What is variadic parameter?
A variadic parameter in Swift allows you to pass a variable number of arguments of the same type to a function. Variadic parameters are useful when you don't know in advance how many values will be passed into the function. You can specify a variadic parameter by appending three dots `...` to the parameter's type.
```swift
func sum(numbers: Int...) -> Int {
    var total = 0
    for number in numbers {
        total += number
    }
    return total
}

// Calling the function with a varying number of arguments
let result1 = sum(numbers: 1, 2, 3, 4, 5)
print(result1)  // Output: 15

let result2 = sum(numbers: 10, 20)
print(result2)  // Output: 30

let result3 = sum(numbers: 42)
print(result3)  // Output: 42
```
### Limitations
- Only One Variadic Parameter: A function can only have one variadic parameter.
- Type Safety: All arguments passed to the variadic parameter must be of the same type.

## What is `inout` parameter?
An in-out parameter allows a function to modify the value of a parameter and have that change reflected outside the function. This is useful when you need to pass a variable to a function, modify it within the function, and retain the modifications after the function call completes.

To declare an in-out parameter, you prefix the parameter type with the `inout` keyword. When calling the function, you prefix the variable with an ampersand `&`.

Here’s how to define and use a function with an in-out parameter:
```swift
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
    let temporaryA = a
    a = b
    b = temporaryA
}

var x = 3
var y = 5
swapTwoInts(&x, &y)
print("x is now \(x), y is now \(y)")  // Output: x is now 5, y is now 3
```
Changes to the in-out parameter inside the function affect the original variable outside the function.

## What is closure?
A closure in Swift is a self-contained block of functionality that can be passed around and used in your code. Closures can capture and store references to any constants and variables from the context in which they are defined, known as closing over those constants and variables. This enables you to write concise and expressive code.

Closures in Swift are similar to blocks in C and Objective-C, and to lambdas in other programming languages. They come in three forms:

1. Global functions are closures that have a name and do not capture any values.
2. Nested functions are closures that have a name and can capture values from their enclosing function.
3. Closure expressions are unnamed closures written in a lightweight syntax that can capture values from their surrounding context.

Here's the basic syntax:

```swift
{ (parameters) -> returnType in
    statements
}
```
Here's a simple example of a closure that takes two integers and returns their sum:
```swift
let sumClosure = { (a: Int, b: Int) -> Int in
    return a + b
}

let result = sumClosure(3, 5)
print(result)  // Output: 8
```

## What is trailing closure?
Trailing closure syntax in Swift allows you to write a closure expression outside of the parentheses of a function call if the closure is the final argument to that function. This can make your code more readable, especially when the closure is long or when a function has multiple parameters.

Consider a function that takes a closure as its last parameter:
```swift
func performOperation(a: Int, b: Int, operation: (Int, Int) -> Int) -> Int {
    return operation(a, b)
}
```
You can call this function using a trailing closure like this:
```swift
let result = performOperation(a: 4, b: 2) { (x, y) -> Int in
    return x + y
}
print(result)  // Output: 6
```

Trailing closures are particularly useful when:
- The closure is long and makes the function call more readable when placed outside the parentheses.
- The function has multiple parameters, and the closure is the last one.

For very simple closures, you can omit the parameter types and return type, using shorthand argument names:
```swift
let doubledShorthand = numbers.map { $0 * 2 }

print(doubledShorthand)  // Output: [2, 4, 6, 8, 10]
```

## How a closure can capture values?
Closures can capture and store references to variables and constants from the surrounding context in which they are defined. This ability to "capture" values makes closures powerful and flexible, allowing them to access and modify these values even after the original scope has gone out of existence.

When a closure captures a value, it means that the closure holds a reference to that value and can access or modify it later. This is particularly useful for scenarios like callback functions, asynchronous operations, or any case where the closure needs to retain state.

Here’s a simple example to demonstrate how closures capture values:

```swift
func makeIncrementer(incrementAmount: Int) -> () -> Int {
    var total = 0
    let incrementer: () -> Int = {
        total += incrementAmount
        return total
    }
    return incrementer
}

let incrementByTwo = makeIncrementer(incrementAmount: 2)

print(incrementByTwo())  // Output: 2

print(incrementByTwo())  // Output: 4

print(incrementByTwo())  // Output: 6
```

In this example:
- The `incrementer`closure captures the `total` and `incrementAmount` variables from the surrounding context of the `makeIncrementer` function.
- Each time the `incrementer` closure is called, it modifies the `total` variable, which retains its state between calls.

## What are strong and weak references in closures?
Strong and weak references are used to manage memory and prevent retain cycles when using closures. Understanding the difference between strong and weak references is crucial for effective memory management, especially when dealing with closures that capture references to objects.

### Strong references
A **strong reference** means that the reference to an object keeps the object alive as long as the reference itself exists. By default, closures capture variables and objects using strong references. If a closure captures self or other objects strongly, it can create a retain cycle (strong reference cycle), which prevents the objects from being deallocated.
```swift
class MyClass {
    var value = 10
    var closure: (() -> Void)?

    func setupClosure() {
        closure = {
            print(self.value)
        }
    }
}

let instance = MyClass()
instance.setupClosure()
```
In this example:
- The closure captures `self` strongly.
- If `instance` is assigned to a property of `closure`, a retain cycle is created, preventing both the `MyClass` instance and the closure from being deallocated.

### Weak references
A weak reference does not keep the object it references alive. This is useful to break retain cycles. When the object referenced by a weak reference is deallocated, the weak reference automatically becomes `nil`.

To avoid retain cycles, you can capture `self` (or other objects) weakly within a closure. This ensures that the closure does not keep a strong reference to the captured object, allowing it to be deallocated when there are no other strong references to it.
```swift
class MyClass {
    var value = 10
    var closure: (() -> Void)?

    func setupClosure() {
        closure = { [weak self] in
            guard let strongSelf = self else { return }
            print(strongSelf.value)
        }
    }
}

let instance = MyClass()
instance.setupClosure()
instance.closure?()  // Output: 10
```
In this example:
- The closure captures `self` weakly using `[weak self]`.
- `strongSelf` is used to safely unwrap `self` inside the closure.
- This prevents a retain cycle, allowing the `MyClass` instance to be deallocated when no other strong references exist.

### Unowned References
An `unowned` reference is similar to a weak reference but is used when you know that the referenced object will never be deallocated before the reference. If the referenced object is deallocated, accessing an `unowned` reference will cause a runtime crash.

Example with Unowned Reference
```swift
class MyClass {
    var value = 10
    var closure: (() -> Void)?

    func setupClosure() {
        closure = { [unowned self] in
            print(self.value)
        }
    }
}

let instance = MyClass()
instance.setupClosure()
instance.closure?()  // Output: 10
```
In this example:
- The closure captures self as `unowned`.
- Use `unowned` only when you are certain that `self` will not be deallocated before the closure is called.

## What is an escaping closure?
An escaping closure is a closure that can be executed after the function it was passed to has returned. To declare an escaping closure, you use the `@escaping` attribute in the function parameter. This is necessary because the closure can "escape" the scope of the function, meaning it can be called at a later time, such as in asynchronous operations, completion handlers, or when the closure is stored for later execution.

You need to mark a closure as `@escaping` when:
- The closure is stored in a property that exists outside the function's scope.
- The closure is passed to an asynchronous function.
- The closure is captured by another closure that is `@escaping`.

Here’s a simple example using an escaping closure in an asynchronous operation:
```swift
func performAsyncOperation(completion: @escaping () -> Void) {
    DispatchQueue.global().async {
        // Simulate a network request or other async operation
        sleep(2)  // Delay for 2 seconds
        completion()  // Call the completion handler
    }
}

performAsyncOperation {
    print("Async operation completed")
}
```
In this example:
- The `completion` closure is marked as `@escaping` because it is called after the `performAsyncOperation` function returns.
- The closure is executed after a delay, simulating an asynchronous operation.

Use `[weak self]` or `[unowned self]` to avoid strong reference cycles when capturing self.

## How to define stored closure?
You can define a stored closure by declaring a property of a closure type within a class or struct. This allows the closure to be stored and executed at a later time. Here’s a step-by-step guide on how to define and use a stored closure.

Step-by-Step Example:
1. **Declare the Closure Property**: Define a property in your class or struct to store the closure. The closure type includes the parameters and the return type.
2. **Assign the Closure**: Assign a closure to this property. This can be done directly or through a method.
3. **Execute the Closure**: Call the stored closure at the appropriate time.
```swift
class TaskManager {
    // Declare a closure property
    var completionHandler: (() -> Void)?

    // Method to assign the closure
    func setCompletionHandler(handler: @escaping () -> Void) {
        completionHandler = handler
    }

    // Method to execute the stored closure
    func performTask() {
        // Simulate a task
        print("Task is being performed")
        // Call the stored closure
        completionHandler?()
    }
}

let manager = TaskManager()

// Assign a closure to the completionHandler property
manager.setCompletionHandler {
    print("Task completed")
}

// Perform the task, which will eventually call the stored closure
manager.performTask()

// Output:
// Task is being performed
// Task completed
```

## What is autoclosure?
An `autoclosure` in Swift is a special type of closure that is automatically created to wrap an expression that's passed as an argument to a function. This can make code more concise and readable by allowing you to omit explicit closure syntax when passing expressions to functions that expect closures.

When you mark a function parameter with the `@autoclosure` attribute, Swift automatically wraps the provided expression in a closure. This means that the expression isn't evaluated until the closure is called, which can be useful for delaying evaluation or implementing custom control flow constructs.

Here's how you can define your own function with an @autoclosure parameter:
```swift
func logIfTrue(_ condition: @autoclosure () -> Bool, message: String) {
    if condition() {
        print(message)
    }
}

let isLoggedIn = false
logIfTrue(isLoggedIn, message: "User is logged in")
```
In this example:
- The `logIfTrue` function takes a condition marked with `@autoclosure`.
- The expression `isLoggedIn` is automatically wrapped in a closure that is evaluated within the function.

## `@autoclosure` and `@escaping`
By default, `@autoclosure` parameters are non-escaping, meaning the closure must be executed within the function body. If you need the closure to escape (be stored and called later), you must explicitly mark it with both `@autoclosure` and `@escaping`.

Example with `@autoclosure` and `@escaping`
```swift
var delayedClosures: [() -> Void] = []

func addDelayedClosure(_ closure: @autoclosure @escaping () -> Void) {
    delayedClosures.append(closure)
}

addDelayedClosure(print("This will be printed later"))

for closure in delayedClosures {
    closure()
}

// Output: This will be printed later
```
In this example:
- The `addDelayedClosure` function takes an `@autoclosure` and `@escaping` parameter.
- The expression `print("This will be printed later")` is wrapped in an escaping closure and stored in an array.
- The closure is executed later, printing the message.

### Summary
- `@autoclosure`: Automatically wraps an expression in a closure.
- **Use Case**: Useful for delaying evaluation and making function calls more concise and readable.
- **Syntax**: Mark the parameter with @autoclosure in the function definition.
- `@escaping`: Combine @autoclosure with @escaping if the closure needs to escape the function scope.

Using `@autoclosure` can simplify your code by reducing boilerplate and making function calls that involve expressions more natural to read and write.

## What are associated values?
Associated values allow you to store additional information alongside an enumeration case. This feature makes enums much more powerful and flexible, as they can carry varying types and amounts of data depending on the case. Associated values are specified at the time of defining an enum case and can be different for each case.

Here's an example of how to define and use enums with associated values:
```swift
enum NetworkResponse {
    case success(data: String)
    case failure(error: String)
    case timeout(seconds: Int)
}

let response1 = NetworkResponse.success(data: "Response Data")

let response2 = NetworkResponse.failure(error: "Network Error")

let response3 = NetworkResponse.timeout(seconds: 30)
```
You can access associated values using a `switch` statement, which allows you to extract and work with the data stored in each case:
```swift
switch response1 {
case .success(let data):
    print("Success with data: \(data)")
case .failure(let error):
    print("Failed with error: \(error)")
case .timeout(let seconds):
    print("Timeout after \(seconds) seconds")
}
```
In this example:
- The `switch` statement matches the `response1` variable against each case.
The associated value is extracted into a constant (`let data`, `let error`, `let seconds`) and used within the `case` block.

## What is recursive enumeration?
A recursive enumeration is an enumeration type that has one or more cases which can refer to the enumeration itself. This allows you to create data structures like trees or linked lists where elements can be nested within each other.

To define a recursive enumeration, you use the `indirect` keyword. This keyword can be applied to an individual case or to the entire enumeration to indicate that the cases can contain instances of the enumeration itself.

Here's an example of a simple recursive enumeration to represent an arithmetic expression:
```swift
enum ArithmeticExpression {
    case number(Int)

    indirect case addition(ArithmeticExpression, ArithmeticExpression)

    indirect case multiplication(ArithmeticExpression, ArithmeticExpression)
}
```

## What's the difference between `struct` and `class`?
`struct` and `class` are two fundamental building blocks for creating custom data types. While they share some similarities, there are key differences between them that influence how they are used and behave in different scenarios. Here’s a detailed comparison of `struct` and `class`:

Value Types vs. Reference Types
- **Structs**: Structs are value types. This means that when you assign a struct to a variable or pass it to a function, a copy of the struct is created. Changes to the copy do not affect the original instance.
- **Classes**: Classes are reference types. When you assign a class instance to a variable or pass it to a function, a reference to the same instance is created. Changes to the instance via any reference affect the original instance.

```swift
struct Point {
    var x: Int
    var y: Int
}

var point1 = Point(x: 0, y: 0)
var point2 = point1
point2.x = 10

print(point1.x) // Output: 0
print(point2.x) // Output: 10
```
In this example, `point2` is a copy of `point1`, so changing `point2` does not affect `point1`.

```swift
class Point {
    var x: Int
    var y: Int

    init(x: Int, y: Int) {
        self.x = x
        self.y = y
    }
}

var point1 = Point(x: 0, y: 0)
var point2 = point1
point2.x = 10

print(point1.x) // Output: 10
print(point2.x) // Output: 10
```
In this example, `point1` and `point2` both reference the same instance, so changing `point2` affects `point1`.

## Compare inheritance between `struct` and `class`
- **Structs**: Structs do not support inheritance. You cannot create a struct that inherits the properties and methods of another struct.
- **Classes**: Classes support inheritance. You can create a class that inherits from another class, gaining access to its properties and methods.

```swift
class Vehicle {
    var currentSpeed = 0.0
    
    func description() -> String {
        return "Traveling at \(currentSpeed) miles per hour"
    }
}

class Bicycle: Vehicle {
    var hasBasket = false
}

let bike = Bicycle()
bike.currentSpeed = 15.0
print(bike.description()) // Output: Traveling at 15.0 miles per hour
```

## Compare mutability between `struct` and `class`
- **Structs**: By default, structs are immutable when declared with `let`. You need to use `var` to make them mutable. Also, individual properties of a struct cannot be changed unless the struct itself is declared as `var`.

- **Classes**: Class instances are always mutable regardless of whether they are declared with `let` or `var`. However, properties within the class can be marked as `let` to make them immutable.

```swift
struct Point {
    var x: Int
    var y: Int
}

var point = Point(x: 0, y: 0)
point.x = 10 // Allowed

let fixedPoint = Point(x: 0, y: 0)
fixedPoint.x = 10 // Error: Cannot assign to property: 'fixedPoint' is a 'let' constant

class Point {
    var x: Int
    var y: Int

    init(x: Int, y: Int) {
        self.x = x
        self.y = y
    }
}

let point = Point(x: 0, y: 0)
point.x = 10 // Allowed
```

## Compare memory management between `struct` and `class`
- **Structs**: Structs are allocated on the stack, which generally makes them faster to allocate and deallocate. The actual behavior depends on the size of the struct and optimization performed by the compiler.

- **Classes**: Classes are allocated on the heap, and their memory management involves reference counting (ARC - Automatic Reference Counting) to manage the lifecycle of instances.

## Compare identity between `struct` and `class`
- **Structs**: Structs do not have an identity. Two structs with the same values are considered identical.

- **Classes**: Classes have an identity. Each instance of a class has its own identity, and even if two instances have the same property values, they are considered different.

```swift
struct Point {
    var x: Int
    var y: Int
}

let pointA = Point(x: 0, y: 0)
let pointB = Point(x: 0, y: 0)
print(pointA == pointB) // Output: true (with Equatable conformance)

class Point {
    var x: Int
    var y: Int

    init(x: Int, y: Int) {
        self.x = x
        self.y = y
    }
}

let pointA = Point(x: 0, y: 0)
let pointB = Point(x: 0, y: 0)
print(pointA === pointB) // Output: false
```

## When to use structs vs. classes?
### Use Structs When:
- You want value semantics.
- The data type is relatively simple and will not be subclassed.
- Instances of the data type need to be copied rather than referenced.

### Use Classes When:
- You need reference semantics.
- You need to use inheritance.
- You are working with more complex data structures that require identity.

### Summary
- **Structs**: Value types, no inheritance, stack allocation, no identity, immutable with `let`.
- **Classes**: Reference types, support inheritance, heap allocation, identity, always mutable but properties can be marked as immutable with `let`.

Choosing between structs and classes depends on the requirements of your application and the behavior you need for your data types.

## What are identity operators?
Identity operators are used to determine if two references (typically instances of classes) refer to the same memory location. These operators are particularly useful when working with reference types, such as classes, to check if two variables reference the exact same instance.

There are two identity operators in Swift:

1. `===` (Identity Operator)
- **Purpose**: Checks if two references point to the same instance.
- **Usage**: Returns true if both references point to the same instance, false otherwise.

2. `!==` (Non-identity Operator)
- **Purpose**: Checks if two references do not point to the same instance.
- **Usage**: Returns true if the references do not point to the same instance, false otherwise.

Here's a practical example to demonstrate how these operators work:
```swift
class Person {
    var name: String

    init(name: String) {
        self.name = name
    }
}

let personA = Person(name: "Alice")
let personB = Person(name: "Bob")
let personC = personA

// Identity operator (===)
if personA === personC {
    print("personA and personC are the same instance.")
} else {
    print("personA and personC are different instances.")
}

if personA === personB {
    print("personA and personB are the same instance.")
} else {
    print("personA and personB are different instances.")
}

// Non-identity operator (!==)
if personA !== personB {
    print("personA and personB are different instances.")
} else {
    print("personA and personB are the same instance.")
}
```

## What is lazy stored property?
A lazy stored property is a property whose initial value is not calculated until the first time it is accessed. This can be useful for properties that are computationally expensive to create or properties that depend on external conditions which may not be known until after an instance is initialized.

### Characteristics of lazy stored properties
- **Delayed Initialization**: The property’s initial value is not set until it is first accessed.
- **`lazy` keyword**: Declared with the `lazy` keyword.
- **Mutability**: Must always be declared with `var` because its value might not be set until after the instance’s initialization, and constant properties `let` must have their values set during initialization.
- **Storage**: Once initialized, the value is stored and reused on subsequent accesses.

Here's how to declare and use a lazy stored property:
```swift
class DataLoader {
    var data: String = "Data"

    func loadData() -> String {
        return "Loaded Data"
    }
}

class ViewController {
    var title: String

    lazy var dataLoader = DataLoader()
    
    init(title: String) {
        self.title = title
    }
}

let viewController = ViewController(title: "Home")
print("Before accessing dataLoader")
print(viewController.dataLoader.data) // The DataLoader instance is created here
```
In this example:
- The `dataLoader` property in ViewController is marked as lazy.
- The `DataLoader` instance is not created when ViewController is - initialized.
- The `DataLoader` instance is created the first time dataLoader is accessed.

## What are use cases of lazy stored properties?
### Use Cases
- **Expensive Computation**: When the initialization of a property involves expensive computations or resource loading (e.g., network requests, file I/O).
- **Dependency on External State**: When the property’s value depends on conditions that might change after initialization.
- **Avoiding Unnecessary Initialization**: When the property might not be used at all, avoiding unnecessary initialization can save resources.

Example with expensive computation:
```swift
class ComplexObject {
    init() {
        print("ComplexObject initialized")
    }
}

class Container {
    lazy var complexObject = ComplexObject()
    
    init() {
        print("Container initialized")
    }
}

let container = Container() // "Container initialized" is printed

print("Before accessing complexObject")

print(container.complexObject) // "ComplexObject initialized" is printed here
```
In this example:
- The `ComplexObject` initialization is deferred until `complexObject` is accessed for the first time.
- The output demonstrates that `ComplexObject` is not initialized during the `Container` initialization.

### Summary
- **Lazy Stored Property**: A property whose initial value is calculated only on first access.
- **Declaration**: Use the `lazy` keyword, must be a `var`.
- **Use Cases**: Useful for properties with expensive initialization, dependencies on external state, or properties that might not be used.

Lazy stored properties provide a way to optimize resource usage by delaying the creation of objects until they are actually needed. This can improve performance and reduce the memory footprint of your applications.

## What is computed property?
A computed property does not store a value directly. Instead, it provides a getter and optionally a setter to retrieve and set other properties or values indirectly. Computed properties are a way to add logic to the storage of property values.

### Characteristics
- **No Stored Value**: Computed properties do not store values. Instead, they compute the value every time it is accessed.
- **Getters and Setters**: Computed properties can have a getter and optionally a setter.
- **Var Declaration**: Computed properties must be declared with `var` because their values are not stored, but rather computed dynamically.

Here is the basic syntax for a computed property:

```swift
var propertyName: Type {
    get {
        // return some value
    }
    set(newValue) {
        // perform some action with newValue
    }
}
```
If the computed property is read-only, the `get` block can be omitted

## Whare are advantages of computed properties?
- **Encapsulation**: Encapsulate complex logic related to properties.
- **Derived Values**: Provide a way to derive values from other properties without storing them separately.
- **Validation**: Include validation logic in setters to ensure values meet certain criteria.

## Practical use cases

Temperature conversion
```swift
struct Temperature {
    var celsius: Double
    
    var fahrenheit: Double {
        get {
            return (celsius * 9 / 5) + 32
        }
        set {
            celsius = (newValue - 32) * 5 / 9
        }
    }
}

var temp = Temperature(celsius: 25)

print("Celsius: \(temp.celsius)") // Output: Celsius: 25.0

print("Fahrenheit: \(temp.fahrenheit)") // Output: Fahrenheit: 77.0

temp.fahrenheit = 100

print("New Celsius: \(temp.celsius)") // Output: New Celsius: 37.77777777777778
```
In this example, the `fahrenheit` property is a computed property with both a getter and a setter, allowing for temperature conversion between Celsius and Fahrenheit.

### Summary
- **Computed Properties**: Properties that compute their value every time they are accessed.
- **No Stored Value**: Unlike stored properties, they do not hold a value.
- **Getters and Setters**: Can include logic to compute the value (getter) and optionally set the value (setter).
- **Use Cases**: Useful for derived values, encapsulation, and adding logic to property access.

## What are property observers?
Property observers in Swift allow you to monitor and respond to changes in a property's value. They can be added to any stored property (except lazy properties) and to any property inherited from a superclass. Property observers come in two forms: `willSet` and `didSet`.

### Types of Property Observers
1. **`willSet`**: Called just before the value of the property is set. The new value is available as a parameter, with the default parameter name `newValue`.
1. **`didSet`**: Called immediately after the new value is set. The old value is available through the implicit parameter oldValue.

Here's the basic syntax for using property observers:
```swift
var propertyName: Type {
    willSet(newValue) {
        // code to execute before the value is set
    }
    didSet(oldValue) {
        // code to execute after the value is set
    }
}
```
If you don't need to use the parameter, you can omit it.

### Practical use cases
1. **Validating Input**: Ensure that a new value meets certain criteria before or after it is set.
2. **Synchronizing State**: Update related properties or perform additional setup when a property changes.
3. **Logging Changes**: Keep track of property changes for debugging or logging purposes.

## What is `mutating` keyword used for?
The `mutating` keyword is used in the context of value types (structs and enums) to indicate that a method can modify (mutate) the properties of the instance it belongs to. By default, methods in structs and enums cannot modify `self` or any of its properties because value types are immutable by nature. The `mutating` keyword explicitly allows the method to change the instance itself.

You use `mutating` when you want a method in a struct or enum to be able to modify the instance's properties or to assign a new instance to `self`. Here’s an example using a struct:
```swift
struct Point {
    var x: Int
    var y: Int

    mutating func moveBy(x deltaX: Int, y deltaY: Int) {
        x += deltaX
        y += deltaY
    }
}

var point = Point(x: 0, y: 0)
point.moveBy(x: 10, y: 20)

print(point)  // Output: Point(x: 10, y: 20)
```
### Explanation
- **Without `mutating`**: If you remove the `mutating` keyword, the `moveBy` method would produce a compiler error because it attempts to modify `self` (in this case, the `x` and `y` properties).
- **With `mutating`**: The `mutating` keyword allows the `moveBy` method to change the values of `x` and `y`, thereby modifying the instance.

You can also use `mutating` in enums when a method needs to modify `self`.

The `mutating` keyword provides controlled mutability for value types, ensuring that changes to instances are intentional and explicit.

## What are type methods?
Type methods are methods that are called on the type itself, rather than on an instance of the type. They are declared using the `static` keyword for value types (structs and enums) and the `class` keyword for classes (allowing subclasses to override the method).

### Key Concepts
- **Type methods**: Methods that operate at the type level, meaning they are associated with the type itself rather than with an instance of the type.
- **Static methods**: Declared with the `static` keyword, these methods cannot be overridden by subclasses when used in a class.
- **Class methods**: Declared with the `class` keyword, these methods can be overridden by subclasses.

Example with struct
```swift
struct MathUtility {
    static func square(_ number: Int) -> Int {
        return number * number
    }
}

let result = MathUtility.square(5)  // Output: 25
```
The `square` method is a type method because it is declared with `static`. You can call it directly on the `MathUtility` type without needing an instance.

## Compare type methods in structs, enums and classes
### Key points
1. Value types (structs and enums):
- Use the `static` keyword to define type methods.
- Type methods cannot be overridden in value types.
2. Reference types (classes):
- Use the `class` keyword to define type methods that can be overridden by subclasses.
- Use the `static` keyword if you do not want the method to be overridden.
3. Accessing type methods:
- Type methods are called on the type itself, not on instances. For example, `TypeName.methodName()`.

## How to prevent overrides?
You can prevent a method, property, or initializer from being overridden by subclasses by marking it with the `final` keyword. When you declare something as `final`, it cannot be overridden by any subclass, ensuring that the behavior defined in the superclass remains unchanged.

## Using `final` to prevent overrides
- **`final` keyword**: Prevents methods, properties, and initializers from being overridden in subclasses.
- **Methods**: Mark methods as `final` to prevent them from being overridden.
- **Properties**: Mark properties as `final` to prevent them from being overridden.
- **Initializers**: Mark initializers as `final` to prevent them from being overridden.
- **Classes**: Mark entire classes as `final` to prevent any subclassing.

Using `final` is a useful technique to enforce the integrity of your classes and ensure that specific methods, properties, or entire classes remain unchanged and cannot be extended or altered by subclasses.

## What is designated initializer?
A designated initializer is the primary initializer for a class that ensures all properties are fully initialized before the class is used. It is responsible for initializing all properties introduced by the class and calling the appropriate superclass initializer to ensure the superclass's properties are also initialized.

### Key characteristics
1. **Primary initializer**: Every class must have at least one designated initializer. It's the main initializer that handles the initialization of all properties introduced by the class and also calls an appropriate initializer of its superclass.
2. **Initialization chain**: A designated initializer must call a designated initializer from its superclass. This ensures that the initialization process is complete and all properties in the entire inheritance chain are properly initialized.
3. **Syntax**: Designated initializers are defined like any other initializer using the `init` keyword.

Here’s a simple example to illustrate the concept:
```swift
class Vehicle {
    var numberOfWheels: Int
    
    // Designated initializer
    init(numberOfWheels: Int) {
        self.numberOfWheels = numberOfWheels
    }
}
```

## What are rules for designated initializers?
- **Must call super**: A designated initializer must call a designated initializer of its immediate superclass.
- **Property initialization**: It must fully initialize all of its properties before calling the superclass initializer.
```swift
class Vehicle {
    var numberOfWheels: Int
    
    // Designated initializer
    init(numberOfWheels: Int) {
        self.numberOfWheels = numberOfWheels
    }
}

class Car: Vehicle {
    var color: String
    
    // Designated initializer
    init(numberOfWheels: Int, color: String) {
        self.color = color
        // Call the superclass's designated initializer
        super.init(numberOfWheels: numberOfWheels)
    }
}
```
### Explanation for Car class:
- The `Car` class, which inherits from `Vehicle`, introduces a new property `color`.
- The `Car` class's designated initializer `init(numberOfWheels:color:)` first initializes the `color` property.
- It then calls the superclass's designated initializer `super.init(numberOfWheels:)` to ensure that the `numberOfWheels` property is also initialized.

## How to indicate that a function, method, or initializer can throw an error?
You indicate that a function, method, or initializer can throw an error by adding the `throws` keyword in its declaration. When a function or method is marked with `throws`, it means that it can potentially throw an error during execution, and the calling code must handle this possibility either by using a `do-catch` block or by propagating the error further up the call stack with `try`, `try?`, or `try!`.

Here's how you declare a throwing function:
```swift
func someFunction() throws {
    // Code that might throw an error
}
```

## How to specifying an error type?
You can specify an error type by defining an enumeration (or sometimes a custom class or struct) that conforms to the `Error` protocol. This enumeration represents the different error conditions that your code might encounter. By specifying error types, you provide a clear and structured way to manage errors in your code.

Example: Defining an error type with an enumeration:
```swift
enum FileError: Error {
    case fileNotFound
    case unreadable
    case encodingFailed
}
```

## What is `guard` used for?
The `guard` keyword is used to perform early exits in functions, methods, or loops when certain conditions are not met. It's a powerful tool for controlling the flow of your code by ensuring that necessary conditions are satisfied before proceeding. If a condition is not met, the `guard` statement allows you to exit the current scope (e.g., return from a function or break out of a loop) immediately, avoiding deep nesting and making your code more readable.
```swift
guard condition else {
    // Exit the current scope, e.g., return, throw, break, continue
}
```

Guard with function return
```swift
func greet(person: String?) {
    guard let name = person else {
        print("No name provided.")
        return
    }
    
    print("Hello, \(name)!")
}
```

In this example:
- **Optional binding**: The `guard` statement checks if `person` is `nil`. If `person` is `nil`, the else block is executed, printing an error message and returning early from the function.
- **Unwrapped value**: If the condition is met, the unwrapped value `name` is available for use in the remainder of the function.

## What is type casting?
Type casting is the process of checking the type of an instance or converting it to another type within a class hierarchy. It allows you to treat an instance as either its own type, a superclass, or a subclass. Type casting is commonly used when working with heterogeneous collections, protocols, or when you need to work with a more specific type than what is currently available.

### Key concepts of type casting
- **Upcasting**: This is when you cast an instance to one of its superclasses or a protocol it conforms to. Upcasting is safe and doesn’t require a special keyword because it’s always valid.

- **Downcasting**: This is when you try to cast an instance to one of its subclasses or a specific type. Downcasting can fail if the instance isn’t actually of the type you’re trying to cast to, so Swift provides safe and forced downcasting operators.

## What are available type casting operators?
- **`is` operator**: Used to check if an instance is of a certain type. It returns a Boolean value.

- **`as?` operator**: Used for safe downcasting. It returns an optional value (`nil` if the downcast fails).

- **`as!` operator**: Used for forced downcasting. It attempts to downcast and will crash if the downcast fails.

- **`as` operator**: Used for upcasting or for bridging types (e.g., between Swift and Objective-C types). It's always safe.

## Example of using the `is` operator
```swift
class Animal {}
class Dog: Animal {}

let someAnimal: Animal = Dog()

if someAnimal is Dog {
    print("This animal is a Dog")
}
```
Here, `is` checks whether `someAnimal` is of type `Dog`. Since `someAnimal` is an instance of `Dog`, the condition is true.

## Example of using the `as?` operator (safe downcasting)
```swift
let someAnimal: Animal = Dog()

if let someDog = someAnimal as? Dog {
    print("This animal is definitely a Dog")
} else {
    print("This animal is not a Dog")
}
```
The `as?` operator tries to downcast `someAnima`l to `Dog`. If it succeeds, `someDog` is not `nil` and the downcast is successful.

## Example of using the `as!` operator (forced downcasting)
```swift
let someAnimal: Animal = Dog()
let someDog = someAnimal as! Dog
print("This animal is forced to be a Dog")
```
The `as!` operator forces the downcast. If `someAnimal` isn’t actually a `Dog`, this code would crash at runtime.

## Example of using the `as` operator (upcasting and type bridging)
```swift
class Animal {}
class Dog: Animal {}

let someDog = Dog()
let someAnimal: Animal = someDog as Animal // Upcasting

// Type bridging with as
let string = "Hello, Swift"
let nsString = string as NSString
```
- The `as` operator is used here to upcast `someDog` to `Animal`, which is always safe.

- The second example shows type bridging where a Swift `String` is cast to an `NSString`, a type from Objective-C.

## What is `try?` used for?
`try?` is used to handle error-throwing functions by converting the result into an optional. When you use `try?`, it attempts to execute a function that can throw an error, but it won't propagate the error or cause a crash if the function fails. Instead, it returns nil if an error occurs and the function fails, or it returns the result wrapped in an optional if the function succeeds.

### Key points:
- **Success**: If the operation succeeds, `try?` returns the result as an optional e.g., `Some(result)`.
- **Failure**: If an error is thrown, `try?` returns nil instead of propagating the error.

### Syntax
```swift
let result = try? someThrowingFunction()
```
### Example
Consider a function that can throw an error:

```swift
enum FileError: Error {
    case fileNotFound
}

func readFile(_ filename: String) throws -> String {
    if filename == "file.txt" {
        return "File content"
    } else {
        throw FileError.fileNotFound
    }
}

let fileContent = try? readFile("file.txt")
if let content = fileContent {
    print("File was read: \(content)")
} else {
    print("Failed to read the file.")
}
```
In this example:
- `readFile` is a function that may throw an error if the file name is not `"file.txt"`.

- Using `try?`, the readFile function is called, and if it succeeds, the file content is returned as an optional.

- If the file doesn't exist or some other error is thrown, `try?` returns `nil`, and the failure is handled without crashing the program.

## What is `try!` used for?
`try!` is used to execute a throwing function with the assumption that the function **will not throw an error**. If the function does throw an error at runtime, the program will crash. Essentially, `try!` tells the compiler: "I'm sure this function won't fail, so don't make me handle errors."

Because `try!` disables error handling, it's important to use it with caution, as any error thrown will result in a runtime crash.

### Syntax
```swift
let result = try! someThrowingFunction()
```
### Example
Consider a function that throws an error:

```swift
enum FileError: Error {
    case fileNotFound
}

func readFile(_ filename: String) throws -> String {
    if filename == "file.txt" {
        return "File content"
    } else {
        throw FileError.fileNotFound
    }
}

// Using try!
let fileContent = try! readFile("file.txt")
print(fileContent)
```
In this example:
- `readFile` is a function that may throw an error if the file name is not `"file.txt"`.

- The `try!` keyword is used because the programmer is confident that the file exists (in this case, `"file.txt"`).

- If the file exists, the content is printed.

- If the file doesn't exist (or any other error occurs), the program will crash.
