# Swift Advanced
Properties, subscripts, concurrency, type casting, nested types, extensions, protocols, generics, Combine framework

* [### What are property wrappers?](#What-are-property-wrappers)
* [### What are available built-in property wrappers?](#What-are-available-built-in-property-wrappers)
* [### What is `@Published` used for?](#What-is-Published-used-for)
* [### What is property wrapper projected value?](#What-is-property-wrapper-projected-value)
* [### What are subscripts?](#What-are-subscripts)
* [### What is convenience initializer?](#What-is-convenience-initializer)
* [### What are rules for convenience initializers?](#What-are-rules-for-convenience-initializers)
* [### What is failable initializer?](#What-is-failable-initializer)
* [### What is example usage of failable initializer?](#What-is-example-usage-of-failable-initializer)
* [### Why use failable initializers?](#Why-use-failable-initializers)
* [### What is `required` modifier used for?](#What-is-required-modifier-used-for)
* [### How to setup default property value with closure?](#How-to-setup-default-property-value-with-closure)
* [### What is asynchronous function?](#What-is-asynchronous-function)
* [### How to define asynchronous function?](#How-to-define-asynchronous-function)
* [### How to await asynchronous operation?](#How-to-await-asynchronous-operation)
* [### How to call asynchronous functions?](#How-to-call-asynchronous-functions)
* [### What are benefits of asynchronous functions?](#What-are-benefits-of-asynchronous-functions)
* [### What is asynchronous sequence?](#What-is-asynchronous-sequence)
* [### What is `AsyncSequence` protocol used for?](#What-is-AsyncSequence-protocol-used-for)
* [### How to iterate over an asynchronous sequence?](#How-to-iterate-over-an-asynchronous-sequence)
* [### Practical example: AsyncStream](#Practical-example-AsyncStream)
* [### What are use cases for asynchronous sequences?](#What-are-use-cases-for-asynchronous-sequences)
* [### How to call asynchronous functions in parallel?](#How-to-call-asynchronous-functions-in-parallel)
* [### What is a `Task`?](#What-is-a-Task)
* [### How to creaate a `Task`?](#How-to-creaate-a-Task)
* [### Structured vs. unstructured tasks](#Structured-vs-unstructured-tasks)
* [### What is a `TaskGroup`?](#What-is-a-TaskGroup)
* [### How to create `TaskGroup`?](#How-to-create-TaskGroup)
* [### Differences between `Task` and `TaskGroup`](#Differences-between-Task-and-TaskGroup)
* [### What is Task cancellation?](#What-is-Task-cancellation)
* [### How to check for Task cancellation?](#How-to-check-for-Task-cancellation)
* [### How to throw on cancellation?](#How-to-throw-on-cancellation)
* [### How to cancel a Task?](#How-to-cancel-a-Task)
* [### Task group cancellation](#Task-group-cancellation)
* [### How to use `CheckedContinuation`?](#How-to-use-CheckedContinuation)
* [### What is an Actor?](#What-is-an-Actor)
* [### How to define an actor?](#How-to-define-an-actor)
* [### How to use an actor?](#How-to-use-an-actor)
* [### Reentrancy in actors](#Reentrancy-in-actors)
* [### What are global actors?](#What-are-global-actors)
* [### How to define a global actor?](#How-to-define-a-global-actor)
* [### How to use a global actor?](#How-to-use-a-global-actor)
* [### Using global actor on functions or properties](#Using-global-actor-on-functions-or-properties)
* [### What is sendable type?](#What-is-sendable-type)
* [### How to define a Sendable type?](#How-to-define-a-Sendable-type)
* [### What is implicit conformance to `Sendable`?](#What-is-implicit-conformance-to-Sendable)
* [### Whar are non-sendable types?](#Whar-are-non-sendable-types)
* [### What is `@unchecked` used for?](#What-is-unchecked-used-for)
* [### What is macro?](#What-is-macro)
* [### What are `Any` and `AnyObject`?](#What-are-Any-and-AnyObject)
* [### What is `Any` used for?](#What-is-Any-used-for)
* [### What is `AnyObject` used for?](#What-is-AnyObject-used-for)
* [### Differences between `Any` and `AnyObject`](#Differences-between-Any-and-AnyObject)
* [### Type casting with `Any` and `AnyObject`](#Type-casting-with-Any-and-AnyObject)
* [### What are nested types?](#What-are-nested-types)
* [### Example of nested structures](#Example-of-nested-structures)
* [### Example of nested enumerations](#Example-of-nested-enumerations)
* [### Example of nested classes](#Example-of-nested-classes)
* [### What are extensions?](#What-are-extensions)
* [### Example of adding methods using extensions](#Example-of-adding-methods-using-extensions)
* [### Example of adding computed properties using extensions](#Example-of-adding-computed-properties-using-extensions)
* [### Example of protocol conformance using extensions](#Example-of-protocol-conformance-using-extensions)
* [### Example of adding initializers using extensions](#Example-of-adding-initializers-using-extensions)
* [### Example of extensions for protocols](#Example-of-extensions-for-protocols)
* [### Example of delegation: protocol and implementation](#Example-of-delegation-protocol-and-implementation)
* [### Example of delegation: delegating object](#Example-of-delegation-delegating-object)
* [### Common uses of delegation in iOS](#Common-uses-of-delegation-in-iOS)
* [### What is conditional conformance to a protocol?](#What-is-conditional-conformance-to-a-protocol)
* [### Example: Extending `Array` to conform to a protocol conditionally](#Example-Extending-Array-to-conform-to-a-protocol-conditionally)
* [### Example: Extending `Equatable` to a custom generic type](#Example-Extending-Equatable-to-a-custom-generic-type)
* [### Example: Conditional conformance with `Codable`](#Example-Conditional-conformance-with-Codable)
* [### How to limit protocol adoption to class types?](#How-to-limit-protocol-adoption-to-class-types)
* [### Example usage how to limit protocol adoption to class types](#Example-usage-how-to-limit-protocol-adoption-to-class-types)
* [### Why restrict protocol adoption to class types?](#Why-restrict-protocol-adoption-to-class-types)
* [### What is protocol composition?](#What-is-protocol-composition)
* [### What are advantages of protocol composition?](#What-are-advantages-of-protocol-composition)
* [### Optional protocol requirements](#Optional-protocol-requirements)
* [### What are generics?](#What-are-generics)
* [### Basic example of generics (functions)](#Basic-example-of-generics-functions)
* [### Generic types](#Generic-types)
* [### Generic constraints](#Generic-constraints)
* [### What are associated types?](#What-are-associated-types)
* [### Example of associated types](#Example-of-associated-types)
* [### Constraints on associated types](#Constraints-on-associated-types)
* [### Extensions with a generic `where` clause](#Extensions-with-a-generic-where-clause)
* [### Example: Extension with a generic `where` clause on a type](#Example-Extension-with-a-generic-where-clause-on-a-type)
* [### Example: Extension with a generic `where` clause on a protocol](#Example-Extension-with-a-generic-where-clause-on-a-protocol)
* [### What are opaque types?](#What-are-opaque-types)
* [### Opaque type vs. protocol type](#Opaque-type-vs-protocol-type)
* [### Example: Returning an opaque type](#Example-Returning-an-opaque-type)
* [### Example: Using opaque types with different types](#Example-Using-opaque-types-with-different-types)
* [### Benefits of opaque types](#Benefits-of-opaque-types)
* [### Opaque types use cases](#Opaque-types-use-cases)
* [### Comparison to boxed/existential types (`any`)](#Comparison-to-boxed-existential-types-any)
* [### What is boxed protocol type?](#What-is-boxed-protocol-type)
* [### Key characteristics of boxed protocol types](#Key-characteristics-of-boxed-protocol-types)
* [### What is type erasure?](#What-is-type-erasure)
* [### Example: Type erasure with a protocol](#Example-Type-erasure-with-a-protocol)
* [### Benefits of type erasure](#Benefits-of-type-erasure)
* [### Drawbacks of type erasure](#Drawbacks-of-type-erasure)
* [### Type erasure summary](#Type-erasure-summary)
* [### What's the difference between `self` and `Self`?](#What-s-the-difference-between-self-and-Self)
* [### The access levels](#The-access-levels)
* [### The access levels best practices](#The-access-levels-best-practices)
* [### Bitwise operators](#Bitwise-operators)
* [### Operator methods](#Operator-methods)
* [### Examples of operator methods: Addition operator `+`](#Examples-of-operator-methods-Addition-operator)
* [### Examples of operator methods: Equality operator `==`](#Examples-of-operator-methods-Equality-operator)
* [### Examples of operator methods: Custom prefix operator `-`](#Examples-of-operator-methods-Custom-prefix-operator)
* [### Custom operators](#Custom-operators)
* [### What is `@resultBuilder`?](#What-is-resultBuilder)
* [### Example: SwiftUI's `@ViewBuilder`](#Example-SwiftUI-s-ViewBuilder)
* [### Creating your own `@resultBuilder`](#Creating-your-own-resultBuilder)
* [### What is Combine framework?](#What-is-Combine-framework)
* [### How Combine works?](#How-Combine-works)
* [### Combine: example usage](#Combine-example-usage)
* [### Combine building blocks](#Combine-building-blocks)
* [### Combine real-world use cases](#Combine-real-world-use-cases)
* [### Combine advantages](#Combine-advantages)
* [### `Just` publisher](#Just-publisher)
* [### `Just` publisher usage and example](#Just-publisher-usage-and-example)
* [### When to use `Just`](#When-to-use-Just)
* [### `Future` publisher](#Future-publisher)
* [### `Future` publisher usage and example](#Future-publisher-usage-and-example)
* [### When to use `Future`](#When-to-use-Future)
* [### `PassthroughSubject` publisher](#PassthroughSubject-publisher)
* [### `PassthroughSubject` publisher usage and example](#PassthroughSubject-publisher-usage-and-example)
* [### When to use `PassthroughSubject`](#When-to-use-PassthroughSubject)
* [### `PassthroughSubject`: Comparison with `CurrentValueSubject`](#PassthroughSubject-Comparison-with-CurrentValueSubject)
* [### `CurrentValueSubject` publisher](#CurrentValueSubject-publisher)
* [### `CurrentValueSubject` publisher usage and example](#CurrentValueSubject-publisher-usage-and-example)
* [### When to use `CurrentValueSubject`](#When-to-use-CurrentValueSubject)
* [### `sink` subscriber](#sink-subscriber)
* [### `sink` example: Handling values and completion](#sink-example-Handling-values-and-completion)
* [### `sink` example: Handling only values](#sink-example-Handling-only-values)
* [### Memory management with `sink`](#Memory-management-with-sink)
* [### `assign` subscriber](#assign-subscriber)
* [### `assign` subscriber usage and example](#assign-subscriber-usage-and-example)
* [### When to use `assign`?](#When-to-use-assign)
* [### Combine: Transformation Operators](#Combine-Transformation-Operators)
* [### Combine: Filtering operators](#Combine-Filtering-operators)
* [### Combine: Combining operators](#Combine-Combining-operators)
* [### Combine: Sequence operators](#Combine-Sequence-operators)
* [### Combine: Time operators](#Combine-Time-operators)
* [### Combine: Error handling operators](#Combine-Error-handling-operators)
* [### Combine schedulers](#Combine-schedulers)
* [### Commonly used schedulers: DispatchQueue](#Commonly-used-schedulers-DispatchQueue)
* [### Commonly used schedulers: RunLoop](#Commonly-used-schedulers-RunLoop)
* [### Commonly used schedulers: OperationQueue](#Commonly-used-schedulers-OperationQueue)
* [### Combine: Using schedulers effectively](#Combine-Using-schedulers-effectively)
* [### `Deferred` publisher](#Deferred-publisher)
* [### `Deferred` publisher usage and example](#Deferred-publisher-usage-and-example)
* [### Why use `Deferred`?](#Why-use-Deferred)
* [### What is list's deep copy?](#What-is-list-s-deep-copy)
* [### List deep copy: For arrays of value types](#List-deep-copy-For-arrays-of-value-types)
* [### List deep copy: For arrays of reference types](#List-deep-copy-For-arrays-of-reference-types)
* [### List deep copy: Using protocol](#List-deep-copy-Using-protocol)
* [### List deep copy: Handling nested arrays](#List-deep-copy-Handling-nested-arrays)
* [### What does `eraseToAnyPublisher` do?](#What-does-eraseToAnyPublisher-do)
* [### How does `eraseToAnyPublisher` work?](#How-does-eraseToAnyPublisher-work)
* [### What are benefits of using `eraseToAnyPublisher`?](#What-are-benefits-of-using-eraseToAnyPublisher)
* [### What can be Combine `flatMap` operator used for?](#What-can-be-Combine-flatMap-operator-used-for)
* [### Combine `flatMap`: Chaining asynchronous operations](#Combine-flatMap-Chaining-asynchronous-operations)
* [### Combine `flatMap`: Handling multiple nested publishers](#Combine-flatMap-Handling-multiple-nested-publishers)
* [### Combine `flatMap`: Combining results from different publishers](#Combine-flatMap-Combining-results-from-different-publishers)
* [### Combine `flatMap`: Dynamic publishers based on emitted values](#Combine-flatMap-Dynamic-publishers-based-on-emitted-values)
* [### Combine `flatMap`: Summary](#Combine-flatMap-Summary)
* [### What can be Combine `compactMap` operator used for?](#What-can-be-Combine-compactMap-operator-used-for)
* [### What is `nonisolated` used for?](#What-is-nonisolated-used-for)
* [### Use cases for `nonisolated`](#Use-cases-for-nonisolated)
* [### Explain the difference between `Equatable` and `Comparable` protocols](#Explain-the-difference-between-Equatable-and-Comparable-protocols)
* [### What is `@inlinable`?](#What-is-inlinable)
* [### What is `@frozen`?](#What-is-frozen)
* [### When to use `@frozen`?](#When-to-use-frozen)
* [### What is `@MainActor`?](#What-is-MainActor)
* [### Key differences between `@MainActor` and `DispatchQueue.main.async`](#Key-differences-between-MainActor-and-DispatchQueue-main-async)
* [### Core Image](#Core-Image)
* [### Basic example using Core Image](#Basic-example-using-Core-Image)
* [### Core Image features](#Core-Image-features)
* [### Core Animation](#Core-Animation)
* [### Core Animation: CALayer](#Core-Animation-CALayer)
* [### Core Animation: Implicit animations](#Core-Animation-Implicit-animations)
* [### Core Animation: Explicit animations](#Core-Animation-Explicit-animations)
* [### Core Animation: Animation timing](#Core-Animation-Animation-timing)
* [### Core Animation: Transactions](#Core-Animation-Transactions)
* [### Core Animation: Keyframe animations](#Core-Animation-Keyframe-animations)
* [### Core Animation: Layer hierarchies](#Core-Animation-Layer-hierarchies)
* [### Core Animation: Transformations](#Core-Animation-Transformations)
* [### Core Animation: Core animation on the GPU](#Core-Animation-Core-animation-on-the-GPU)
* [### Core Animation types](#Core-Animation-types)
* [### Core Animation: Layer masking](#Core-Animation-Layer-masking)
* [### Core Animation: Replicating layers](#Core-Animation-Replicating-layers)
* [### Core Animation: Emitter layers](#Core-Animation-Emitter-layers)
* [### Core Animation: Delegates](#Core-Animation-Delegates)
* [### Core Animation: Performance considerations](#Core-Animation-Performance-considerations)
* [### Core Animation: Practical use cases](#Core-Animation-Practical-use-cases)
* [### AVFoundation](#AVFoundation)
* [### AVFoundation: `AVPlayer` and `AVPlayerLayer`](#AVFoundation-AVPlayer-and-AVPlayerLayer)
* [### AVFoundation: AVCaptureSession and Media Capture](#AVFoundation-AVCaptureSession-and-Media-Capture)
* [### AVFoundation: AVComposition and Media Editing](#AVFoundation-AVComposition-and-Media-Editing)
* [### AVFoundation: AVAssetExportSession](#AVFoundation-AVAssetExportSession)
* [### AVFoundation: Metadata Management](#AVFoundation-Metadata-Management)
* [### AVFoundation: Audio Processing](#AVFoundation-Audio-Processing)
* [### AVFoundation: Time-based media operations](#AVFoundation-Time-based-media-operations)
* [### AVFoundation: Real-time video effects](#AVFoundation-Real-time-video-effects)
* [### Best practices for AVFoundation](#Best-practices-for-AVFoundation)

## ### What are property wrappers?
Property wrappers provide a mechanism for encapsulating common property logic and behavior in a reusable way. They allow you to define a custom wrapper type that can add additional behavior to a property, such as validation, transformation, or synchronization.

### Key Concepts
- **Wrapper type**: A struct, class, or enum that defines the property wrapper.
- **`@propertyWrapper`** attribute: Used to declare a type as a property wrapper.
- **Wrapped property**: The property that uses the property wrapper.

A property wrapper is defined by marking a type with the `@propertyWrapper` attribute and defining a `wrappedValue` property that gets and sets the value.

Here’s a simple example of a property wrapper that clamps a value within a specified range:
```swift
@propertyWrapper
struct Clamped<Value: Comparable> {
    private var value: Value
    let range: ClosedRange<Value>

    var wrappedValue: Value {
        get { value }
        set { value = min(max(newValue, range.lowerBound), range.upperBound) }
    }

    init(wrappedValue: Value, range: ClosedRange<Value>) {
        self.value = min(max(wrappedValue, range.lowerBound), range.upperBound)
        self.range = range
    }
}

struct Rectangle {
    @Clamped(range: 0...100) var width: Int
    @Clamped(range: 0...100) var height: Int
}

var rect = Rectangle(width: 120, height: -10)

print(rect.width) // Output: 100 (clamped to the upper bound)

print(rect.height) // Output: 0 (clamped to the lower bound)

rect.width = 50
rect.height = 150

print(rect.width) // Output: 50 (within the range)

print(rect.height) // Output: 100 (clamped to the upper bound)
```
### Explanation
- **Property wrapper definition**: The `Clamped` struct is marked with the `@propertyWrapper` attribute. It has a private stored property `value`, a public `wrappedValue` property, and an initializer.
- **Using the Property Wrapper**: The `@Clamped` attribute is applied to the `width` and `height` properties in the `Rectangle` struct. The `wrappedValue` property handles getting and setting the clamped values.

## ### What are available built-in property wrappers?
Swift includes some built-in property wrappers, such as:
- `@State` (SwiftUI): Manages a view’s state.
- `@Published`: Automatically announces changes to a property.
- `@Environment` (SwiftUI): Accesses values stored in a view’s environment.
- `@AppStorage`: Wraps access to `UserDefaults`, automatically reading and writing values to it.

These built-in property wrappers streamline many common tasks in Swift, particularly in the development of modern, reactive, and declarative user interfaces with SwiftUI.

## ### What is `@Published` used for?
### `@Published`
- **Purpose**: Declares that a property in an `ObservableObject` should trigger a change notification when it changes. Useful in SwiftUI and Combine for automatically updating views or triggering other reactive programming behavior.
- **Usage**: Used in classes that conform to `ObservableObject`.
```swift
import Combine

class User: ObservableObject {
    @Published var name: String = "Alice"
}

let user = User()
let cancellable = user.$name.sink { newName in
    print("User name changed to \(newName)")
}

user.name = "Bob" // Output: "User name changed to Bob"
```

## ### What is property wrapper projected value?
A projected value is an additional value provided by a property wrapper, which can be accessed alongside the primary wrapped value. The projected value is typically used to expose supplementary information or functionality related to the property wrapper.

### How projected values work
- **Wrapped value**: The main value that the property wrapper manages. It is accessed using the property name.
- **Projected value**: An additional value provided by the property wrapper, accessed using the `$` prefix before the property name (e.g., `$propertyName`).

Let's consider a custom property wrapper that tracks whether a value has changed:

```swift
@propertyWrapper
struct TrackedValue<T> {
    private var value: T
    private(set) var hasChanged: Bool = false

    var wrappedValue: T {
        get { value }
        set {
            value = newValue
            hasChanged = true
        }
    }

    var projectedValue: Bool {
        return hasChanged
    }

    init(wrappedValue: T) {
        self.value = wrappedValue
    }
}

struct Example {
    @TrackedValue var number: Int = 0
}

var example = Example()

print(example.number) // Output: 0

print(example.$number) // Output: false (initially, hasChanged is false)

example.number = 42
print(example.number) // Output: 42

print(example.$number) // Output: true (hasChanged is now true)
```
### Explanation
- The `wrappedValue` property represents the main value (`number` in this case). It's accessed directly through `example.number`.
- The `projectedValue` property provides additional information (`hasChanged` in this case), which is accessed using `$example.number`.

## ### What are subscripts?
Subscripts are a feature that allows you to define a custom way to access elements of a collection, list, sequence, or any type you define, using the familiar square bracket syntax `[]`. Subscripts can be used to read and write values based on an index or other key, much like how you access elements in arrays or dictionaries.

The basic syntax for defining a subscript is:
```swift
subscript(parameters) -> ReturnType {
    get {
        // Return some value of ReturnType
    }
    set(newValue) {
        // Set some value of ReturnType
    }
}
```
- **Parameters**: Subscripts can take one or more parameters, which are used to determine how to access the element.
- **Return type**: The return type specifies the type of value the subscript returns.
- **`get` and `set`**: You can define a getter and an optional setter. If you only define a getter, the subscript is read-only.

Subscripts are a powerful feature that allows types to be indexed in a flexible and customizable way. They enable you to create intuitive and concise interfaces for accessing and modifying data within your types.

## ### What is convenience initializer?
A convenience initializer is a secondary initializer that provides a shortcut to initializing an instance of a class. It is typically used to offer alternative ways to initialize a class with default values or a simplified set of parameters. Unlike a designated initializer, a convenience initializer must call another initializer within the same class, either another convenience initializer or a designated initializer.

### Key characteristics
- **Simplification**: Convenience initializers are meant to simplify the initialization process by providing default values or fewer parameters than a designated initializer.

- **Delegation**: A convenience initializer must always delegate across to another initializer in the same class, either by calling a designated initializer or another convenience initializer.

- **`convenience` keyword**: Convenience initializers are marked with the `convenience` keyword, which differentiates them from designated initializers.

```swift
class Car {
    var numberOfWheels: Int
    var color: String
    
    // Designated initializer
    init(numberOfWheels: Int, color: String) {
        self.numberOfWheels = numberOfWheels
        self.color = color
    }
    
    // Convenience initializer
    convenience init(color: String) {
        self.init(numberOfWheels: 4, color: color)
    }
}

let myCar = Car(color: "Red")
print(myCar.numberOfWheels)  // Output: 4

print(myCar.color)           // Output: Red
```

The `convenience init(color:)` initializer provides a simplified way to create a `Car` instance by only specifying the color. It assumes a default of 4 wheels by calling the designated initializer `init(numberOfWheels:color:)` with `numberOfWheels` set to 4.

## ### What are rules for convenience initializers?
1. **Must call an initializer**: A convenience initializer must call another initializer in the same class. It cannot directly initialize any properties.

2. **Cannot be overridden**: Convenience initializers cannot be overridden in subclasses.

3. **Delegate across**: The convenience initializer must delegate the initialization process to a designated initializer or another convenience initializer, ensuring that all properties are properly initialized.

### When to use convenience initializers
- **Default values**: When you want to provide default values for certain properties without making the caller specify them.

- **Simplified initialization**: When initializing an object with a subset of parameters or providing an easier way to create an instance.

- **Multiple initialization options**: When a class needs multiple ways to be initialized, convenience initializers offer a flexible and clear approach.

## ### What is failable initializer?
A failable initializer is an initializer that can return `nil` if initialization fails. This is useful in situations where an object cannot be initialized with certain values or conditions, and you want to handle such failures gracefully.

Failable initializers are defined using the `init?` syntax. The `?` indicates that the initializer might return `nil`, making it an optional initializer.

```swift
class Person {
    var name: String
    
    // Failable initializer
    init?(name: String) {
        if name.isEmpty {
            return nil  // Initialization fails if the name is empty
        }
        self.name = name
    }
}
```

## ### What is example usage of failable initializer?
### Example usage
```swift
let validPerson = Person(name: "John")

if let person = validPerson {
    print("Person created with name: \(person.name)")
} else {
    print("Failed to create person")
}

let invalidPerson = Person(name: "")

if let person = invalidPerson {
    print("Person created with name: \(person.name)")
} else {
    print("Failed to create person")  // Output: Failed to create person
}
```
### Explanation
- **Failable initialization**: The `init?(name:)` initializer checks if the `name` is empty. If it is, the initializer returns `nil`, indicating failure. Otherwise, it initializes the `name` property.

- **Handling the result**: When using a failable initializer, the result is an optional. You need to unwrap it using `if let`, `guard let`, or optional chaining to check if the initialization was successful.

## ### Why use failable initializers?
1. **Invalid input handling**: When certain input values should prevent an object from being created, a failable initializer lets you enforce that constraint.

2. **Error Avoidance**: It avoids using implicitly unwrapped optionals or force unwrapping, which can lead to runtime crashes if not handled properly.

3. **Safeguarding against invalid states**: It ensures that instances are only created if all conditions for a valid object are met.

In enumerations, failable initializers can be used to match raw values or to return `nil` for invalid cases.

You can also define a failable initializer with `init!`, which returns an implicitly unwrapped optional. This can be useful when you want the initializer to fail, but you don’t want to handle the optional every time.

Failable initializers are a powerful feature that helps you write safer, more robust code by handling invalid initialization scenarios gracefully.

## ### What is `required` modifier used for?
The `required` modifier is used to indicate that a subclass must implement a particular initializer. When an initializer is marked with required, all subclasses of the class are required to provide their own implementation of this initializer, either by inheriting it or by providing a custom implementation.

## Key points
1. **Forces subclass implementation**: Any class that inherits from a class with a `required` initializer must implement that initializer.

2. **Inherits automatically**: If a subclass does not provide its own implementation of the required initializer, it automatically inherits the one from the superclass.

3. **Used with designated initializers**: The `required` modifier is typically used with designated initializers, ensuring that all subclasses implement the initializer in a consistent way.

Here’s the basic syntax for using the required modifier:
```swift
class SomeClass {
    required init() {
        // initializer implementation
    }
}

class SubClass: SomeClass {
    // Must implement the required initializer, either explicitly or by inheriting it
    required init() {
        // Custom implementation or call to super.init()
        super.init()
    }
}
```

The `required` modifier is a powerful tool for enforcing consistent behavior across class hierarchies, ensuring that all subclasses provide the necessary initializers.

## ### How to setup default property value with closure?
You can set up a default property value using a closure. This is particularly useful when the property’s initial value requires some setup or computation that cannot be easily expressed as a simple literal. The closure is executed immediately to initialize the property, and its result is used as the initial value.

```swift
class MyClass {
    let someProperty: Int = {
        // Some setup or computation
        let value = 42
        return value
    }()
}
```

### Explanation
- **Closure block**: The closure `{ ... }` is defined to encapsulate the setup logic. The closure must return a value of the property’s type (in this case, `Int`).
- **Immediate execution**: The closure is followed by `()`, which indicates that the closure is immediately executed to produce the initial value for the property.
- **Stored property**: The result of the closure is stored as the initial value of `someProperty`


## ### What is asynchronous function?
An asynchronous function allows you to perform tasks that might take some time to complete, such as network requests, file I/O, or complex computations, without blocking the main thread. By marking a function as asynchronous, you enable it to perform work in the background and return a result later, allowing the rest of your code to continue running in the meantime.

### Key concepts
- **Asynchronous execution**: An asynchronous function can start a task that runs in the background, freeing up the main thread (or calling thread) to handle other tasks concurrently.
- **Suspension points**: Asynchronous functions can be suspended and resumed at specific points, allowing them to wait for asynchronous operations (like network requests) to complete without blocking the entire function.
- **Concurrency**: Asynchronous functions are a fundamental part of writing concurrent code, enabling multiple tasks to be performed at the same time.

## ### How to define asynchronous function?
Asynchronous functions are defined using the async keyword:
```swift
func fetchData() async -> String {
    // Asynchronous code here
    return "Data"
}
```

## ### How to await asynchronous operation?
Within an asynchronous function, you can call other asynchronous functions using the `await` keyword. The `await` keyword indicates that the function will be suspended at this point until the asynchronous operation completes.

Example
```swift
func fetchData(from url: String) async throws -> Data {
    let url = URL(string: url)!
    let (data, _) = try await URLSession.shared.data(from: url)
    return data
}
```
In this example:
- **`async` keyword**: The `fetchData(from:)` function is marked as `async`, meaning it can be suspended and resumed later.
- **`await` keyword**: The `try await` statement is used to wait for the data task to complete. The function will be suspended until the data is received.
- **Error handling**: The function is also marked with `throws`, indicating it can throw an error if something goes wrong, like a network failure.

## ### How to call asynchronous functions?
Asynchronous functions must be called from within another asynchronous context, typically within an `async` function or concurrency context like a `Task`.

```swift
func processData() async {
    do {
        let data = try await fetchData(from: "https://example.com/data")
        print("Data received: \(data)")
    } catch {
        print("Failed to fetch data: \(error)")
    }
}

Task {
    await processData()
}
```
In this example:
- **Asynchronous context**: The `processData()` function is an asynchronous function that calls the `fetchData(from:)` function using `await`.
- **Task**: The `processData()` function is executed within a `Task`, which provides the necessary asynchronous context for running `async` functions in a non-asynchronous environment (like main() or a synchronous method).

## ### What are benefits of asynchronous functions?
- **Non-blocking operations**: Asynchronous functions allow potentially long-running operations to be performed without freezing the user interface or blocking other tasks.
- **Improved performance**: By enabling concurrent execution, asynchronous functions help make better use of system resources, improving the overall performance and responsiveness of your application.
- **Simpler code**: Structured concurrency model, which includes `async` and `await`, allows you to write asynchronous code that is easier to read, understand, and maintain compared to traditional callback-based or closure-based asynchronous code.

### Summary
- **Asynchronous functions (`async`)**: These functions allow you to perform tasks in the background without blocking the main thread.
- **`await` keyword**: Used to pause execution until an asynchronous operation completes.
- **Concurrency**: Asynchronous functions enable concurrent execution, leading to more responsive and efficient code.
- **Error handling**: Asynchronous functions can also throw errors, which must be handled appropriately.

Asynchronous functions are a key feature in modern Swift programming, allowing developers to handle asynchronous tasks in a clean, structured, and efficient manner.

## ### What is asynchronous sequence?
An asynchronous sequence is a type that conforms to the `AsyncSequence` protocol, allowing you to iterate over a sequence of values that are produced asynchronously. This is particularly useful when you want to work with a series of values that arrive over time, such as values from a network stream, user input events, or data being read from a file in chunks.

### Key concepts
- **Asynchronous sequence**: A sequence where the elements are produced or fetched asynchronously, meaning each element might take some time to become available.
- **Iteration with for `await`**: You can iterate over an asynchronous sequence using a `for await` loop, which suspends the loop's execution until the next element is available.

## ### What is `AsyncSequence` protocol used for?
The `AsyncSequence` protocol defines the interface for an asynchronous sequence. A type conforming to `AsyncSequence` must provide an `AsyncIterator` that produces values asynchronously.

Here's a simple example of creating an asynchronous sequence:
```swift
struct CountdownAsyncSequence: AsyncSequence {
    typealias Element = Int
    
    let start: Int
    
    struct AsyncIterator: AsyncIteratorProtocol {
        var current: Int
        
        mutating func next() async -> Int? {
            guard current > 0 else { return nil }
            let value = current
            current -= 1
            return value
        }
    }
    
    func makeAsyncIterator() -> AsyncIterator {
        return AsyncIterator(current: start)
    }
}
```
In this example:
- **`CountdownAsyncSequence`**: A custom asynchronous sequence that counts down from a starting value to zero.
- **`AsyncIterator`**: The iterator conforms to `AsyncIteratorProtocol` and provides the `next()` method, which asynchronously returns the next value in the sequence.
- **`makeAsyncIterator()`**: This method returns an instance of AsyncIterator, allowing you to iterate over the sequence asynchronously.

## ### How to iterate over an asynchronous sequence?
You can iterate over an `AsyncSequence` using the for `await loop`, which suspends execution until the next element is available:

```swift
let countdown = CountdownAsyncSequence(start: 5)

for await number in countdown {
    print("Countdown: \(number)")
}
```

## ### Practical example: AsyncStream
In real-world applications, you might use `AsyncStream` to create an asynchronous sequence. `AsyncStream` allows you to bridge the gap between callback-based code and structured concurrency model.

```swift
func fetchNumbers() -> AsyncStream<Int> {
    AsyncStream { continuation in
        for i in 1...5 {
            continuation.yield(i)

            try? await Task.sleep(nanoseconds: 1_000_000_000)  // Simulating async work
        }
        continuation.finish()
    }
}

Task {
    for await number in fetchNumbers() {
        print("Received number: \(number)")
    }
}
```
In this example:
- **`fetchNumbers`**: This function returns an `AsyncStream` that produces numbers from 1 to 5, with a simulated delay between each number.
- **`for await` loop**: The numbers are received asynchronously in a `for await` loop, demonstrating how you can process values as they become available.

## ### What are use cases for asynchronous sequences?
- **Networking**: Streaming data from a server, such as a WebSocket connection or downloading large files in chunks.
- **User input**: Handling asynchronous input events, such as button presses, text input, or gestures.
- **Real-time data**: Processing live data feeds, such as sensor data, stock prices, or real-time notifications.

### Summary
- **Asynchronous sequences**: Represent sequences of values that are produced asynchronously, allowing for non-blocking iteration over values that arrive over time.
- **`AsyncSequence` protocol**: Defines the structure of an asynchronous sequence, requiring an AsyncIterator.
- **`for await` loop**: Used to iterate over asynchronous sequences, suspending the loop until the next value is available.
- **Use cases**: Useful in scenarios where data is received or produced over time, such as network streams, user input, or real-time data processing.

Asynchronous sequences are a powerful feature in Swift's concurrency model, enabling you to work with sequences of asynchronously produced values in a clean, structured, and efficient way.

## ### How to call asynchronous functions in parallel?
You can call asynchronous functions in parallel using several approaches, with `async let` being one of the most common and straightforward methods. This allows you to run multiple asynchronous tasks concurrently, improving the performance of your application by making better use of system resources.

The `async let` syntax allows you to create and run multiple asynchronous tasks in parallel, and then await their results later.

Here's an example of how to call asynchronous functions in parallel:
```swift
func fetchAllData() async {
    // Run the asynchronous functions in parallel
    async let image = fetchImage()
    async let userData = fetchUserData()
    async let posts = fetchPosts()

    // Await their results
    let (imageResult, userDataResult, postsResult) = await (image, userData, posts)
    
    print("Fetched image: \(imageResult)")
    print("Fetched user data: \(userDataResult)")
    print("Fetched posts: \(postsResult)")
}

Task {
    await fetchAllData()
}
```
In this example:
- **`async let`**: Each `async let` statement starts an asynchronous task in parallel. The tasks run concurrently without waiting for each other to complete.
- **`await`**: Later in the code, you use `await` to get the results of these tasks. The `await` statement will suspend the execution until the respective task is completed.
- **Efficiency**: By running these tasks in parallel, the total time to fetch all data is reduced compared to running them sequentially.

## ### What is a `Task`?
A `Task` represents a unit of work that runs asynchronously. You can think of it as a lightweight thread that can perform some work in the background, allowing your code to run concurrently. Tasks can be created to execute code that doesn't block the main thread, making your app more responsive.

### Key features of `Task`:
- **Asynchronous execution**: A `Task` can execute code asynchronously, meaning it can run concurrently with other tasks or the main thread.
- **Automatic cancellation**: Tasks can be canceled automatically if their parent task is canceled, helping manage resource use and avoid unnecessary work.
- **Isolation**: Tasks help in isolating mutable state by default, which reduces data races and makes concurrent code safer.

## ### How to creaate a `Task`?
You create a task by calling the Task initializer, usually from within an asynchronous context or directly from synchronous code.

Example:
```swift
Task {
    // This code runs concurrently with other tasks
    let result = await fetchData()
    print("Fetched data: \(result)")
}
```
In this example, the `Task` runs the `fetchData()` function asynchronously, allowing the code following the `Task` creation to continue executing without waiting for `fetchData()` to complete.

## ### Structured vs. unstructured tasks
- **Structured task**: A task that is part of the existing hierarchy of tasks, such as one created with `async let` or in a `TaskGroup`. It inherits the cancellation and priority of its parent task.
- **Unstructured task**: A standalone task, not linked to the current task hierarchy. Created using `Task {}` or `Task.detached`. These tasks do not automatically inherit cancellation from their parent context.

Example of an unstructured task:
```swift
Task.detached {
    // This runs independently from the surrounding context
    let result = await fetchData()

    print("Detached task fetched: \(result)")
}
```

## ### What is a `TaskGroup`?
A `TaskGroup` allows you to create a group of tasks that can run concurrently and be managed together. You use `TaskGroup` when you need to run multiple asynchronous tasks concurrently and handle their results as they complete.

### Key features of `TaskGroup`:
- **Dynamic task creation**: You can add tasks to a group dynamically, and these tasks can run concurrently.
- **Result collection**: As tasks in the group complete, you can collect and process their results.
- **Cancellation propagation**: If the group is canceled, all tasks within the group are also canceled.

## ### How to create `TaskGroup`?
You use the `withTaskGroup` function to create a `TaskGroup` and manage tasks within it.

Example:
```swift
func fetchAllData() async {
    await withTaskGroup(of: String.self) { group in
        group.addTask { await fetchData1() }
        group.addTask { await fetchData2() }
        group.addTask { await fetchData3() }

        for await result in group {
            print("Fetched data: \(result)")
        }
    }
}
```
In this example:
- **`withTaskGroup`**: Initializes a task group where you can add tasks that run concurrently.
- **Dynamic task addition**: Tasks are added to the group using `group.addTask { }`.
- **Result collection**: The results of the tasks are collected and processed as they complete, in the order they finish.

## ### Differences between `Task` and `TaskGroup`
- **`Task`**: Represents a single unit of asynchronous work. Use it when you need to run a single operation asynchronously.

- **`TaskGroup`**: Represents a collection of tasks that run concurrently and are managed together. Use it when you have multiple operations that can run in parallel and need to manage them as a group.

These constructs help in writing clean, efficient, and responsive code in Swift, taking full advantage of the language's concurrency model.

## ### What is Task cancellation?
Task cancellation is a mechanism that allows you to stop a running task before it completes. This is particularly useful in scenarios where you no longer need the result of a task or if continuing the task would be wasteful, such as when a user navigates away from a screen, or when an operation takes too long and you want to timeout.

### How Task cancellation works
- **Cooperative cancellation**: Task cancellation is cooperative, meaning the task needs to regularly check whether it has been canceled and then respond appropriately. The system will not forcefully stop the task; instead, the task itself must stop its work when it detects that it has been canceled.

- **Cancellation propagation**: If a task is part of a task hierarchy (e.g., tasks within a `TaskGroup` or child tasks created with `async let`), cancellation of the parent task will propagate down to its child tasks.

## ### How to check for Task cancellation?
A task can check if it has been canceled by calling `Task.isCancelled`. If the task has been canceled, `Task.isCancelled` will return `true`, and the task can then decide to stop execution.

Example of checking for cancellation
```swift
func performWork() async {
    for i in 1...10 {
        // Check if the task has been canceled
        if Task.isCancelled {
            print("Task was canceled")
            return
        }
        
        print("Performing step \(i)")
        try? await Task.sleep(nanoseconds: 500_000_000)  // Simulate work
    }
    print("Task completed")
}
```
In this example, the task periodically checks `Task.isCancelled` during its loop. If the task has been canceled, it prints a message and returns early.

## ### How to throw on cancellation?
Instead of just returning when a task is canceled, you can also throw an error to indicate that the task did not complete successfully due to cancellation. Swift provides a `CancellationError` for this purpose.

```swift
func performCancelableWork() async throws {
    for i in 1...10 {
        try Task.checkCancellation()  // Throws a CancellationError if the task was canceled
        
        print("Performing step \(i)")
        try? await Task.sleep(nanoseconds: 500_000_000)  // Simulate work
    }
    print("Task completed")
}

Task {
    do {
        try await performCancelableWork()
    } catch is CancellationError {
        print("Task was canceled and threw an error")
    } catch {
        print("An unexpected error occurred: \(error)")
    }
}
```
In this example:
- **`Task.checkCancellation()`**: This method checks for cancellation and automatically throws a `CancellationError` if the task was canceled.

- **Error Handling**: The task's caller can catch the `CancellationError` to handle the cancellation appropriately.

## ### How to cancel a Task?
You can cancel a task by calling its `cancel()` method. If you're within the task itself, you typically handle cancellation by checking `Task.isCancelled` or using `Task.checkCancellation()`.

```swift
let task = Task {
    await performWork()
}

// Cancel the task after a delay
Task {
    try? await Task.sleep(nanoseconds: 1_000_000_000)  // Wait 1 second

    task.cancel()
    print("Task was requested to cancel")
}
```
In this example:
- **Task creation**: A task is created to perform some work.

- **Cancellation**: A second task cancels the first task after 1 second, causing the first task to stop its work early.

## ### Task group cancellation
In a `TaskGroup`, if any task fails or if the group itself is canceled, all remaining tasks in the group are also canceled.

```swift
await withTaskGroup(of: Void.self) { group in
    group.addTask {
        try await performCancelableWork()
    }
    group.addTask {
        try await performCancelableWork()
    }
    
    // Simulate a condition to cancel the group
    group.cancelAll()  // This cancels all tasks in the group
}
```
In this example, `group.cancelAll()` cancels all tasks that are currently running within the `TaskGroup`.

## ### How to use `CheckedContinuation`?
One approach to receive a notification of task cancellation is to use a `CheckedContinuation`. This allows you to create a point in your code where the task can be resumed or notified about cancellation.

```swift
import Foundation

func performCancelableWork() async {
    await withCheckedContinuation { (continuation: CheckedContinuation<Void, Never>) in
        let task = Task {
            while !Task.isCancelled {
                print("Working...")
                try? await Task.sleep(nanoseconds: 500_000_000)  // Simulate work
            }
            print("Task was canceled")
            continuation.resume()
        }
        
        Task {
            // Simulate some external condition that triggers cancellation
            try? await Task.sleep(nanoseconds: 2_000_000_000)  // Wait 2 seconds
            task.cancel()
        }
    }
}

Task {
    await performCancelableWork()
    print("Received cancellation notification")
}
```
In this example:
- **`CheckedContinuation`**: Used to suspend the execution until the task is either completed or canceled. When the task is canceled, the `continuation.resume()` is called to notify that the task was canceled.

- **Notification**: After the task is canceled and `continuation.resume()` is called, the code following the `await performCancelableWork()` will execute, indicating that the cancellation was handled.

## ### What is an Actor?
An actor is a reference type that provides a safe, isolated environment for managing and modifying mutable state in a concurrent programming context. Actors are designed to help prevent data races, a common issue in concurrent programming where multiple threads or tasks access shared data simultaneously, leading to unpredictable behavior.

### Key features of actors
- **Data isolation**: Actors guarantee that only one task can access their mutable state at a time. This ensures that any modifications to the actor's properties or methods happen in a thread-safe manner.

- **Reference type**: Similar to classes, actors are reference types, meaning they are allocated on the heap, and references to them are passed around rather than copies of their data.

- **Concurrency control**: By default, only one task at a time can interact with an actor's state. Other tasks trying to access the actor will be suspended until the current task finishes, thereby preventing race conditions.

- **Asynchronous access**: Interaction with actors is usually asynchronous, which means you often need to use `await` when calling an actor's method or accessing its properties.

## ### How to define an actor?
Actors are defined similarly to classes, using the `actor` keyword.

```swift
actor BankAccount {
    private var balance: Double = 0.0
    
    func deposit(amount: Double) {
        balance += amount
    }
    
    func withdraw(amount: Double) -> Bool {
        if balance >= amount {
            balance -= amount
            return true
        } else {
            return false
        }
    }
    
    func getBalance() -> Double {
        return balance
    }
}
```
In this example:
- **Actor definition**: `BankAccount` is defined as an actor.

- **Private state**: The `balance` property is private and mutable, but access to it is controlled by the actor's methods.

- **Concurrency-safe methods**: The `deposit`, `withdraw`, and `getBalance` methods are safe to call from multiple tasks because the actor ensures that only one task accesses its state at a time.

## ### How to use an actor?
When you interact with an actor, you typically do so asynchronously.

```swift
let account = BankAccount()

Task {
    await account.deposit(amount: 100.0)
    let success = await account.withdraw(amount: 50.0)
    let balance = await account.getBalance()
    
    print("Withdrawal successful: \(success)")
    print("Current balance: \(balance)")
}
```
In this example:
- **Asynchronous interaction**: The `deposit`, `withdraw`, and `getBalance` methods are called using `await` because they may involve suspending the current task while the actor handles another task.

- **Safety**: Even if multiple tasks try to interact with the `BankAccount` actor simultaneously, the actor's internal state (`balance`) is protected from race conditions.

## ### Reentrancy in actors
Actors in Swift are reentrant, meaning that while an actor is awaiting the completion of an asynchronous operation, it can process other incoming tasks. This reentrancy can help in certain situations but can also lead to subtle bugs if not carefully managed, especially when the actor's state depends on the order of operations.

## ### What are global actors?
In addition to individual actors, Swift also supports global actors that provide concurrency protection across a broader scope, such as for an entire module or application. Global actors are useful when you want to enforce that certain code always runs on a specific actor, for example, ensuring that UI updates always happen on the main thread.

```swift
@MainActor
class ViewModel {
    private var data: [String] = []
    
    func updateData(newData: [String]) {
        data = newData
    }
    
    func fetchData() -> [String] {
        return data
    }
}
```
In this example, the `ViewModel` class is annotated with `@MainActor`, ensuring that all its methods and properties are accessed on the main thread.

## ### How to define a global actor?
A global actor is a way to enforce that certain code runs on a specific thread or execution context across your entire app or module. You define a global actor using the `@globalActor` attribute and typically use it to ensure that certain operations (like UI updates) always happen on the correct thread, such as the main thread.
```swift
@globalActor
struct MyGlobalActor {
    static let shared = MyActor()
}

actor MyActor {
    // Actor's isolated state and methods go here
}
```
In this example:
- **`@globalActor`**: The `MyGlobalActor` struct is marked as a global actor.

- **`shared` instance**: The global actor requires a `shared` static instance, which is an actor itself (`MyActor` in this case).

## ### How to use a global actor?
After defining a global actor, you can use it to ensure certain classes, structs, functions, or properties always execute on the actor's context. This is done by annotating the code with the global actor.

```swift
@MyGlobalActor
class SomeClass {
    var data: String = ""
    
    func updateData(newData: String) {
        data = newData
    }
    
    func fetchData() -> String {
        return data
    }
}
```
The `SomeClass` class is annotated with `@MyGlobalActor`, meaning all of its properties and methods are automatically isolated by the global actor.

## ### Using global actor on functions or properties
You can also use a global actor on individual functions, methods, or properties instead of an entire class or struct.

```swift
@MyGlobalActor
func performCriticalTask() {
    // Critical task that must run on MyGlobalActor's context
}

class AnotherClass {
    @MyGlobalActor var importantData: String = ""
    
    @MyGlobalActor
    func updateImportantData(newData: String) {
        importantData = newData
    }
}
```
In this example:
- **Global actor on function**: `performCriticalTask` will always run on `MyGlobalActor's` context.

- **Global actor on property**: The `importantData` property in `AnotherClass` is isolated by `MyGlobalActor`.

- **Global actor on method**: The `updateImportantData` method is isolated by MyGlobalActor.

## ### What is sendable type?
A sendable type is a type that can be safely used across concurrency boundaries, such as between different threads or tasks. This concept is crucial in Swift's concurrency model, where ensuring that data is safely shared or passed between concurrently executing code is vital to avoid data races and undefined behavior.

### What makes a type `Sendable`?
A type is considered `Sendable` if it can be passed or accessed from one concurrent context to another without causing thread safety issues. This generally means that the type is immutable or safely synchronized.

## ### How to define a Sendable type?
Swift provides a protocol called `Sendable` that types can conform to, either explicitly or implicitly. Many basic types like `Int`, `String`, and `Array` (when their elements are `Sendable`) automatically conform to Sendable.

```swift
struct Point: Sendable {
    let x: Int
    let y: Int
}
```
In this example, `Point` is a simple struct that is immutable (because all its properties are constants). Therefore, it safely conforms to `Sendable`.

## ### What is implicit conformance to `Sendable`?
Some types automatically conform to `Sendable` without requiring explicit declaration. This includes:

- Value types like `struct` and `enum` with all `Sendable` properties.

- Immutable reference types (`class`) where all stored properties are `Sendable`.

- Types like `Int`, `Double`, `String`, etc., which are inherently thread-safe.

```swift
struct User {
    let name: String
    let age: Int
}

let user = User(name: "Alice", age: 30)
```
Here, `User` implicitly conforms to `Sendable` because `String` and `Int` are `Sendable`, and `User` is immutable.

## ### Whar are non-sendable types?
Types that are not safe to share between concurrent contexts do not conform to `Sendable`. This typically includes mutable reference types (e.g., `class`) with non-thread-safe properties.

```swift
class Counter {
    var value: Int = 0
    
    func increment() {
        value += 1
    }
}
```
In this example, `Counter` is a non-Sendable type because its `value` property can be modified from multiple threads or tasks concurrently, leading to potential data races.

## ### What is `@unchecked` used for?
The `@unchecked` keyword is used in combination with the `Sendable` protocol to explicitly mark a type as conforming to `Sendable`, even if the compiler cannot guarantee that the type is actually safe to use across concurrency boundaries. Essentially, it tells the compiler to trust you that the type is safe to be sent between tasks or threads, bypassing the usual safety checks.
```swift
final class Logger: @unchecked Sendable {
    private var logs: [String] = []
    
    func log(message: String) {
        logs.append(message)
    }
    
    func allLogs() -> [String] {
        return logs
    }
}
```
In this example:
- **Logger class**: `Logger` has a mutable array `logs`, which is not inherently thread-safe. If accessed from multiple threads simultaneously, it could lead to race conditions.

- **`@unchecked Sendable`**: The `Logger` class is marked as `@unchecked Sendable`, meaning that the compiler will allow instances of `Logger` to be used across concurrency boundaries (e.g., passed between different tasks), even though it's not strictly safe without additional synchronization.

## ### What is macro?
A macro is a compile-time feature that allows you to generate code or perform transformations on code before it is compiled. Macros can be used to reduce boilerplate, enforce patterns, or generate repetitive code, which can enhance productivity and reduce errors in codebases.

### Key concepts of macros in Swift
- **Compile-time code generation**: Macros operate at compile-time, meaning they transform or generate code during the compilation process, rather than at runtime.

- **Syntax transformations**: Macros can modify or extend Swift's syntax, enabling new patterns or reducing the need for repetitive code constructs.

- **Parameterized and non-parameterized**: Macros can be parameterized, allowing developers to pass arguments to them, or non-parameterized, applying to specific parts of code without additional input.

- **Reducing boilerplate**: One of the main use cases for macros is to reduce repetitive patterns or boilerplate code, making the code more concise and maintainable.

## ### What are `Any` and `AnyObject`?
`Any` and `AnyObject` are special types that provide a way to work with values that are not known at compile-time. They are useful in scenarios where you need to handle a variety of types in a flexible and dynamic way.

## ### What is `Any` used for?
- `Any` can represent an instance of any type, including function types, optional types, and even `AnyObject`.

- It can hold both value types (e.g., `Int`, `String`, `Structs`, `Enums`) and reference types (`Classes`).

- `Any` is the most generic type in Swift and is often used when you need to work with heterogeneous collections or when you don't know the specific type of a value at compile time.

```swift
var anything: Any

anything = 5        // Int
anything = "Hello"  // String
anything = [1, 2, 3] // Array
```
In this example, anything can be assigned a value of any type.

## ### What is `AnyObject` used for?
- `AnyObject` represents an instance of any class type. It is restricted to reference types (`class` instances) and cannot hold value types like `struct` or `enum`.

- `AnyObject` is often used when you need to interact with Objective-C APIs, where the type system is less strict and class types are often treated generically.

```swift
class Dog {
    var name: String
    
    init(name: String) {
        self.name = name
    }
}

class Cat {
    var age: Int
    
    init(age: Int) {
        self.age = age
    }
}

var anyObject: AnyObject

anyObject = Dog(name: "Buddy")
anyObject = Cat(age: 5)
```
In this example, `anyObject` can hold instances of any class, such as `Dog` or `Cat`.

## ### Differences between `Any` and `AnyObject`
### Type scope:
- `Any` can represent both value types and reference types.

- `AnyObject` is limited to reference types (`class` instances).

### Use cases
- Use `Any` when you need to handle any kind of type, including both value and reference types.

- Use `AnyObject` when you need to work specifically with class instances or interact with Objective-C APIs.

## ### Type casting with `Any` and `AnyObject`
When working with `Any` or `AnyObject`, you often need to cast the value back to its original type using type casting operators (`as?`, `as!` or `is`).

```swift
let items: [Any] = [5, "Hello", Dog(name: "Buddy")]

for item in items {
    if let number = item as? Int {
        print("Integer: \(number)")
    } else if let text = item as? String {
        print("String: \(text)")
    } else if let dog = item as? Dog {
        print("Dog name: \(dog.name)")
    }
}
```
In this example, the `items` array contains elements of different types, and type casting is used to determine the type of each element at runtime.

## ### What are nested types?
Nested types refer to the practice of defining types within the context of other types, such as classes, structures, enumerations, and even within other nested types. This allows you to group related types together in a logical and hierarchical manner, improving code organization and encapsulation.

### Why use nested types?
- **Encapsulation**: Nesting types within other types helps encapsulate functionality that is specific to the enclosing type, preventing them from being used or accessed outside of their intended context.

- **Code organization**: It helps in organizing code better by grouping related types together, making the code easier to understand and maintain.

- **Avoiding name clashes**: Nesting types within another type prevents name clashes with other types defined elsewhere in your codebase.

## ### Example of nested structures
```swift
struct Car {
    struct Engine {
        var horsepower: Int
    }
    
    var model: String
    var engine: Engine
}

let myCar = Car(model: "Tesla Model S", engine: Car.Engine(horsepower: 670))

print("My car is a \(myCar.model) with \(myCar.engine.horsepower) horsepower.")
```
`Engine` is a structure nested inside the `Car` structure. This implies that `Engine` is closely related to `Car` and it should only be used within the context of a `Car`.

## ### Example of nested enumerations
```swift
struct Device {
    enum Status {
        case on, off, standby
    }
    
    var status: Status
}

let device = Device(status: .on)

print("The device is currently \(device.status).")
```
Here, `Status` is an enumeration nested inside the `Device` structure, indicating that the status is directly associated with the device.

## ### Example of nested classes
```swift
class University {
    class Department {
        var name: String
        
        init(name: String) {
            self.name = name
        }
    }
    
    var department: Department
    
    init(department: Department) {
        self.department = department
    }
}

let compSci = University.Department(name: "Computer Science")

let university = University(department: compSci)

print("Department: \(university.department.name)")
```
`Department` is a class nested inside the `University` class, signifying that a department is an integral part of a university.

## ### What are extensions?
Extensions are a powerful feature that allows you to add new functionality to an existing class, structure, enumeration, or protocol without modifying the original source code. Extensions can be used to add methods, computed properties, initializers, subscripts, and even conform types to protocols. They are particularly useful for organizing code, enhancing readability, and adhering to the open/closed principle (i.e., classes should be open for extension but closed for modification).

### Key features of extensions
- **Add new functionality**: You can add methods, computed properties, and more to existing types, including types for which you do not have access to the source code (e.g., types from the standard library or frameworks).

- **Protocol conformance**: Extensions can be used to make an existing type conform to a protocol, allowing you to separate protocol conformance from the primary implementation of the type.

- **No stored properties**: Extensions cannot add stored properties to types. They can only add computed properties, methods, initializers, subscripts, and protocol conformances.

- **Modularity**: Extensions help in organizing code by allowing you to break up large types into smaller, focused extensions.

## ### Example of adding methods using extensions
```swift
extension String {
    func reversedString() -> String {
        return String(self.reversed())
    }
}

let greeting = "Hello"

print(greeting.reversedString())  // Output: "olleH"
```
In this example, the `reversedString()` method is added to the `String` type using an extension. Now, any `String` instance can use this method.

## ### Example of adding computed properties using extensions
```swift
extension Int {
    var squared: Int {
        return self * self
    }
}

let number = 4
print(number.squared)  // Output: 16
```
Here, a computed property `squared` is added to the `Int` type, allowing you to get the square of an integer easily.

## ### Example of protocol conformance using extensions
```swift
protocol Describable {
    func describe() -> String
}

extension Double: Describable {
    func describe() -> String {
        return "The value is \(self)"
    }
}

let pi: Double = 3.14159
print(pi.describe())  // Output: "The value is 3.14159"
```
In this example, an extension is used to make `Double` conform to the `Describable` protocol by implementing the `describe()` method.

## ### Example of adding initializers using extensions
```swift
struct Point {
    var x: Double
    var y: Double
}

extension Point {
    init(xy: Double) {
        self.init(x: xy, y: xy)
    }
}

let point = Point(xy: 3.0)
print(point)  // Output: Point(x: 3.0, y: 3.0)
```
Here, an additional initializer is added to the `Point` struct, allowing you to initialize a `Point` with the same value for both `x` and `y`.

## ### Example of extensions for protocols
Extensions can also be used to add default implementations to protocols, which is particularly useful in Swift's protocol-oriented programming paradigm.

```swift
protocol Identifiable {
    var id: String { get }
}

extension Identifiable {
    func identify() -> String {
        return "My ID is \(id)"
    }
}

struct User: Identifiable {
    var id: String
}

let user = User(id: "12345")
print(user.identify())  // Output: "My ID is 12345"
```
In this example, the `identify()` method is provided as a default implementation for any type that conforms to the `Identifiable` protocol.

## ### Example of delegation: protocol and implementation
Let’s consider an example where we have a TaskManager that delegates the task of reporting progress to another object.

### Step 1: Define a protocol
```swift
protocol TaskManagerDelegate: AnyObject {  // "AnyObject" indicates this protocol can only be adopted by class types
    func taskDidStart()
    func task(didUpdateProgress progress: Float)
    func taskDidFinish()
}
```
This protocol defines the methods that the delegate must implement.

### Step 2: Implement the delegate
```swift
class TaskHandler: TaskManagerDelegate {
    func taskDidStart() {
        print("Task started.")
    }
    
    func task(didUpdateProgress progress: Float) {
        print("Task progress: \(progress * 100)%")
    }
    
    func taskDidFinish() {
        print("Task finished.")
    }
}
```
The `TaskHandler` class conforms to the `TaskManagerDelegate` protocol and implements its methods.

## ### Example of delegation: delegating object
### Step 1: Create a delegating object
```swift
class TaskManager {
    weak var delegate: TaskManagerDelegate?  // Declare the delegate as weak to avoid retain cycles
    
    func startTask() {
        delegate?.taskDidStart()
        
        for i in 1...10 {
            // Simulate work being done
            sleep(1)
            let progress = Float(i) / 10.0
            delegate?.task(didUpdateProgress: progress)
        }
        
        delegate?.taskDidFinish()
    }
}
```
The `TaskManager` class has a `delegate` property of type `TaskManagerDelegate?`. It calls the delegate's methods at different stages of the task.

### Step 2: Assign the Delegate and Start the Task
```swift
let taskManager = TaskManager()
let taskHandler = TaskHandler()

taskManager.delegate = taskHandler  // Assign the delegate
taskManager.startTask()
```
When the `startTask` method is called on `taskManager`, it uses the `taskHandler` to report progress.

## ### Common uses of delegation in iOS
Delegation is heavily used in iOS development, especially in UIKit. Examples include:

- **UITableViewDelegate and UITableViewDataSource**: Used to manage the display and behavior of table views.

- **UITextFieldDelegate**: Used to manage text input behavior.

- **NSURLSessionDelegate**: Used to handle events related to network requests.

## ### What is conditional conformance to a protocol?
Conditional conformance allows a generic type to conform to a protocol only when certain conditions are met, such as when the generic type's parameters themselves conform to a specific protocol. This feature is particularly powerful for creating flexible and reusable code while maintaining type safety.

### Why use conditional conformance?
Conditional conformance is useful when you want to extend a generic type to conform to a protocol, but only under specific conditions. For instance, you might want an array to conform to a protocol only if its elements also conform to that protocol.

### How conditional conformance works
You can make a generic type conform to a protocol conditionally by adding constraints to the generic parameters in the conformance declaration.

## ### Example: Extending `Array` to conform to a protocol conditionally
Let's say we have a protocol called Summable that requires a method for summing elements.

```swift
protocol Summable {
    func sum() -> Self
}
```
We want to make `Array` conform to `Summable`, but only if the elements of the array themselves conform to `Summable`.

```swift
extension Array: Summable where Element: Summable {

    func sum() -> Element {
        return self.reduce(Element.sum()) { $0.sum() }
    }
}
```
In this example, the extension makes `Array` conform to `Summable`, but only when `Element` (the type of the elements in the array) also conforms to `Summable`.

## ### Example: Extending `Equatable` to a custom generic type
Suppose you have a generic type Box that wraps another type:
```swift
struct Box<T> {
    let value: T
}
```
You want `Box` to conform to `Equatable`, but only if the type `T` inside `Box` is `Equatable`.
```swift
extension Box: Equatable where T: Equatable {
    static func == (lhs: Box<T>, rhs: Box<T>) -> Bool {
        return lhs.value == rhs.value
    }
}
```
Here, `Box` will only conform to `Equatable` if the type `T` is `Equatable`. This ensures that `Box` can only be compared for equality when its wrapped type supports equality comparison.

## ### Example: Conditional conformance with `Codable`
Let's say you have a generic type `Container` that can hold any type:

```swift
struct Container<T> {
    var items: [T]
}
```
You want `Container` to conform to `Codable` only when the type `T` inside `Container` is also `Codable`.

```swift
extension Container: Codable where T: Codable {}
```
This makes `Container` conform to `Codable` only when `T` is `Codable`, allowing you to encode and decode `Container` instances when they contain codable items.

## ### How to limit protocol adoption to class types?
You can limit a protocol so that only class types (also known as reference types) can adopt it by using the AnyObject protocol as an inheritance requirement. By declaring your protocol to inherit from AnyObject, you restrict its adoption to classes only. This ensures that only class instances can conform to the protocol, and it cannot be adopted by structs or enums (which are value types).

Here’s how you can define a protocol that can only be adopted by class types:
```swift
protocol MyClassOnlyProtocol: AnyObject {
    func someMethod()
}
```
In this example:
- **`MyClassOnlyProtocol`**: This is the protocol that can only be adopted by classes.
- **`AnyObject`**: By inheriting from `AnyObject`, the protocol is limited to class types.

## ### Example usage how to limit protocol adoption to class types
### Step 1: Define the protocol
```swift
protocol MyClassOnlyProtocol: AnyObject {
    func someMethod()
}
```
This protocol now can only be adopted by classes.

### Step 2: Adopt the protocol in a class
```swift
class MyClass: MyClassOnlyProtocol {
    func someMethod() {
        print("Method implemented in MyClass")
    }
}
```
Here, `MyClass` adopts the `MyClassOnlyProtocol` and implements its required method.

## ### Why restrict protocol adoption to class types?
Restricting protocol adoption to class types might be necessary in scenarios where:

- **Reference semantics**: The protocol requires reference semantics, meaning you need the conforming type to behave as a reference rather than a value. For example, when you need to share the same instance across different parts of your code or maintain identity.

- **Avoiding copying**: Since value types like structs are copied when passed around, you may want to avoid this behavior, especially when dealing with large objects or when mutation is needed.

- **ARC (Automatic Reference Counting)**: You want the protocol to work with features that rely on ARC, such as weak references, which are not applicable to value types.

## ### What is protocol composition?
Protocol composition allows you to create a type that conforms to multiple protocols simultaneously. Instead of defining a new protocol that inherits from several others, you can compose protocols together on the fly using the protocol composition syntax. This is particularly useful when you want to specify that a type must conform to more than one protocol without creating a new protocol.

The syntax for protocol composition uses the `&` operator between the protocols:
```swift
protocol ProtocolA {
    func methodA()
}

protocol ProtocolB {
    func methodB()
}

typealias CombinedProtocol = ProtocolA & ProtocolB
```
In this example:
- **`CombinedProtocol`**: This is a type alias that represents any type that conforms to both `ProtocolA` and `ProtocolB`.

## ### What are advantages of protocol composition?
- **Flexibility**: Allows you to work with types that conform to multiple protocols without needing to define a new protocol that combines them.

- **Reusability**: You can easily reuse existing protocols in various combinations, promoting modular design.

- **Type safety**: Swift ensures at compile-time that the type conforms to all the required protocols, preventing runtime errors.

## ### Optional protocol requirements
Optional protocol requirements are a feature that allows certain methods or properties in a protocol to be optionally implemented by conforming types. This means that a type conforming to the protocol is not required to implement those specific methods or properties.

However, it's important to note that optional protocol requirements are only available when the protocol is marked with the `@objc` attribute, which restricts the protocol to being compatible with Objective-C. As a result, this feature is typically used when working with Cocoa or Cocoa Touch frameworks, where interoperability with Objective-C is needed.

To declare optional protocol requirements, the protocol must be marked with `@objc`, and the optional requirements are declared using the `@objc optional` keyword:

```swift
@objc protocol MyProtocol {
    func requiredMethod()
    @objc optional func optionalMethod()
}
```
In this example:
- **`requiredMethod()`**: This method is required and must be implemented by any type conforming to `MyProtocol`.

- **`optionalMethod()`**: This method is optional, meaning a conforming type may implement it, but it's not required.

## ### What are generics?
Generics allow you to write flexible and reusable code by defining functions, types, and methods that can work with any type, rather than requiring a specific one. Generics enable you to write code that can handle different data types in a type-safe way, making your code more abstract, general, and reusable.

### Why use generics?
- **Code reusability**: Instead of writing the same function or type for different data types, you can write it once and use it with any type.

- **Type safety**: Generics enable you to write functions or types that work with multiple types while preserving type safety, reducing the risk of runtime errors.

- **Flexibility**: You can build more abstract and versatile algorithms that work across different types.

## ### Basic example of generics (functions)
Let’s start with a simple example: a function that swaps two values.

### Without generics
```swift
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
    let temp = a
    a = b
    b = temp
}
```
This function works fine for `Int`, but what if you wanted to swap two `String` values? You'd have to write another function:

```swift
func swapTwoStrings(_ a: inout String, _ b: inout String) {
    let temp = a
    a = b
    b = temp
}
```
This results in repetitive code.

### With generics
Using generics, you can write a single `swap` function that works with any type:

```swift
func swapTwoValues<T>(_ a: inout T, _ b: inout T) {
    let temp = a
    a = b
    b = temp
}
```
- **`<T>`**: This defines a generic type parameter `T`. It acts as a placeholder for any type.

- **`_ a: inout T, _ b: inout T`**: The function can now accept two parameters of any type T, as long as both are of the same type.

You can use `swapTwoValues` with `Int`, `String`, or any other type:
```swift
var a = 5
var b = 10
swapTwoValues(&a, &b)  // a is now 10, b is 5

var x = "Hello"
var y = "World"
swapTwoValues(&x, &y)  // x is now "World", y is "Hello"
```

## ### Generic types
You can also create generic types, such as generic classes, structs, or enums. A common example is a stack data structure.

```swift
struct Stack<Element> {
    private var items: [Element] = []
    
    mutating func push(_ item: Element) {
        items.append(item)
    }
    
    mutating func pop() -> Element? {
        return items.popLast()
    }
}
```
- **`<Element>`**: This defines a generic type parameter `Element` for the `Stack` type.
- **`items: [Element]`**: The stack uses an array to store elements, and these elements can be of any type.

You can create a stack for integers, strings, or any other type:
```swift
var intStack = Stack<Int>()
intStack.push(1)
intStack.push(2)

print(intStack.pop())  // Output: Optional(2)

var stringStack = Stack<String>()
stringStack.push("Hello")
stringStack.push("World")

print(stringStack.pop())  // Output: Optional("World")
```

## ### Generic constraints
Sometimes, you might want to restrict the types that can be used with your generic code. This is where generic constraints come in. You can specify that a type parameter must conform to a certain protocol or be a subclass of a specific class.

```swift
func findIndex<T: Equatable>(of valueToFind: T, in array: [T]) -> Int? {
    for (index, value) in array.enumerated() {
        if value == valueToFind {
            return index
        }
    }
    return nil
}
```
- **`<T: Equatable>`**: The generic type `T` is constrained to types that conform to the `Equatable` protocol.
- This function now works only with types that can be compared for equality.
```swift
let numbers = [1, 2, 3, 4, 5]

if let index = findIndex(of: 3, in: numbers) {
    print("Index: \(index)")  // Output: Index: 2
}

let words = ["apple", "banana", "cherry"]

if let index = findIndex(of: "banana", in: words) {
    print("Index: \(index)")  // Output: Index: 1
}
```

## ### What are associated types?
An associated type is a placeholder name for a type that is used within a protocol. It is specified with the `associatedtype` keyword inside the protocol. When a type conforms to the protocol, it specifies what the associated type should be. This allows the protocol to be more generic and work with different types without being tied to a specific one.

Here's how you declare an associated type in a protocol:
```swift
protocol Container {
    associatedtype Item
    
    var count: Int { get }
    subscript(index: Int) -> Item { get }
    
    func append(_ item: Item)
}
```
In this example:
- **`associatedtype Item`**: Declares an associated type named Item. The actual type of Item will be determined by the conforming type.

- The `Container` protocol defines methods and properties that use the Item type.

## ### Example of associated types
Let's implement the Container protocol in a Stack type.
```swift
struct Stack<Element>: Container {
    // The type of 'Item' is inferred to be 'Element'
    var items: [Element] = []
    
    var count: Int {
        return items.count
    }
    
    subscript(index: Int) -> Element {
        return items[index]
    }
    
    mutating func append(_ item: Element) {
        items.append(item)
    }
    
    mutating func pop() -> Element? {
        return items.popLast()
    }
}
```
In this implementation:
- `Element`: The `Stack` structure uses a generic parameter `Element`, which becomes the associated type `Item` when the `Stack` conforms to `Container`.

- The `Item` type is inferred to be the same as `Element`, so there's no need to explicitly declare the `Item` type.

## ### Constraints on associated types
Just like generic type parameters, you can apply constraints to associated types to restrict what types can be used.

### Example with constraints
```swift
protocol Container {
    associatedtype Item: Equatable
    
    var count: Int { get }
    subscript(index: Int) -> Item { get }
    
    func append(_ item: Item)
}
```
In this example:
- `Item: Equatable`: The associated type `Item` is constrained to types that conform to the `Equatable` protocol. This means any type that conforms to `Container` must specify an Item type that can be compared for equality.

## ### Extensions with a generic `where` clause
When you combine extensions with a generic where clause, you can make your extensions apply only to types that meet specific criteria. This allows you to add functionality in a more controlled and precise manner.

### What is a generic `where` clause?
A generic where clause is a way to specify conditions that types must meet for a generic type, function, or extension to be valid. You use a `where` clause to define these conditions.

```swift
extension SomeType where Condition {
    // New functionality for SomeType that meets the Condition
}
```

## ### Example: Extension with a generic `where` clause on a type
Let's say you have a generic type `Stack`, and you want to add a method that’s only available when the elements in the stack are `Equatable`:

```swift
struct Stack<Element> {
    private var items: [Element] = []
    
    mutating func push(_ item: Element) {
        items.append(item)
    }
    
    mutating func pop() -> Element? {
        return items.popLast()
    }
}

extension Stack where Element: Equatable {
    func isTop(_ item: Element) -> Bool {
        guard let topItem = items.last else {
            return false
        }
        return topItem == item
    }
}
```
Explanation:
- `where Element: Equatable`: This condition means the extension is only applicable when `Element`, the type stored in the `Stack`, conforms to the `Equatable` protocol.

- `isTop(_ item: Element) -> Bool`: This method checks if a given item is the top item in the stack. It can only be implemented for `Equatable` types, as it uses the `==` operator.

If you tried to call `isTop(_:)` on a `Stack` that holds a non-`Equatable` type, you’d get a compile-time error.

## ### Example: Extension with a generic `where` clause on a protocol
You can also use a generic where clause to extend a protocol in a way that only applies to certain types that conform to the protocol.
```swift
protocol Container {
    associatedtype Item
    
    var count: Int { get }
    subscript(index: Int) -> Item { get }
}

extension Container where Item: Equatable {
    func allItemsEqual() -> Bool {
        for i in 1..<count {
            if self[i] != self[0] {
                return false
            }
        }
        return true
    }
}
```
Explanation:
- **`Container where Item: Equatable`**: This extension is only available to types that conform to `Container` and have an `Item` type that is `Equatable`.

- **`allItemsEqual`**: This method checks if all items in the container are equal.

## ### What are opaque types?
Opaque types provide a way to return a type from a function or method without exposing the specific underlying type to the caller. This is done using the `some` keyword. Opaque types offer a balance between abstraction and type safety, allowing you to hide implementation details while still ensuring that the returned value conforms to a particular protocol.

### Key concepts
- **Type abstraction**: Opaque types allow you to hide the concrete type that a function or method returns. The caller only knows that the returned value conforms to a specific protocol or set of requirements, not what the actual type is.

- **Type safety**: Even though the specific type is hidden, the compiler knows what the type is and enforces type safety. This means that you can't accidentally mix up types or misuse the returned value.

## ### Opaque type vs. protocol type
- **Opaque type**: The concrete type is known at compile time, but hidden from the caller. The caller only knows that the return type conforms to a certain protocol. The concrete type remains consistent for a particular function.

- **Protocol type (`any`)**: The concrete type can vary, and the caller can interact with it using only the methods and properties defined by the protocol. However, protocol types can incur runtime costs due to dynamic dispatch and type erasure.

## ### Example: Returning an opaque type
Suppose you have two different types that conform to a protocol `Shape`:

```swift
protocol Shape {
    func area() -> Double
}

struct Circle: Shape {
    var radius: Double
    
    func area() -> Double {
        return .pi * radius * radius
    }
}

struct Square: Shape {
    var side: Double
    
    func area() -> Double {
        return side * side
    }
}
```
You could write a function that returns either a `Circle` or a `Square`, but you want to hide the specific type from the caller:

```swift
func makeShape() -> some Shape {
    return Circle(radius: 5)
}
```
In this function:
- **`some Shape`**: The return type is an opaque type, indicating that the function returns some type that conforms to the `Shape` protocol, but the exact type is hidden.

The caller of `makeShape` doesn’t need to know that it’s a `Circle`. They only know that they’re getting something that conforms to `Shape`:

```swift
let shape = makeShape()
print(shape.area())  // Works because `Shape` protocol guarantees `area` method
```

## ### Example: Using opaque types with different types
One important thing to note is that the opaque type must be consistent. If you tried to return different types based on a condition, you would get a compile-time error:

```swift
func makeShape(condition: Bool) -> some Shape {
    if condition {
        return Circle(radius: 5)
    } else {
        return Square(side: 10)  // Error: Return types must be the same
    }
}
```
Opaque types require that the returned value is of the same concrete type, regardless of how the function executes.

## ### Benefits of opaque types
- **Encapsulation**: You can hide the details of your implementation while providing a clean, abstract interface.

- **Performance**: Since the concrete type is known at compile time, the Swift compiler can optimize the code better than with protocol types (`any`).

- **Type safety**: The compiler ensures that the returned value always conforms to the expected protocol, even though the specific type is hidden.

## ### Opaque types use cases
Opaque types are particularly useful in cases like:

- **Returning types that conform to a protocol**: When you want to hide the exact type but ensure it conforms to a specific protocol.

- **Abstracting complexity**: When you want to provide a simple interface to complex logic, where the specific types are not important to the user.

- **Maintaining flexibility**: When you may want to change the underlying type without affecting the API or the code that uses it.

## ### Comparison to boxed/existential types (`any`)
### Opaque types (`some`):

- The type is determined at compile time and remains consistent.
- Better performance due to lack of type erasure.
- Stronger type safety guarantees.

### Boxed protocol / existential types (`any`):

- The type can vary at runtime.
- Supports dynamic dispatch.
- Can handle multiple types at the cost of some performance overhead.

## ### What is boxed protocol type?
A boxed protocol type refers to a concept where a value of a type that conforms to a protocol is stored in a way that abstracts (or "boxes") the underlying concrete type, allowing for a more flexible, albeit less type-safe, handling of multiple types. This is typically done using existential types (also referred to as protocol types) in Swift, and is common when using a protocol as a type itself.

## ### Key characteristics of boxed protocol types
- **Type erasure**: When you use a protocol as a type, the specific details of the underlying type are erased, or "boxed". The only thing the compiler knows is that the value conforms to the protocol. This is known as type erasure.

- **Dynamic dispatch**: Methods on a boxed protocol type are called via dynamic dispatch, which means the actual method to call is determined at runtime. This adds some runtime overhead compared to calling methods on a concrete type directly.

- **Limited type information**: Since the underlying type is erased, you lose some of the type information, which can make certain operations (like comparing two values) more difficult or impossible without additional type information or casting.

- **Flexibility**: Boxed protocol types allow you to write more flexible and generic code, as you can handle multiple types uniformly as long as they conform to the protocol.

## ### What is type erasure?
Type erasure is a technique that allows you to work with values of different concrete types in a generic way while hiding (or "erasing") the specific underlying type information. This enables you to use protocols with associated types or generic types as concrete types, providing flexibility while maintaining a uniform interface.

### Why use type erasure?
Protocols with associated types or self-requirements (e.g., `Self` or associated types) cannot be used directly as types. This limitation can make it challenging to create collections or APIs that can handle multiple types conforming to such protocols in a type-safe manner. Type erasure solves this problem by wrapping the conforming types in a type-erased container that hides the specific type, allowing you to use the protocol as a type.

## ### Example: Type erasure with a protocol
Consider a protocol with an associated type:
```swift
protocol Shape {
    func area() -> Double
}

struct Circle: Shape {
    var radius: Double
    func area() -> Double {
        return .pi * radius * radius
    }
}

struct Square: Shape {
    var side: Double
    func area() -> Double {
        return side * side
    }
}
```
You want to create a collection of different `Shape` types and work with them uniformly. However, because `Shape` uses `Self` in its methods, you can't create an array of `Shape`:

```swift
// This won't work
let shapes: [Shape] = [Circle(radius: 5), Square(side: 10)]
```

### Implementing Type Erasure
You can implement type erasure by creating a wrapper that conforms to the `Shape` protocol, but erases the underlying type:

```swift
struct AnyShape: Shape {
    private let _area: () -> Double

    init<S: Shape>(_ shape: S) {
        _area = shape.area
    }

    func area() -> Double {
        return _area()
    }
}
```
Here’s how it works:
- **`AnyShape`**: This struct is the type-erased wrapper. It conforms to the `Shape` protocol.

- **`_area`**: This is a stored closure that captures the area function of the wrapped concrete type.

- **`init<S: Shape>`**: The initializer takes any type conforming to `Shape`, and stores its `area` function in the `_area` closure.

Now, you can create a collection of `Shape` objects:
```swift
let shapes: [AnyShape] = [AnyShape(Circle(radius: 5)), AnyShape(Square(side: 10))]

for shape in shapes {
    print(shape.area())
}
```

## ### Benefits of type erasure
- **Flexibility**: Type erasure allows you to work with heterogeneous collections of types that conform to a protocol with associated types or self-requirements.

- **Abstraction**: The concrete type is hidden, providing an abstract and uniform interface for interacting with different types.

- **Simplification**: Type erasure can simplify APIs by allowing you to define functions and methods that accept or return types conforming to protocols with associated types, without exposing the underlying implementation details.

## ### Drawbacks of type erasure
- **Complexity**: Implementing type erasure requires additional boilerplate code, such as wrapper types, which can make the code harder to understand and maintain.

- **Performance overhead**: There may be some performance overhead due to the use of closures and indirection, as well as the loss of some compile-time optimizations.

- **Loss of type information**: With type erasure, the specific type information is hidden, which can limit the operations you can perform on the type-erased value.

## ### Type erasure summary
- **Type erasure**: A technique that hides the concrete type of a value conforming to a protocol with associated types or self-requirements, allowing the protocol to be used as a type.

- **Implementation**: Usually involves creating a wrapper type that conforms to the protocol and delegates the protocol's requirements to the wrapped value.

- **Use cases**: Heterogeneous collections, abstracting APIs, and working with protocols that have associated types.

Type erasure is a powerful tool for creating flexible, abstract APIs while maintaining type safety and a uniform interface, though it comes with trade-offs in complexity and performance.

## ### What's the difference between `self` and `Self`?
### `self`

- Refers to the current instance of a type (class, struct, or enum).

- Used to access instance properties, methods, or to disambiguate from local variables.

### `Self`

- Refers to the type itself, especially in the context of protocols and static/class methods.

- Used in protocols to refer to the type that conforms to the protocol, ensuring that certain methods return the same type as the conforming type.

Understanding the distinction between `self` and `Self` is crucial for writing correct and clear Swift code, particularly when dealing with protocols, initializers, and type-level methods.

## ### The access levels
Swift has five access levels and visibility scope:
- **`open`**:  Anywhere in the module and any module that imports it. Inheritance outside module: Yes

- **`public`**: Anywhere in the module and any module that imports it

- **`internal`**: Anywhere in the same module

- **`fileprivate`**: Only within the same source file

- **`private`**: Only within the same declaration (class, struct, etc.)

## ### The access levels best practices
- **Use `internal` (the default) unless you need something to be more or less visible**. This keeps your codebase clean and prevents accidental misuse.

- **Use `private` and `fileprivate` to encapsulate implementation details** that shouldn’t be accessible outside the immediate context, maintaining a clean API surface.

- **Use `public` and `open` carefully in libraries and frameworks**, as they define the public interface and extensibility points for your code, which will be used by other developers.

Understanding and using these access levels effectively helps ensure your Swift code is well-organized, maintainable, and secure.

## ### Bitwise operators
Bitwise operators allow you to manipulate individual bits of data types such as integers. They perform operations directly on the binary representation of numbers. These operators are often used in low-level programming, cryptography, graphics programming, and situations where performance is critical.

Swift provides several bitwise operators:
- **Bitwise NOT `~`** Used to invert all bits.

- **Bitwise AND `&`** Commonly used in masking operations to select specific bits.

- **Bitwise OR `|`** Used to set specific bits.

- **Bitwise XOR `^`** Used to toggle specific bits.

- **Bitwise Left Shift `<<`** Used in performance-critical code for multiplication, division by powers of two, or bit manipulation.

- **Bitwise Right Shift `>>`**

Understanding bitwise operators is crucial for tasks that require direct manipulation of binary data, offering powerful tools for low-level operations in Swift.

## ### Operator methods
Operators such as `+`, `-`, `*` and `==` can be overloaded or custom operators can be created to work with custom types. These are known as operator methods. Operator methods are special methods that allow you to define the behavior of an operator when used with instances of your custom types.

### Defining operator methods
To define an operator method, you need to use the `static func` keyword inside your custom type (class, struct, or enum) and associate it with the operator symbol. Swift allows overloading both existing operators and defining custom operators.

## ### Examples of operator methods: Addition operator `+`
Let's say you have a `Vector2D` struct that represents a 2D vector, and you want to add two vectors together using the `+` operator.

```swift
struct Vector2D {
    var x: Double
    var y: Double
    
    // Overloading the + operator for Vector2D
    static func +(lhs: Vector2D, rhs: Vector2D) -> Vector2D {
        return Vector2D(x: lhs.x + rhs.x, y: lhs.y + rhs.y)
    }
}

let vector1 = Vector2D(x: 3.0, y: 4.0)
let vector2 = Vector2D(x: 2.0, y: 3.0)
let result = vector1 + vector2  // Vector2D(x: 5.0, y: 7.0)
```
Explanation: The `+` operator is overloaded to add the `x` and `y` components of two `Vector2D` instances. The result is a new `Vector2D` instance.

## ### Examples of operator methods: Equality operator `==`
You can also overload the equality operator `==` to compare two instances of a custom type.

```swift
struct Vector2D: Equatable {
    var x: Double
    var y: Double
    
    // Overloading the == operator for Vector2D
    static func ==(lhs: Vector2D, rhs: Vector2D) -> Bool {
        return lhs.x == rhs.x && lhs.y == rhs.y
    }
}

let vector1 = Vector2D(x: 3.0, y: 4.0)
let vector2 = Vector2D(x: 3.0, y: 4.0)
let vector3 = Vector2D(x: 2.0, y: 3.0)

print(vector1 == vector2)  // true
print(vector1 == vector3)  // false
```
Explanation: The `==` operator is overloaded to compare the x and y components of two `Vector2D` instances for equality.

## ### Examples of operator methods: Custom prefix operator `-`
You can define custom behavior for prefix operators like the unary minus (-) for a type.

```swift
prefix operator -  // Define a prefix operator

struct Vector2D {
    var x: Double
    var y: Double
    
    // Overloading the unary - operator for Vector2D
    static prefix func -(vector: Vector2D) -> Vector2D {
        return Vector2D(x: -vector.x, y: -vector.y)
    }
}

let vector = Vector2D(x: 3.0, y: 4.0)
let negatedVector = -vector  // Vector2D(x: -3.0, y: -4.0)
```
Explanation: The `-` operator is overloaded as a prefix operator to negate the `x` and `y` components of a `Vector2D` instance.

## ### Custom operators
You can also define entirely new operators and then provide implementations for them. For example, you could define a `**` operator to perform exponentiation:

```swift
infix operator ** : MultiplicationPrecedence  // Define a custom infix operator

func **(base: Double, exponent: Double) -> Double {
    return pow(base, exponent)
}

let result = 2.0 ** 3.0  // 8.0
```
Explanation: The `**` operator is defined and implemented to perform exponentiation using the `pow` function from the standard library.

## ### What is `@resultBuilder`?
`@resultBuilder` is a powerful feature that allows you to define a custom syntax for building complex data structures, typically by composing smaller pieces of data in a declarative way. It's used to create domain-specific languages (DSLs) that enable a more expressive and natural way of defining complex operations, such as UI layouts, HTML markup, or data pipelines.

### Key concepts of `@resultBuilder`
- **Result builder**: A result builder is a type that provides a set of methods used to transform a sequence of statements into a single result.

- **Declarative syntax**: It allows you to write code in a declarative style, where the focus is on what you want to achieve rather than how to achieve it.

- **Transform statements**: The result builder transforms a series of statements into a single value, often by combining them into a collection or other structure.

## ### Example: SwiftUI's `@ViewBuilder`
SwiftUI uses a result builder called @ViewBuilder to allow developers to write views in a natural, declarative style.

```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            Text("Hello, World!")
            Text("This is a declarative UI")
        }
    }
}
```
Here, VStack is using `@ViewBuilder` to combine the `Text` views into a single `View` structure.

## ### Creating your own `@resultBuilder`
You can create a custom result builder by defining a struct or class and annotating it with `@resultBuilder`. The result builder type needs to implement several static methods that describe how to handle different parts of the builder syntax, such as combining multiple values, handling optional values, or building blocks conditionally.

Let's create a simple result builder to construct arrays of integers.
```swift
@resultBuilder
struct IntArrayBuilder {
    static func buildBlock(_ components: Int...) -> [Int] {
        return components
    }

    static func buildOptional(_ component: [Int]?) -> [Int] {
        return component ?? []
    }

    static func buildEither(first component: [Int]) -> [Int] {
        return component
    }

    static func buildEither(second component: [Int]) -> [Int] {
        return component
    }

    static func buildArray(_ components: [[Int]]) -> [Int] {
        return components.flatMap { $0 }
    }
}

func buildIntArray(@IntArrayBuilder _ content: () -> [Int]) -> [Int] {
    return content()
}

// Usage example
let numbers = buildIntArray {
    1
    2
    3
    if true {
        4
        5
    } else {
        6
    }
}
print(numbers)  // Output: [1, 2, 3, 4, 5]
```
Explanation:
- **`buildBlock(_:)`**: Combines multiple elements into a single result, in this case, an array of integers.

- **`buildOptional(_:)`**: Handles optional values.

- **`buildEither(first:)` and `buildEither(second:)`**: Handle conditional statements (`if-else`) within the result builder.

- **`buildArray(_:)`**: Handles loops like `for` or `map` inside the result builder.

## ### What is Combine framework?
The Combine framework is a powerful reactive programming framework introduced by Apple in iOS 13, macOS 10.15, watchOS 6, and tvOS 13. It allows developers to work with asynchronous events by providing a declarative Swift API for handling asynchronous sequences of values over time.

### Key concepts of combine
- **Publisher**: A publisher is a source of values that can emit a sequence of values over time, which can either succeed or fail with an error. Publishers can emit zero or more values and then complete, or they can fail with an error.

- **Subscriber**: A subscriber listens to values emitted by a publisher. When a subscriber is attached to a publisher, it can receive values, completion events, or error events.

- **Operators**: Operators are methods that transform, combine, filter, or otherwise manipulate the values emitted by a publisher before they are received by a subscriber. Combine provides a rich set of operators like `map`, `filter`, `combineLatest` and `flatMap` for transforming data streams.

- **Subscription**: A subscription represents the connection between a publisher and a subscriber. It controls the flow of data and allows the subscriber to cancel the subscription if it no longer needs the data.

- **Subject**: A subject is a type of publisher that can both publish values and be subscribed to. Subjects are typically used to bridge imperative code (like user input) with reactive Combine code.

## ### How Combine works?
In Combine, you create a data pipeline where:

- **Publishers** emit values or events over time.
- **Operators** process or modify these values.
- **Subscribers** consume the values or handle completion or error events.

Here's a basic flow:

**Publisher** → **Operator** → **Subscriber**

## ### Combine: example usage
Below is a simple example of how Combine can be used to filter and transform values emitted by a publisher:

```swift
import Combine

// A simple publisher that emits numbers 1 to 5
let publisher = [1, 2, 3, 4, 5].publisher

// A subscriber that listens to the publisher
let subscription = publisher
    .filter { $0 % 2 == 0 } // Filter even numbers
    .map { $0 * 10 }        // Multiply by 10
    .sink(
        receiveCompletion: { completion in
            switch completion {
            case .finished:
                print("Finished")
            case .failure(let error):
                print("Failed with error: \(error)")
            }
        },
        receiveValue: { value in
            print("Received value: \(value)")
        }
    )

// Output:
// Received value: 20
// Received value: 40
// Finished
```

## ### Combine building blocks
1. **Publishers**:
- Examples: **`Just`**, **`Future`**, **`PassthroughSubject`**, **`CurrentValueSubject`**, **`URLSession.DataTaskPublisher`**.
- Emit sequences of values or events over time.

2. **Subscribers**:
- Examples: **`sink`**, **`assign`**.
- Attach to publishers to receive and handle values or completion events.

3. **Operators**:
- Examples: **`map`**, **`filter`**, **`reduce`**, **`debounce`**, **`merge`**, **`combineLatest`**.
- Transform or combine data from publishers before it reaches subscribers.

4. **Subjects**:
- **`PassthroughSubject`**: Emits values to subscribers.
- **`CurrentValueSubject`**: Like **`PassthroughSubject`**, but also retains the current value, so new subscribers immediately receive the latest value.

5. **Schedulers**:
- Define where and when work occurs, such as on the main thread, a background thread, or after a delay.

## ### Combine real-world use cases
- **Network requests**: Chain and process responses from API calls.

- **User input handling**: Debounce and throttle text input in search fields.

- **Data binding**: Bind data between your model and UI in a reactive way, similar to how SwiftUI works.

- **Event streams**: React to system notifications, delegate calls, or other event-driven programming tasks.

## ### Combine advantages
- **Declarative**: Code becomes more declarative and easier to reason about.

- **Type-safe**: Strongly typed, which catches errors at compile time.

- **Integration**: Designed to work seamlessly with Swift, SwiftUI, and other Apple frameworks.

## ### `Just` publisher
A `Just` publisher in Combine is a simple type of publisher that emits a single value and then immediately finishes. It's useful when you want to work with a known, single value in a Combine pipeline, or when you want to wrap a constant value in a publisher to integrate with other Combine-based code.

### Key characteristics of `Just`
- **Single output**: It emits exactly one value and then completes.

- **Immediate completion**: After emitting the value, it immediately finishes and sends a .finished completion event to its subscribers.

- **No failure**: The `Just` publisher cannot fail. It uses `Never` as its failure type, indicating that it never emits an error.

## ### `Just` publisher usage and example
`Just` is commonly used in scenarios where you need a simple publisher that wraps a constant value, or in testing where you want to provide a known value in a Combine chain.

Here's an example of using `Just` in a Combine pipeline:
```swift
import Combine

// Create a Just publisher that emits the value "Hello, Combine!"
let justPublisher = Just("Hello, Combine!")

// Subscribe to the publisher
let subscription = justPublisher
    .sink(
        receiveCompletion: { completion in
            print("Completion: \(completion)")
        },
        receiveValue: { value in
            print("Value: \(value)")
        }
    )

// Output:
// Value: Hello, Combine!
// Completion: finished
```
Explanation
- **Creating a publisher: `Just("Hello, Combine!")`** creates a publisher that will emit the string "Hello, Combine!".

- **Subscribing**: The sink method subscribes to the Just publisher, providing closures to handle the received value and the completion event.

- **Output**: The value is printed, followed by a message indicating that the publisher has finished.

## ### When to use `Just`
- **Testing**: It's useful in unit tests where you want to simulate a publisher that emits a single value.

- **Default values**: When you need to provide a default value or wrap a known constant in a Combine chain.

- **Simple pipelines**: In simple Combine chains where you don't need more complex, dynamic publishers.

## ### `Future` publisher
The `Future` publisher in Combine is a powerful tool for handling asynchronous tasks that will eventually produce a result or fail with an error. Unlike `Just`, which emits a single known value immediately, `Future` allows you to create a publisher that will emit a value or an error sometime in the future.

### Key characteristics of `Future`
- **Asynchronous**: `Future` is designed for tasks that will complete at a later time, such as network requests, file operations, or any other asynchronous operations.

- **Single output**: Like `Just`, `Future` emits exactly one value or an error and then completes.

- **Promise-based**: When you create a `Future`, you receive a `Promise` object that you use to either fulfill with a value or reject with an error.

## ### `Future` publisher usage and example
A `Future` is typically created with a closure that takes a `Promise` as an argument. The closure contains the asynchronous code, and once the operation is complete, you call the `Promise` with either a success or failure result.

Here’s an example of using Future to simulate a simple asynchronous operation that fetches data:

```swift
import Combine

// A function that returns a Future publisher
func fetchData() -> Future<String, Error> {
    return Future { promise in
        // Simulating an asynchronous operation with a delay
        DispatchQueue.global().asyncAfter(deadline: .now() + 2) {
            let success = true // Simulate success or failure
            
            if success {
                promise(.success("Data received successfully!"))
            } else {
                promise(.failure(NSError(domain: "Error", code: -1, userInfo: nil)))
            }
        }
    }
}

// Using the Future publisher
let futurePublisher = fetchData()

let subscription = futurePublisher
    .sink(
        receiveCompletion: { completion in
            switch completion {
            case .finished:
                print("Finished")
            case .failure(let error):
                print("Failed with error: \(error)")
            }
        },
        receiveValue: { value in
            print("Value: \(value)")
        }
    )

// Output after 2 seconds:
// Value: Data received successfully!
// Finished
```
Explanation
- **Creating a Future**: The `fetchData()` function returns a `Future` that simulates an asynchronous operation. Inside the closure, you perform your async task (here simulated with a delay), and then use the `promise` to return a result.

- **Promise**: The `Promise` is called with `.success` or `.failure` to indicate whether the operation succeeded or failed.

- **Subscribing**: The `sink` subscriber is used to handle the received value or error when the Future completes.

## ### When to use `Future`
- **Asynchronous operations**: Ideal for wrapping asynchronous operations such as network requests, database queries, or any task that takes time to complete.

- **Single result**: Use `Future` when you expect to receive only one value (or error) from the operation.

- **Integration with Combine**: `Future` is a great way to bridge asynchronous code with Combine's reactive programming model.

## ### `PassthroughSubject` publisher
A `PassthroughSubject` in Combine is a type of publisher that you can use to manually emit values or events to subscribers. Unlike other publishers that may have a predefined sequence of events (like `Just` or `Future`), `PassthroughSubject` allows you to dynamically send values at any time, making it ideal for handling user input, notifications, or other events that occur over time.

### Key characteristics of `PassthroughSubject`
- **Manual control**: You manually send values or completion events to subscribers using methods like `send(_:)`.

- **Multiple subscribers**: Multiple subscribers can attach to a `PassthroughSubject` and receive the same events.

- **No initial value**: Unlike `CurrentValueSubject`, `PassthroughSubject` does not have an initial value or store the last emitted value.

- **Completion and error handling**: You can signal completion or failure at any time using the `send(completion:)` method.

## ### `PassthroughSubject` publisher usage and example
`PassthroughSubject` is typically used when you want to broadcast events or values to one or more subscribers, and you want to control when those events occur.

Here’s an example of using `PassthroughSubject` to broadcast user input events:
```swift
import Combine

// Define a PassthroughSubject that emits String values and never fails
let subject = PassthroughSubject<String, Never>()

// Create a subscriber to listen to the subject
let subscription = subject
    .sink(
        receiveCompletion: { completion in
            switch completion {
            case .finished:
                print("Finished")
            }
        },
        receiveValue: { value in
            print("Received value: \(value)")
        }
    )

// Manually send values to the subject
subject.send("Hello")
subject.send("Combine")
subject.send("World")

// Complete the subject
subject.send(completion: .finished)

// Output:
// Received value: Hello
// Received value: Combine
// Received value: World
// Finished
```
Explanation
- **Creating a subject**: The `PassthroughSubject<String, Never>()` creates a subject that emits `String` values and never fails (`Never` is the error type).

- **Subscribing**: The `sink` subscriber is attached to the subject, and it will print any values it receives.

- **Sending values**: The `send(_:)` method is used to manually emit values. In this example, "Hello", "Combine", and "World" are sent to the subscribers.

- **Completion**: The `send(completion:)` method is called to signal that no more values will be sent, completing the subject.

## ### When to use `PassthroughSubject`
- **Event broadcasting**: When you need to broadcast events like user actions, notifications, or other triggers to one or more subscribers.

- **Dynamic data sources**: For scenarios where the data source is dynamic, such as user input, sensors, or real-time data feeds.

- **Manual control**: When you want full control over when values are emitted and when the publisher completes.

## ### `PassthroughSubject`: Comparison with `CurrentValueSubject`
- **`PassthroughSubject`**: Does not store the current value, and new subscribers do not receive any previous values—only new ones sent after they subscribe.

- **`CurrentValueSubject`**: Holds onto the most recent value and sends it to any new subscribers immediately upon subscription.

## ### `CurrentValueSubject` publisher
The `CurrentValueSubject` in Combine is a special type of publisher that stores the latest value it has received and emits it to new subscribers. It combines the behavior of a regular subject (where you can manually send values) with the ability to hold onto and replay the most recent value to new subscribers.

### Key characteristics of `CurrentValueSubject`
- **Initial value**: You must initialize a `CurrentValueSubject` with an initial value, which is immediately available to any subscribers.

- **Stored value**: It always holds the latest value that was sent, and any new subscriber will immediately receive this value upon subscribing.

- **Manual control**: Similar to `PassthroughSubject`, you can manually send new values and completion events.

- **Multiple subscribers**: Multiple subscribers can attach to a `CurrentValueSubject`, and all will receive updates when new values are sent.

## ### `CurrentValueSubject` publisher usage and example
`CurrentValueSubject` is ideal when you need to maintain a current state and share it with multiple subscribers, even those that subscribe after the state has been updated.

Here’s an example of using `CurrentValueSubject` to keep track of a changing value:

```swift
import Combine

// Create a CurrentValueSubject with an initial value of "Initial Value"
let subject = CurrentValueSubject<String, Never>("Initial Value")

// Subscriber 1
let subscription1 = subject
    .sink(
        receiveCompletion: { completion in
            print("Subscriber 1 - Completion: \(completion)")
        },
        receiveValue: { value in
            print("Subscriber 1 - Received value: \(value)")
        }
    )

// Send a new value to the subject
subject.send("Hello, Combine!")

// Subscriber 2 subscribes after a value has been sent
let subscription2 = subject
    .sink(
        receiveCompletion: { completion in
            print("Subscriber 2 - Completion: \(completion)")
        },
        receiveValue: { value in
            print("Subscriber 2 - Received value: \(value)")
        }
    )

// Send another new value
subject.send("CurrentValueSubject is powerful!")

// Output:
// Subscriber 1 - Received value: Initial Value
// Subscriber 1 - Received value: Hello, Combine!
// Subscriber 2 - Received value: Hello, Combine!
// Subscriber 1 - Received value: CurrentValueSubject is powerful!
// Subscriber 2 - Received value: CurrentValueSubject is powerful!
```
Explanation
- **Initial value**: The `CurrentValueSubject` is initialized with `"Initial Value"`.

- **Subscriber 1**: This subscriber immediately receives the initial value and then receives any new values as they are sent.

- **Sending values**: The `send(_:)` method is used to manually emit new values (`"Hello, Combine!"` and `"CurrentValueSubject is powerful!"`).

- **Subscriber 2**: When Subscriber 2 subscribes, it immediately receives the most recent value (`"Hello, Combine!"`) before receiving any further updates.

## ### When to use `CurrentValueSubject`
- **State management**: When you need to maintain and share a current state with multiple subscribers, and new subscribers should immediately receive the latest state.

- **Configuration or settings**: Useful for scenarios where a configuration or setting might change, and you want all subscribers to stay up-to-date.

- **Reactive UI components**: Great for UI components that need to reflect the latest data or state.

## ### `sink` subscriber
The `sink` subscriber in Combine is a convenient and flexible way to attach a closure-based handler to a publisher. It allows you to react to emitted values and completion events in a Combine pipeline without needing to define a full custom subscriber.

### Key characteristics of `sink`
- **Closure-based**: You provide closures to handle values and completion events, making it simple to use.

- **Flexibility**: `sink` can handle both the values emitted by the publisher and its completion (whether successful or due to an error).

- **Memory management**: The returned `AnyCancellable` object must be retained if you want to keep the subscription alive; otherwise, it will automatically cancel when it goes out of scope.

## ### `sink` example: Handling values and completion
```
import Combine

// Create a simple publisher that emits values from 1 to 3
let publisher = [1, 2, 3].publisher

// Subscribe to the publisher using sink
let subscription = publisher.sink(
    receiveCompletion: { completion in
        switch completion {
        case .finished:
            print("Completed successfully.")
        case .failure(let error):
            print("Failed with error: \(error)")
        }
    },
    receiveValue: { value in
        print("Received value: \(value)")
    }
)

// Output:
// Received value: 1
// Received value: 2
// Received value: 3
// Completed successfully.
```
Explanation
1. **Publisher**: The example uses an array's `publisher` property, which emits each element of the array as a value.

2. **sink**: The `sink` method is used to handle both the values emitted by the publisher and the completion event.
- **`receiveValue`**: This closure is called each time the publisher emits a value.

- **`receiveCompletion`**: This closure is called when the publisher finishes or encounters an error.

## ### `sink` example: Handling only values
If you're only interested in the values and don't need to handle the completion, you can omit the `receiveCompletion` closure:

```swift
import Combine

// Publisher that emits strings
let stringPublisher = ["Hello", "Combine"].publisher

// Subscribe to the publisher using sink, handling only the values
let valueSubscription = stringPublisher.sink { value in
    print("Received value: \(value)")
}

// Output:
// Received value: Hello
// Received value: Combine
```
Explanation
- **Simplified subscription**: In this example, we only handle the values emitted by the publisher, omitting the completion handling.

## ### Memory management with `sink`
The `sink` method returns an `AnyCancellable` object, which is important for managing the lifetime of the subscription. If you don’t retain the `AnyCancellable`, the subscription will be automatically canceled when it goes out of scope.

Example: Storing the subscription
```swift
import Combine

class MyClass {
    var subscription: AnyCancellable?

    func start() {
        let publisher = ["One", "Two", "Three"].publisher
        subscription = publisher.sink { value in
            print("Received value: \(value)")
        }
    }
}

let myClass = MyClass()
myClass.start()

// Output:
// Received value: One
// Received value: Two
// Received value: Three
```
Explanation
- **Retaining the subscription**: The `subscription` property retains the `AnyCancellable`, ensuring that the subscription stays active until you explicitly cancel it or the `MyClass` instance is deallocated.

## ### `assign` subscriber
The `assign` subscriber in Combine is a specialized subscriber that assigns the value it receives from a publisher directly to a property of an object. It’s particularly useful when you want to bind a stream of values to a property, such as updating a UI element or a model property in response to data changes.

### Key characteristics of `assign`
- **Automatic assignment**: It automatically assigns the values received from the publisher to the specified property of an object.

- **Memory management**: Like other subscribers, `assign` returns an `AnyCancellable` object, which you need to retain if you want to keep the subscription alive.

- **No completion handling**: Unlike `sink`, `assign` only handles values and does not deal with completion or errors.

## ### `assign` subscriber usage and example
You use `assign` to create a binding between a publisher and a property on an object. This is useful for situations where you want the property to automatically reflect the latest value from the publisher.

Let’s see an example where we bind a publisher’s output to a property of a class:

```swift
import Combine

class MyModel {
    var name: String = "" {
        didSet {
            print("Name updated to: \(name)")
        }
    }
}

let model = MyModel()

// Create a publisher that emits string values
let namePublisher = ["Alice", "Bob", "Charlie"].publisher

// Use Assign to bind the publisher to the model's `name` property
let subscription = namePublisher
    .assign(to: \.name, on: model)

// Output:
// Name updated to: Alice
// Name updated to: Bob
// Name updated to: Charlie
```
Explanation
- **Publisher**: The `namePublisher` emits a sequence of strings.

- **Assign**: The `assign(to:on:)` method is used to bind the values emitted by the publisher to the `name` property of the `MyModel` instance.

- **Property updates**: The `name` property of the `MyModel` instance is updated automatically each time a new value is emitted by the publisher. The `didSet` property observer is triggered each time the `name` is updated, printing the new value.

## ### When to use `assign`?
- **Property binding**: Ideal for scenarios where you need to automatically update an object’s property in response to a stream of data.

- **UI updates**: Commonly used to bind model data to UI elements in a reactive way, ensuring the UI stays in sync with the data.

- **Simplifying code**: Reduces boilerplate code needed to manually update properties in response to data changes.

## ### Combine: Transformation Operators
- **`map`**: Transforms each value emitted by a publisher into a new value.
```swift
let numbers = [1, 2, 3].publisher
let squared = numbers.map { $0 * $0 }
```

- **`compactMap`**: Transforms values and filters out `nil` results.
```swift
let strings = ["1", "2", "three"].publisher
let numbers = strings.compactMap { Int($0) }
```

- **`flatMap`**: Maps values to new publishers and flattens them into a single stream.
```swift
let numbers = [1, 2, 3].publisher
let multiplied = numbers.flatMap { number in
    [number, number * 2].publisher
}
```

- **`scan`**: Accumulates values over time, producing a running total.
```swift
let numbers = [1, 2, 3, 4].publisher
let runningTotal = numbers.scan(0) { $0 + $1 }
```

## ### Combine: Filtering operators
- **`filter`**: Emits only values that satisfy a condition.
```swift
let numbers = [1, 2, 3, 4, 5].publisher
let evenNumbers = numbers.filter { $0 % 2 == 0 }
```

- **`removeDuplicates`**: Removes consecutive duplicate values.
```swift
let numbers = [1, 1, 2, 2, 3].publisher
let uniqueNumbers = numbers.removeDuplicates()
```

- **`dropFirst`**: Ignores the first n values.
```swift
let numbers = [1, 2, 3, 4, 5].publisher
let dropped = numbers.dropFirst(2)
```

- **`prefix`**: Takes the first n values and ignores the rest.
```swift
let numbers = [1, 2, 3, 4, 5].publisher
let firstTwo = numbers.prefix(2)
```

## ### Combine: Combining operators
- **`merge`**: Combines multiple publishers into a single stream.
```swift
let publisher1 = [1, 2, 3].publisher
let publisher2 = [4, 5, 6].publisher
let merged = publisher1.merge(with: publisher2)
```

- **`zip`**: Combines values from two publishers into pairs.
```swift
let numbers = [1, 2, 3].publisher
let letters = ["A", "B", "C"].publisher
let zipped = numbers.zip(letters)
```

- **`combineLatest`**: Combines the latest values from two publishers.
```swift
let numbers = [1, 2, 3].publisher
let letters = ["A", "B", "C"].publisher
let combined = numbers.combineLatest(letters)
```

- **`switchToLatest`**: Flattens a stream of publishers into a single stream, always switching to the latest publisher.
```swift
let subject1 = PassthroughSubject<Int, Never>()
let subject2 = PassthroughSubject<Int, Never>()
let subjects = PassthroughSubject<PassthroughSubject<Int, Never>, Never>()

let latest = subjects.switchToLatest()
```

## ### Combine: Sequence operators
- **`collect`**: Collects all values emitted by the publisher into an array.
```swift
let numbers = [1, 2, 3, 4].publisher
let array = numbers.collect()
```

- **`count`**: Counts the number of values emitted by the publisher.
```swift
let numbers = [1, 2, 3, 4].publisher
let count = numbers.count()
```

- **`first`**: Takes the first value emitted by the publisher and completes.
```swift
let numbers = [1, 2, 3, 4].publisher
let firstValue = numbers.first()
```

## ### Combine: Time operators
- **`debounce`**: Emits a value only after a specified time interval without receiving another value.
```swift
let subject = PassthroughSubject<String, Never>()
let debounced = subject.debounce(for: .seconds(1), scheduler: RunLoop.main)
```

- **`delay`**: Delays the emission of each value by a specified duration.
```swift
let subject = PassthroughSubject<Int, Never>()
let delayed = subject.delay(for: .seconds(2), scheduler: RunLoop.main)
```

- **`throttle`**: Emits the first value within a specified time interval and then suppresses others until the interval ends.
```swift
let subject = PassthroughSubject<String, Never>()
let throttled = subject.throttle(for: .seconds(2), scheduler: RunLoop.main, latest: true)
```

## ### Combine: Error handling operators
- **`catch`**: Replaces an error with another publisher.
```swift
let failingPublisher = Fail<Int, Error>(error: URLError(.badURL))

let replacementPublisher = Just(100)

let caught = failingPublisher.catch { _ in replacementPublisher }
```

- **`retry`**: Retries a failing publisher a specified number of times.
```swift
let failingPublisher = Fail<Int, Error>(error: URLError(.badURL))

let retried = failingPublisher.retry(2)
```

## ### Combine schedulers
In Combine, schedulers are responsible for controlling the timing and execution context of publishers and subscribers. They determine on which thread or queue the work should be performed, making it easier to handle asynchronous operations and ensure that UI updates occur on the main thread.

### Key concepts of schedulers
1. **Scheduler protocol**: This protocol defines when and where to execute tasks. Various types of schedulers conform to this protocol, allowing you to specify execution context (like main thread, background queue, etc.).

2. **Schedulers in Combine**:
- **Immediate**: Executes tasks immediately, without any delay. Useful for testing.

- **MainScheduler**: Ensures tasks run on the main thread, which is critical for updating the UI.

- **OperationQueueScheduler**: Executes tasks on a specified `OperationQueue`.

- **RunLoopScheduler**: Executes tasks on a specific `RunLoop`.

- **DispatchQueueScheduler**: Uses a `DispatchQueue` (from Grand Central Dispatch) to execute tasks.

## ### Commonly used schedulers: DispatchQueue
DispatchQueue: A powerful and flexible scheduler that leverages GCD to execute tasks on various dispatch queues.

Usage example:
```swift
let backgroundQueue = DispatchQueue(label: "com.example.backgroundQueue")

let publisher = Just("Hello")
    .subscribe(on: backgroundQueue)
    .receive(on: DispatchQueue.main)

publisher.sink { value in
    print("Received on main thread: \(value)")
}
```
Explanation:
- **`subscribe(on:)`** Specifies the scheduler on which the subscription should be performed. In this case, the background queue.

- **`receive(on:)`** Specifies the scheduler on which to receive values. Here, it’s set to the main thread, ensuring any UI updates are performed on the correct thread.

## ### Commonly used schedulers: RunLoop
RunLoop: A scheduler that executes tasks on a run loop, which is often used for timers and other periodic events.

Usage example:
```swift
let runLoop = RunLoop.main

let publisher = Timer.publish(every: 1.0, on: runLoop, in: .default)
    .autoconnect()
    .receive(on: DispatchQueue.main)

publisher.sink { value in
    print("Timer tick on main thread")
}
```
Explanation:
- This example sets up a timer that emits values every second on the main run loop.
- The values are received and handled on the main thread, making it safe to update the UI.

## ### Commonly used schedulers: OperationQueue
OperationQueue: A scheduler that executes tasks on an `OperationQueue`, allowing for more granular control over task execution.

Usage example:
```swift
let operationQueue = OperationQueue()

let publisher = Just("Hello")
    .subscribe(on: operationQueue)
    .receive(on: OperationQueue.main)

publisher.sink { value in
    print("Received on main operation queue: \(value)")
}
```
Explanation:
`OperationQueue` allows you to manage a queue of operations that can run concurrently or serially. The `subscribe(on:)` method sets up the publisher to start on a custom operation queue, while `receive(on:)` ensures the values are handled on the main operation queue.

## ### Combine: Using schedulers effectively
Schedulers are essential for managing threading in Combine, especially when dealing with UI updates and background tasks. By correctly using `subscribe(on:)` and `receive(on:)`, you can control where and when your Combine pipelines execute, ensuring thread safety and efficient execution.

Example: Background processing and UI updates
```swift
import Combine

let backgroundQueue = DispatchQueue(label: "backgroundQueue")
let mainQueue = DispatchQueue.main

let publisher = Just(42)
    .subscribe(on: backgroundQueue) // Perform subscription on background queue
    .map { value in
        // Simulate expensive processing
        return value * 2
    }
    .receive(on: mainQueue) // Receive value on main thread for UI updates
    .sink { value in
        print("Received value: \(value) on main thread")
    }
```

## ### `Deferred` publisher
In Combine, a `Deferred` publisher is used to delay the creation of a publisher until a subscriber actually requests it. This is particularly useful when you need to defer the execution of a publisher's work until the moment it's actually needed, rather than at the time of the publisher's declaration.

### Key concepts of `Deferred`
- **Deferred execution**: The `Deferred` publisher doesn't create the underlying publisher until a subscriber subscribes to it. This ensures that the publisher’s work is postponed until the last possible moment.

- **Dynamic publisher creation**: With `Deferred`, you can dynamically generate a new publisher every time a subscription is made, making it useful when the publisher's behavior depends on the state or configuration at the time of subscription.

## ### `Deferred` publisher usage and example
The `Deferred` publisher wraps a closure that returns a publisher. When a subscriber subscribes, this closure is executed, and the returned publisher is then used to produce values.

Let's look at an example where a `Deferred` publisher is used to simulate a deferred network request.
```swift
import Combine

// Simulate a function that returns a publisher, e.g., a network request
func fetchData() -> AnyPublisher<String, Never> {
    print("Fetching data...")
    return Just("Data fetched!")
        .delay(for: .seconds(2), scheduler: DispatchQueue.global())
        .eraseToAnyPublisher()
}

// Create a deferred publisher that calls fetchData() only when subscribed
let deferredPublisher = Deferred {
    return fetchData()
}

// Subscribe to the deferred publisher
let subscription = deferredPublisher
    .sink(receiveCompletion: { completion in
        print("Completed: \(completion)")
    }, receiveValue: { value in
        print("Received value: \(value)")
    })

// Output:
// Fetching data...
// (after 2 seconds)
// Received value: Data fetched!
// Completed: finished
```
Explanation
- **Function**: The `fetchData` function returns a `Just` publisher wrapped in a delay to simulate a network request.

- **Deferred publisher**: The `Deferred` publisher wraps the `fetchData` function. This ensures that the `fetchData` function is only called when a subscription is made.

- **Subscription**: When `sink` subscribes to the `deferredPublisher`, the `fetchData` function is called, triggering the simulated network request and eventually delivering the data.

## ### Why use `Deferred`?
- **Lazy evaluation**: If you have a publisher that performs expensive operations (like network requests or complex computations), using `Deferred` can ensure that these operations are only performed when absolutely necessary—when there's an active subscriber.

- **Dynamic data**: `Deferred` is useful when the publisher needs to be recreated each time based on the current state or context.

- **Testing**: It can be particularly helpful in testing scenarios where you need to ensure that certain actions don't occur until a subscription is made.

## ### What is list's deep copy?
A deep copy of a list (array) means creating a new array where all elements are duplicated in such a way that they do not share references with the original array. This is particularly important when dealing with arrays of reference types, such as objects or classes, where a simple assignment only creates a shallow copy (i.e., both arrays share the same objects).

Here are different ways you can perform a deep copy of a list:

1. For arrays of value types
2. For arrays of reference types
3. Using protocol
4. Handling nested arrays

## ### List deep copy: For arrays of value types
If the array contains value types (like `Int`, `String`, `Structs`, etc.), you don't need to do anything special since assigning the array or copying it will automatically create a deep copy:

```swift
let originalArray = [1, 2, 3, 4]
let copiedArray = originalArray // This is a deep copy because Int is a value type
```

## ### List deep copy: For arrays of reference types
If the array contains reference types (like classes), you'll need to manually create copies of the elements to achieve a true deep copy.

### Example with custom class
Consider a custom class Person:

```swift
class Person {
    var name: String
    
    init(name: String) {
        self.name = name
    }
    
    func copy() -> Person {
        return Person(name: self.name)
    }
}

let originalArray = [Person(name: "Alice"), Person(name: "Bob")]
```
To deep copy this array:
```swift
let copiedArray = originalArray.map { $0.copy() }
```
Explanation:
- **`map` function**: Iterates over each element in `originalArray` and applies the `copy` method, returning a new array with new `Person` instances. This ensures that `copiedArray` contains entirely new `Person` objects, independent of those in `originalArray`.

## ### List deep copy: Using protocol
You can make the Person class conform to the NSCopying protocol, which is more idiomatic:

```swift
class Person: NSCopying {
    var name: String
    
    init(name: String) {
        self.name = name
    }
    
    func copy(with zone: NSZone? = nil) -> Any {
        return Person(name: self.name)
    }
}

let originalArray = [Person(name: "Alice"), Person(name: "Bob")]

let copiedArray = originalArray.map { $0.copy() as! Person }
```
Explanation:
- **`NSCopying` protocol**: Provides a standard way to implement copying. The `copy` method returns a new instance of `Person`.

- **`map` with `copy`**: Similar to the previous example, but using the `NSCopying` protocol.

## ### List deep copy: Handling nested arrays
If you have an array of arrays or a more complex nested structure, you would need to recursively apply the deep copy logic to each level of the structure:

```swift
let originalNestedArray = [[Person(name: "Alice")], [Person(name: "Bob")]]

let copiedNestedArray = originalNestedArray.map { innerArray in
    innerArray.map { $0.copy() }
}
```

## ### What does `eraseToAnyPublisher` do?
In Combine framework, the `eraseToAnyPublisher` method is used to hide the specific type of a publisher, allowing you to return a more generic type, `AnyPublisher`, instead of the concrete type of the publisher you’re working with.

### Why use eraseToAnyPublisher?
- **Type erasure**: Combine's operators often return complex, nested types. For example, chaining operations like `map`, `flatMap` and filter on a publisher can result in a deeply nested publisher type. Returning these specific types from functions or passing them around in your code can lead to overly complex and difficult-to-maintain type signatures.

- **API flexibility**: If you're building an API or a function that returns a publisher, it's often preferable to return a generic `AnyPublisher<Output, Failure>` rather than exposing the exact type of the publisher. This abstraction allows you to change the internal implementation of the function (like replacing one operator chain with another) without affecting the function's public interface.

## ### How does `eraseToAnyPublisher` work?
The `eraseToAnyPublisher` method essentially wraps the publisher in a type-erased box. It doesn't change the behavior of the publisher; it just hides its actual type.

Here’s how you can use it:
```swift
import Combine

// A function that returns a type-erased publisher
func fetchUser() -> AnyPublisher<String, Error> {
    Just("John Doe")
        .setFailureType(to: Error.self)
        .eraseToAnyPublisher() // The actual type of the publisher is hidden
}

// Another function returning a type-erased publisher
func fetchData() -> AnyPublisher<Data, Error> {
    URLSession.shared.dataTaskPublisher(for: URL(string: "https://example.com")!)
        .map(\.data)
        .eraseToAnyPublisher()
}
```
Explanation:
- **Just("John Doe").setFailureType(to: Error.self)`**: This creates a publisher that emits a single value of `"John Doe"` and can potentially fail with an error.

- **`eraseToAnyPublisher()`**: This converts the specific publisher type (which in this case is `Just<String>.SetFailureType<Error>`) into a generic `AnyPublisher<String, Error>`.

## ### What are benefits of using `eraseToAnyPublisher`?
- **Simpler function signatures**: Instead of returning a complex type like `Map<URLSession.DataTaskPublisher, Data, URLError>`, you return `AnyPublisher<Data, URLError>`. This makes your function signatures more readable and easier to work with.

- **Encapsulation**: By hiding the actual type of the publisher, you encapsulate the implementation details. This is particularly useful when you want to maintain the flexibility to change your internal publisher logic without affecting code that depends on it.

### Example without eraseToAnyPublisher
If you didn’t use eraseToAnyPublisher, your function might return something like this:
```swift
func fetchUser() -> Publishers.MapError<Just<String>, Error> {
    Just("John Doe")
        .setFailureType(to: Error.self)
}
```
This exposes the entire type chain, which could become cumbersome and tightly couples the caller to the specific implementation details of the function. If you later decided to change the implementation, you’d also have to update the function's return type, potentially breaking the existing code.

## ### What can be Combine `flatMap` operator used for?
In Combine framework, the `flatMap` operator is a powerful tool for transforming publishers. It is particularly useful when you have a publisher that emits another publisher, and you want to flatten the sequence of publishers into a single continuous stream of values. Here are some common scenarios where `flatMap` is used:

1. **Chaining asynchronous operations**

2. **Handling multiple nested publishers**

3. **Combining results from different publishers**

4. **Dynamic publishers based on emitted values**

## ### Combine `flatMap`: Chaining asynchronous operations
When you need to perform a sequence of asynchronous operations where each operation returns a publisher, you can use `flatMap` to handle this chaining. For example, you might need to make a network request, and based on the result, make another network request.

```swift
import Combine

struct User: Decodable {
    let id: Int
    let name: String
}

struct UserDetails: Decodable {
    let email: String
    let phone: String
}

func fetchUser() -> AnyPublisher<User, Error> {
    // Simulated network request to fetch a user
    Just(User(id: 1, name: "John Doe"))
        .setFailureType(to: Error.self)
        .eraseToAnyPublisher()
}

func fetchUserDetails(userID: Int) -> AnyPublisher<UserDetails, Error> {
    // Simulated network request to fetch user details
    Just(UserDetails(email: "john.doe@example.com", phone: "123-456-7890"))
        .setFailureType(to: Error.self)
        .eraseToAnyPublisher()
}

let cancellable = fetchUser()
    .flatMap { user in
        fetchUserDetails(userID: user.id)
    }
    .sink(receiveCompletion: { completion in
        switch completion {
        case .finished:
            print("Finished")
        case .failure(let error):
            print("Error: \(error)")
        }
    }, receiveValue: { userDetails in
        print("User details: \(userDetails)")
    })
```
Explanation:
- **`fetchUser`**: Returns a publisher that emits a `User`.

- **`fetchUserDetails`**: Returns a publisher that emits `UserDetails` based on the user ID.

- **`flatMap`**: Takes the `User` emitted by `fetchUser` and uses it to create a new publisher (`fetchUserDetails`). The `flatMap` operator then flattens the resulting publishers into a single stream, allowing you to handle the final `UserDetails`.

## ### Combine `flatMap`: Handling multiple nested publishers
If you have a situation where a publisher emits publishers, and you want to merge all the inner publishers' output into a single stream, flatMap is ideal.

```swift
import Combine

let numberPublisher = PassthroughSubject<Int, Never>()

let cancellable = numberPublisher
    .flatMap { number in
        Just(number * 2) // Transform each emitted number
    }
    .sink { value in
        print("Received value: \(value)")
    }

numberPublisher.send(1)
numberPublisher.send(2)
numberPublisher.send(3)
```
Explanation:
- **`numberPublisher`**: A publisher that emits integers.

- **`flatMap`**: For each integer emitted, it returns a new publisher `Just(number * 2)`, which then emits the transformed value. `flatMap` collects these into a single stream.

## ### Combine `flatMap`: Combining results from different publishers
`flatMap` can also be used to combine results from different publishers. For example, you might want to combine data from two different network requests.

```swift
import Combine

func fetchData() -> AnyPublisher<String, Error> {
    Just("Data from first source")
        .setFailureType(to: Error.self)
        .eraseToAnyPublisher()
}

func fetchAdditionalData() -> AnyPublisher<String, Error> {
    Just("Data from second source")
        .setFailureType(to: Error.self)
        .eraseToAnyPublisher()
}

let cancellable = fetchData()
    .flatMap { firstData in
        fetchAdditionalData().map { secondData in
            "\(firstData) & \(secondData)"
        }
    }
    .sink(receiveCompletion: { completion in
        switch completion {
        case .finished:
            print("Finished")
        case .failure(let error):
            print("Error: \(error)")
        }
    }, receiveValue: { combinedData in
        print("Combined data: \(combinedData)")
    })
```
Explanation:
- **`fetchData` and `fetchAdditionalData`**: Each returns a publisher that emits a string.

- **`flatMap`**: After fetching data from the first source, it fetches additional data and combines the two results into a single output.

## ### Combine `flatMap`: Dynamic publishers based on emitted values
Sometimes, the choice of the next publisher to subscribe to depends on the value emitted by the current publisher. `flatMap` is perfect for dynamically creating a new publisher based on each value emitted.

```swift
import Combine

func fetchValue(for id: Int) -> AnyPublisher<String, Never> {
    return Just("Value for id \(id)")
        .eraseToAnyPublisher()
}

let idsPublisher = [1, 2, 3, 4].publisher

let cancellable = idsPublisher
    .flatMap { id in
        fetchValue(for: id)
    }
    .sink { value in
        print(value)
    }
```
Explanation:
- **`idsPublisher`**: A publisher that emits integers.

- **`flatMap`**: For each emitted integer, a new publisher is created `fetchValue(for: id)`. The results are then flattened into a single stream.

## ### Combine `flatMap`: Summary
In summary, `flatMap` in Combine is used when you have a publisher that produces another publisher, and you want to flatten these nested publishers into a single stream. It’s commonly used for:

- Chaining asynchronous operations.
- Handling nested publishers.
- Combining results from different publishers.
- Creating dynamic publishers based on emitted values.

This flexibility makes `flatMap` one of the most powerful operators in Combine for managing complex reactive data flows.

## ### What can be Combine `compactMap` operator used for?
In Swift's Combine framework, the compactMap operator is used to transform the output of a publisher by applying a closure that returns an optional value. If the closure returns a non-nil value, compactMap emits that value downstream. If the closure returns nil, compactMap skips the emission and does not pass anything downstream for that value.

### Common use cases for `compactMap`
1. **Filtering and transforming data**: When you have a publisher that emits values that may be `nil` after a transformation, and you want to both transform and filter out the `nil` values in a single step.

2. **Unwrapping optionals**: If your publisher emits optional values, and you only want to work with the non-`nil` values, `compactMap` can help you unwrap and filter them.

3. **Processing inputs**: In user input scenarios, where you might get optional or invalid inputs, you can use `compactMap` to filter out those invalid entries.

## ### What is `nonisolated` used for?
The `nonisolated` keyword is used to mark methods, properties, or initializers that belong to an actor but can be accessed from outside the actor’s isolation domain. This allows these members to be accessed concurrently, without requiring the actor's thread-safe execution environment.

Typically, actor members are isolated to ensure thread safety, meaning they are only accessed within the actor's execution context. However, sometimes you want a method or property to be safe to access from outside of the actor without going through the actor's protection mechanisms. This is where `nonisolated` comes in.

### Key points:
- **Actors** provide thread-safe environments for their properties and methods.
- **Nonisolated members** are accessible from outside the actor without requiring async access.
- Typically used for methods that are thread-safe on their own or don't require actor isolation.

### Example:
```swift
actor Counter {
    var value = 0
    
    // Normal method, requires access from within the actor's context
    func increment() {
        value += 1
    }

    // A nonisolated method can be accessed from outside the actor concurrently
    nonisolated func description() -> String {
        return "Counter value"
    }
}
```
In this example:
- `increment()` is an isolated method and can only be accessed asynchronously within the actor's context.
- `description()` is marked as nonisolated, so it can be accessed directly from any thread without going through the actor’s queue.

## ### Use cases for `nonisolated`
- **Computed properties** or **methods** that are thread-safe or don’t access mutable state.

- Methods that provide utility or information and don’t require synchronization with the actor’s state.

- **Static methods** in actors are implicitly nonisolated because they don’t depend on actor instance data.

### Example: Static method
Static methods in an actor don't depend on the actor's state and are `nonisolated` by default.

```swift
actor Database {
    static func version() -> String {
        return "1.0"
    }
}
```
Here, `version()` is automatically nonisolated because it doesn’t operate on the actor’s instance data.

## ### Explain the difference between `Equatable` and `Comparable` protocols
### Key differences:
1. **Equatable**:
- Used for checking equality (`==`) and inequality (`!=`).
- Provides a way to determine whether two instances are exactly the same.
- Example: `point1 == point2`.

2. **Comparable**:
- Used for determining relative order using operators like `<`,` `>,` <=` and `>=`.
- Allows sorting or comparison based on a defined order.
- Example: `point1 < point2`.

### Summary:
- `Equatable` is about checking if two instances are equal.
- `Comparable` is about comparing the relative order of two instances.
- Every `Comparable` type must also be `Equatable` but not every `Equatable` type needs to be `Comparable`.

## ### What is `@inlinable`?
`@inlinable` is an attribute that can be applied to functions, methods, computed properties, and subscripts to indicate that the body of the code should be made available for inlining across module boundaries. This means that the compiler can see the actual implementation of the function, allowing it to decide whether to inline the function when it's used in another module. Inlining can potentially improve performance by reducing function call overhead.

### Key points about `@inlinable`:
- **Cross-module inlining**: When a function or method is marked `@inlinable`, its implementation is exposed in the module's public interface. This allows the Swift compiler to inline the function into the code that uses it, even if that code is in a different module.

- **Performance**: Inlining can lead to better performance because the compiler can replace the function call with the function's body, eliminating the overhead of calling the function and enabling other optimizations like constant folding and dead code elimination.

- **ABI stability**: The attribute helps with ABI (Application Binary Interface) stability. When using `@inlinable`, you allow binary compatibility while still enabling the compiler to optimize across module boundaries.

- **Source code exposure**: Since the function body is made visible to other modules, you should be careful when marking code `@inlinable` because it exposes the actual implementation to users of the module. This can have consequences in terms of API versioning, as changes to inlinable functions may break binary compatibility.

### Example:
```swift
public struct MathOperations {
    @inlinable public static func add(_ a: Int, _ b: Int) -> Int {
        return a + b
    }
}
```
In the above code, the `add` function is marked `@inlinable`, which means that any other module that imports the module containing this struct can inline the `add` function directly into its code.

### When to use `@inlinable`:
- Use `@inlinable` for small, frequently called functions where the performance gains from inlining outweigh the cost of exposing the implementation.

- Avoid using it on complex functions that are likely to change, as this could lead to binary compatibility issues across different versions of your module.

## ### What is `@frozen`?
`@frozen` is an attribute that can be applied to enums or structs to indicate that the type’s layout and cases are fixed and cannot change in future versions of the module. This attribute is primarily used for ABI (Application Binary Interface) stability, allowing the compiler to make optimizations based on the assumption that the type's structure will not change.

### Key concepts of `@frozen`:
- **ABI stability**: When a type is marked `@frozen`, the Swift compiler can make optimizations assuming that the number of cases in an enum or the layout of fields in a struct will remain unchanged. This is important in scenarios where you're distributing a module as a binary framework and want to guarantee that future versions of the framework will maintain compatibility at the binary level.

- **Enums**:
  - For `@frozen` enums, the compiler assumes that no additional cases will be added in future versions of the library. This allows optimizations such as exhaustive switch statements, where the compiler knows that all possible cases are handled.
  - Without `@frozen`, the compiler generates code that must account for potential future cases, often requiring the use of a default case in switch statements.

- **Structs**:
  - For `@frozen` structs, the layout of stored properties is guaranteed not to change. The compiler can use this information to optimize memory layouts and other performance-sensitive code.

- **Backward compatibility**: By marking an enum or struct as `@frozen`, you're committing to not changing the structure of that type in a backward-incompatible way. This means that you cannot add new cases to an enum or add/remove properties in a struct without breaking ABI compatibility.

### Example of a @frozen enum:
```swift
@frozen public enum Direction {
    case north
    case south
    case east
    case west
}
```
With this `@frozen` enum, the compiler knows that no new cases will be added in the future, so switch statements can be exhaustive without a `default` case:

```swift
func move(direction: Direction) {
    switch direction {
    case .north:
        print("Moving north")
    case .south:
        print("Moving south")
    case .east:
        print("Moving east")
    case .west:
        print("Moving west")
    }
}
```
Without `@frozen`, you would be required to add a `default` case, as the compiler would allow for the possibility of new cases being introduced in future versions of the library.

## ### When to use `@frozen`?
- Use `@frozen` for types where you are certain that the type’s layout or cases will never change in the future.

- It is especially useful for public types in libraries or frameworks that need ABI stability.

- Be cautious with using `@frozen` if you might need to extend or modify the type in the future, as this could break binary compatibility.

## ### What is `@MainActor`?
`@MainActor` is an attribute used to ensure that certain code is executed on the main thread (the thread responsible for updating the UI in iOS and macOS apps). This is crucial because UI updates must always occur on the main thread to prevent crashes or inconsistent behavior.

### Key concepts of `@MainActor`:
- **Main thread execution**: When a function or property is marked with `@MainActor`, the Swift runtime guarantees that it will always be run on the main thread. This is particularly useful in apps where UI elements must be updated from asynchronous background operations.

- **Concurrency support**: @MainActor integrates with Swift's concurrency system (introduced in Swift 5.5), especially when working with async and await. When you mark a function as `@MainActor`, the compiler ensures that it switches to the main thread if the function is called from a background thread.

- **UI frameworks**: In iOS and macOS development, you often interact with UI elements like views, buttons, or labels. These interactions must happen on the main thread, and `@MainActor` helps ensure that the code related to these UI components runs in the correct thread.

- **Automatic thread switching**: If code marked with `@MainActor` is called from a background thread, the Swift runtime automatically schedules the execution on the main thread.

### Usage example:
```swift
import UIKit

class MyViewController: UIViewController {
    
    // This function is marked to always run on the main thread
    @MainActor func updateUI() {
        // Code to update UI elements
        self.view.backgroundColor = .red
    }
    
    func fetchData() async {
        // Simulate background work
        await Task.sleep(1_000_000_000) // 1 second delay
        
        // Now call the UI update method
        await updateUI() // Automatically switches to main thread
    }
}
```
In this example, the `updateUI()` method is marked with `@MainActor`, ensuring that any UI updates inside this function will always run on the main thread. If `fetchData()` is executed on a background thread (asynchronous task), `@MainActor` ensures that `updateUI()` is executed on the main thread when called.

## ### Key differences between `@MainActor` and `DispatchQueue.main.async`
- **@MainActor`: This is part of Swift's concurrency model, making thread handling explicit at the declaration level, which is more type-safe and can integrate smoothly with `async/await`.

- **DispatchQueue.main.async { }`: This is the more traditional way of dispatching work to the main thread, using Grand Central Dispatch (GCD). While still valid, `@MainActor` is preferred when using Swift’s modern concurrency features.

### When to use `@MainActor`:
- Use `@MainActor` for functions, properties, and methods that interact with the UI or need to run on the main thread.

- It simplifies thread management, especially when using Swift's `async/await` concurrency model.

## ### Core Image
Core Image is a powerful framework in Apple's ecosystem for image processing and analysis. It provides a wide range of image filters and utilities that allow developers to apply complex effects to images, perform real-time image processing, and even use custom filters. Core Image is designed to leverage the hardware acceleration of the CPU and GPU, making it suitable for high-performance image manipulation in iOS, macOS, and other Apple platforms.

### Key concepts of Core Image:
- **CIFilter**: The foundation of Core Image's image processing capabilities. A CIFilter is an object that represents an image filter, such as blur, color adjustment, distortion, or compositing. Each filter is defined by a set of input parameters and outputs a new image.

- **CIImage**: The class that represents an image in Core Image. It can be created from various sources, such as images from the disk, data, or even live camera input. CIImage is not a rasterized image but a description of the image and its processing pipeline, allowing deferred rendering.

- **CIContext**: A CIContext object is responsible for rendering CIImage objects into a bitmap or other output formats. It can be created using either a CPU-based context or a GPU-accelerated context, depending on the desired performance and platform.

- **Core image filters**: Core Image offers a wide range of built-in filters, including:

  - **Color adjustments**: Filters like CIColorControls, CIExposureAdjust, and CISepiaTone.
  - **Blur effects**: Filters such as CIGaussianBlur and CIBoxBlur.
  - **Distortion effects**: Filters like CIBumpDistortion or CITwirlDistortion.
  - **Compositing filters**: Filters like CISourceOverCompositing, which allow blending multiple images.

- **Custom filters**: Core Image allows developers to create custom filters by using kernels written in the Core Image Kernel Language (CIKL) or Metal shading language. These custom filters enable more specialized effects or optimizations.

- **Real-time processing**: Core Image can perform image processing in real time, making it highly suitable for apps that need to process video streams or apply live filters, such as camera apps with live effects or AR apps.

- **Performance**: Core Image is designed to be highly performant. It can leverage the GPU for hardware-accelerated image processing, which is particularly useful for real-time filters on live video or high-resolution images.

## ### Basic example using Core Image
Here’s a simple example of applying a sepia tone effect to an image using Core Image:

```swift
import UIKit
import CoreImage

func applySepiaEffect(to image: UIImage) -> UIImage? {
    guard let ciImage = CIImage(image: image) else { return nil }
    
    // Create a sepia tone filter
    let filter = CIFilter(name: "CISepiaTone")
    filter?.setValue(ciImage, forKey: kCIInputImageKey)
    filter?.setValue(0.8, forKey: kCIInputIntensityKey)
    
    // Get the filtered image output
    guard let outputImage = filter?.outputImage else { return nil }
    
    // Create a CIContext and render the filtered image into a UIImage
    let context = CIContext()
    if let cgImage = context.createCGImage(outputImage, from: outputImage.extent) {
        return UIImage(cgImage: cgImage)
    }
    
    return nil
}
```
In this example:
- `CIFilter` is used to apply a sepia tone effect to a `CIImage`.
- The filter processes the image based on the intensity level set by the developer.
- The final output is rendered using a `CIContext` to convert the processed `CIImage` into a `UIImage`.

## ### Core Image features
- **Image enhancement**: Core Image includes filters for automatic enhancement (`CIAutoAdjustment`) to adjust contrast, color, and brightness automatically.

- **Face detection**: Core Image provides face detection capabilities via `CIDetector` and `CIFeature`.

- **Vector graphics rendering**: You can render vector shapes as `CIImage` objects using filters like `CICheckerboardGenerator` and `CIRectangleGenerator`.

- **Custom filters**: With custom kernels, you can create your own filters for specific processing requirements.

## ### Core Animation
Core Animation is a powerful animation framework provided by Apple that allows developers to create smooth, visually appealing animations in iOS, macOS, watchOS, and tvOS applications. Core Animation works at a lower level than UI frameworks like UIKit or AppKit, making it highly efficient for rendering animations directly on the GPU, thus offloading much of the work from the CPU.

## ### Core Animation: CALayer
- The fundamental building block in Core Animation is the `CALayer` class, which represents a rectangular block of content that can be animated. Every view in UIKit or AppKit has a `CALayer` backing it, allowing Core Animation to work seamlessly with the UI.

- Properties of a layer, such as its position, size, background color, opacity, and transform, can be animated without redrawing the view’s content.

## ### Core Animation: Implicit animations
Core Animation provides implicit animations. When you change the animatable properties of a CALayer, Core Animation automatically animates the change. For instance, changing the position of a layer animates it smoothly to the new position by default.

Example:
```swift
let layer = view.layer
layer.position = CGPoint(x: 200, y: 200)
```
This will cause the layer to animate its position from the old value to the new value.

## ### Core Animation: Explicit animations
- If you want more control over animations, you can create explicit animations using `CABasicAnimation`, `CAKeyframeAnimation`, `CAAnimationGroup` or `CATransition`.

- With explicit animations, you create the animation object, configure its properties (such as duration, timing, etc.), and then apply it to a `CALayer`.

Example of an explicit animation:
```swift
let animation = CABasicAnimation(keyPath: "opacity")
animation.fromValue = 1.0
animation.toValue = 0.0
animation.duration = 1.0
layer.add(animation, forKey: "fade")
```

## ### Core Animation: Animation timing
Core Animation supports various timing functions to control the speed of animations, such as `ease-in`, `ease-out` and linear animations. These timing functions can be set via `CAMediaTimingFunction`.

Example:
```swift
let timingFunction = CAMediaTimingFunction(name: .easeInEaseOut)
animation.timingFunction = timingFunction
```

## ### Core Animation: Transactions
- `CATransaction` is used to group multiple animations together and control their properties (e.g., timing). Transactions allow you to start and commit animations explicitly.

- By default, all animations are grouped into an implicit transaction that commits automatically at the end of the current run loop cycle.

Example of using a transaction:
```swift
CATransaction.begin()
CATransaction.setAnimationDuration(2.0)
layer.position = CGPoint(x: 300, y: 300)
CATransaction.commit()
```

## ### Core Animation: Keyframe animations
CAKeyframeAnimation allows you to specify multiple values for a property at different times during the animation. This is useful when you want more complex animations than simple start-to-end transitions.

Example of keyframe animation:
```swift
let keyframeAnimation = CAKeyframeAnimation(keyPath: "position")
keyframeAnimation.values = [NSValue(cgPoint: CGPoint(x: 0, y: 0)),
                            NSValue(cgPoint: CGPoint(x: 100, y: 100)),
                            NSValue(cgPoint: CGPoint(x: 200, y: 0))]
keyframeAnimation.duration = 2.0
layer.add(keyframeAnimation, forKey: "position")
```

## ### Core Animation: Layer hierarchies
Core Animation layers can be arranged in hierarchies, similar to views. Parent layers influence the behavior of child layers, and you can apply animations to entire layer hierarchies.

## ### Core Animation: Transformations
You can apply 3D transformations to layers using the `CATransform3D` struct. Core Animation can handle rotations, translations, and scaling in 3D space.

Example of a 3D rotation:
```swift
let rotation = CATransform3DMakeRotation(CGFloat.pi, 0, 1, 0)
layer.transform = rotation
```

## ### Core Animation: Core animation on the GPU
One of the key reasons Core Animation is so performant is that it works closely with the GPU. The layers and animations are rendered on the GPU, freeing up the CPU for other tasks, like handling touch events or business logic.

## ### Core Animation types
- **CABasicAnimation**: Animates a single property from a start value to an end value.

- **CAKeyframeAnimation**: Animates a property through a series of values (keyframes).

- **CAAnimationGroup**: Combines multiple animations to run in parallel.

- **CATransition**: Adds transitions between two different states (such as fading or sliding).

## ### Core Animation: Layer masking
You can use one `CALayer` to mask another, allowing you to create complex effects like rounded corners or clipping based on shape.

Example:
```swift
let maskLayer = CALayer()
maskLayer.frame = yourView.bounds
maskLayer.contents = yourMaskImage.cgImage
yourView.layer.mask = maskLayer
```

## ### Core Animation: Replicating layers
`CAReplicatorLayer` creates copies (or "replicas") of a layer, each with a slight transformation. This can be used for effects like repeating patterns, waveforms, or 3D visuals.

Example:
```swift
let replicatorLayer = CAReplicatorLayer()
replicatorLayer.instanceCount = 10
replicatorLayer.instanceTransform = CATransform3DMakeTranslation(30, 0, 0)
replicatorLayer.addSublayer(yourLayer)
```

## ### Core Animation: Emitter layers
`CAEmitterLayer` is used to create particle systems. You can define the shape, color, speed, and behavior of the particles.

Example:
```swift
let emitterLayer = CAEmitterLayer()
emitterLayer.emitterPosition = CGPoint(x: 200, y: 200)
let cell = CAEmitterCell()
cell.birthRate = 100
cell.lifetime = 5.0
cell.velocity = 100
emitterLayer.emitterCells = [cell]
```

## ### Core Animation: Delegates
Core Animation allows you to set delegates for animations. This is useful when you need to execute code at certain points during an animation (such as when it starts or finishes).

Example:
```swift
animation.delegate = self
func animationDidStop(_ anim: CAAnimation, finished flag: Bool) {
    // Handle completion
}
```

## ### Core Animation: Performance considerations
- **Offscreen rendering**: Be cautious with operations like shadows and masking, as they may trigger offscreen rendering, which can impact performance. Always profile using instruments like the Core Animation Instrument to avoid bottlenecks.

- **Reduce overdraw**: Ensure that layers do not overlap unnecessarily or have transparency where it's not needed, as overdraw can lead to degraded performance.

## ### Core Animation: Practical use cases
- **Custom UI effects**: Create custom button animations, splash screens or interactive transitions between views.

- **Data visualizations**: Animate charts, graphs, or progress indicators smoothly.

- **Game UI**: Use Core Animation to build responsive and fluid UIs for games.

- **Real-time feedback**: Provide feedback like shaking or bouncing effects for interactive elements like text fields or buttons.

## ### AVFoundation
AVFoundation is a comprehensive framework provided by Apple that enables developers to work with time-based audiovisual media in iOS, macOS, tvOS, and watchOS. It offers powerful tools for capturing, processing, editing, playing, and exporting audio and video content. AVFoundation provides low-level access to media data, making it an essential framework for apps that require complex media handling like camera control, video editing, or custom audio processing.

### Key features of AVFoundation
1. Media playback:
- Play audio and video files, streams, and remote media using AVPlayer and AVPlayerLayer.
- Supports background audio playback and media streaming.

2. Media capture:
- Use the device’s camera and microphone to capture live audio and video using `AVCaptureSession`, `AVCaptureDevice`, `AVCaptureInput` and `AVCaptureOutput`.

3. Media composition and editing:
- Create, edit, and export complex audiovisual compositions using `AVComposition`, `AVAsset` and `AVMutableComposition`.

4. Media export and transcoding:
- Transcode and export media in various formats using `AVAssetExportSession`.

5. Metadata management:
- Read and write metadata in media files using `AVMetadataItem` and `AVMetadataFormat`.

6. Audio processing:
- Advanced control over audio output, including mixing, recording, and applying audio effects.

## ### AVFoundation: `AVPlayer` and `AVPlayerLayer`
- `AVPlayer` is used to play audio or video files and streams.
- `AVPlayerLayer` can display video content in a view by adding it to a layer.
- You can control playback (play, pause, seek) and manage playback state (e.g., buffering, end of playback).

Example:
```swift
let url = URL(string: "https://example.com/video.mp4")

let player = AVPlayer(url: url!)

let playerLayer = AVPlayerLayer(player: player)

playerLayer.frame = view.bounds

view.layer.addSublayer(playerLayer)
player.play()
```

## ### AVFoundation: AVCaptureSession and Media Capture
- `AVCaptureSession` is used to configure real-time capture from the camera or microphone. You configure it by adding input devices (camera or mic) and output (such as a file or preview layer).
- `AVCaptureDevice` represents the physical camera or microphone.
- `AVCaptureVideoPreviewLayer` allows you to display a live camera feed in a view.

Example: Capturing video from the camera
```swift
let captureSession = AVCaptureSession()

guard let videoDevice = AVCaptureDevice.default(for: .video) else { return }

let videoInput = try AVCaptureDeviceInput(device: videoDevice)
captureSession.addInput(videoInput)

let previewLayer = AVCaptureVideoPreviewLayer(session: captureSession)
previewLayer.frame = view.bounds
view.layer.addSublayer(previewLayer)

captureSession.startRunning()
```

## ### AVFoundation: AVComposition and Media Editing
- `AVComposition` allows you to create a timeline-based audiovisual composition by combining different media tracks (audio, video).
- `AVMutableComposition` is its mutable counterpart, used to edit and add tracks.
- You can apply time-based edits, such as trimming, merging, or applying audio tracks, subtitles, or transitions.

Example: Combining two videos
```swift
let composition = AVMutableComposition()

// Add video track from asset 1
let videoTrack = composition.addMutableTrack(withMediaType: .video, preferredTrackID: kCMPersistentTrackID_Invalid)

let videoAsset = AVURLAsset(url: firstVideoURL)

try videoTrack?.insertTimeRange(CMTimeRange(start: .zero, duration: videoAsset.duration),
                                of: videoAsset.tracks(withMediaType: .video).first!,
                                at: .zero)

// Add video track from asset 2
let secondVideoAsset = AVURLAsset(url: secondVideoURL)

try videoTrack?.insertTimeRange(CMTimeRange(start: .zero, duration: secondVideoAsset.duration),
                                of: secondVideoAsset.tracks(withMediaType: .video).first!,
                                at: videoAsset.duration)

// You can then export this composition
```

## ### AVFoundation: AVAssetExportSession
`AVAssetExportSession` is used to export or transcode media. You can specify output file types, preset qualities (like 1080p or 720p), and apply compression.

Example: Exporting a video
```swift
let exportSession = AVAssetExportSession(asset: composition, presetName: 

AVAssetExportPresetHighestQuality)

exportSession?.outputURL = outputFileURL

exportSession?.outputFileType = .mov

exportSession?.exportAsynchronously {
    if exportSession?.status == .completed {
        // Export succeeded
    } else if let error = exportSession?.error {
        print("Error: \(error.localizedDescription)")
    }
}
```

## ### AVFoundation: Metadata Management
You can retrieve and modify metadata from media files, like artist names, album titles, or video captions, using `AVMetadataItem`.

Example: Reading metadata from an asset
```swift
let asset = AVAsset(url: videoURL)

let metadata = asset.metadata(forFormat: AVMetadataFormat.quickTimeMetadata)

for item in metadata {
    print("Key: \(item.key), Value: \(item.value)")
}
```

## ### AVFoundation: Audio Processing
- AVFoundation also offers advanced audio manipulation with `AVAudioEngine` and `AVAudioPlayer`.
- `AVAudioEngine` allows developers to create real-time audio graphs, apply effects, and manage audio inputs/outputs.
- `AVAudioPlayer` is a simple API for playing audio files, controlling playback, and handling audio events.

Example: Playing an audio file
```swift
let player = try AVAudioPlayer(contentsOf: audioURL)
player.play()
```

## ### AVFoundation: Time-based media operations
- AVFoundation provides control over time-based operations such as seeking, trimming, and synchronizing media tracks.

- You can work with `CMTime`, `CMTimeRange` and `CMTimeMapping` to handle time-based operations.

## ### AVFoundation: Real-time video effects
By using the media capture capabilities (`AVCaptureVideoDataOutput`), you can capture frames from the camera in real-time, process them (e.g., apply filters or effects), and render the processed frames back to the screen.

Example: Adding a filter to a live camera feed
```swift
let videoOutput = AVCaptureVideoDataOutput()

videoOutput.setSampleBufferDelegate(self, queue: DispatchQueue(label: "videoQueue"))
captureSession.addOutput(videoOutput)

func captureOutput(_ output: AVCaptureOutput, didOutput sampleBuffer: CMSampleBuffer, from connection: AVCaptureConnection) {

    guard let pixelBuffer = CMSampleBufferGetImageBuffer(sampleBuffer) else { return }
    
    // Apply filters using Core Image
    let ciImage = CIImage(cvPixelBuffer: pixelBuffer)

    let filter = CIFilter(name: "CISepiaTone")

    filter?.setValue(ciImage, forKey: kCIInputImageKey)

    filter?.setValue(0.9, forKey: kCIInputIntensityKey)
    
    // Render the output to screen or process further
}
```

## ### Best practices for AVFoundation
- **Handle memory efficiently**:
Use appropriate configurations for capture sessions (e.g., reducing resolution or frame rate) to avoid overloading memory or processing capacity.

- **Asynchronous operations**:
Media loading, exporting, and playback are often asynchronous, so make sure to handle these tasks with completion handlers and error checking.

- **Use hardware acceleration**:
AVFoundation takes advantage of hardware acceleration, especially for video encoding and decoding. For optimal performance, ensure you use the appropriate video encoding presets for your target device.

- **Error handling**:
Always handle errors when performing tasks like media export, capture, or playback. Use the completion blocks to check the status and manage errors accordingly.
