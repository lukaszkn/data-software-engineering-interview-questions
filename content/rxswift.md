# RxSwift
Basics of RxSwift

* [What is RxSwift?](#What-is-RxSwift)
* [Observable](#Observable)
* [Observer](#Observer)
* [Operators](#Operators)
* [Subjects](#Subjects)
* [Disposables and dispose bags](#Disposables-and-dispose-bags)
* [Schedulers](#Schedulers)
* [Benefits of RxSwift](#Benefits-of-RxSwift)
* [Common use cases](#Common-use-cases)
* [Example with 2 fields and button](#Example-with-2-fields-and-button)
* [What is RxCocoa?](#What-is-RxCocoa)
* [Reactive bindings for UI components](#Reactive-bindings-for-UI-components)
* [Handling UI Events](#Handling-UI-Events)
* [Driver](#Driver)
* [Relay](#Relay)
* [Built-in UI bindings](#Built-in-UI-bindings)
* [DelegateProxy](#DelegateProxy)
* [Example of `UITextField` and `UIButton` tap](#Example-of-UITextField-and-UIButton-tap)
* [Use cases for RxCocoa](#Use-cases-for-RxCocoa)
* [Advantages of RxCocoa](#Advantages-of-RxCocoa)
* [What is Subject?](#What-is-Subject)
* [PublishSubject](#PublishSubject)
* [BehaviorSubject](#BehaviorSubject)
* [ReplaySubject](#ReplaySubject)
* [AsyncSubject](#AsyncSubject)
* [Common use cases for subjects](#Common-use-cases-for-subjects)
* [Binder](#Binder)
* [Creating a Binder](#Creating-a-Binder)
* [Using a `Binder` to bind data to UI components](#Using-a-Binder-to-bind-data-to-UI-components)
* [Benefits of `Binder`](#Benefits-of-Binder)
* [What is RxRelay?](#What-is-RxRelay)
* [PublishRelay](#PublishRelay)
* [BehaviorRelay](#BehaviorRelay)
* [Why use RxRelay?](#Why-use-RxRelay)
* [Practical use cases for RxRelay](#Practical-use-cases-for-RxRelay)
* [Choosing the right publisher/observable](#Choosing-the-right-publisher-observable)
* [`Observable.create`](#Observable-create)
* [`Observable.interval`](#Observable-interval)
* [`Observable.timer`](#Observable-timer)
* [`Observable.deferred`](#Observable-deferred)
* [Transforming operators](#Transforming-operators)
* [Filtering operators](#Filtering-operators)
* [Combining operators](#Combining-operators)
* [Error handling operators](#Error-handling-operators)
* [Time-based operators](#Time-based-operators)
* [Utility operators](#Utility-operators)
* [Conditional and boolean operators](#Conditional-and-boolean-operators)

## What is RxSwift?
RxSwift is a powerful framework for handling asynchronous and event-based programming using observable sequences. It is based on Reactive Extensions (Rx) which uses functional programming with streams and observables to manage and compose asynchronous data sequences.

In RxSwift, instead of directly handling states and events with traditional callbacks or delegates, you work with observables and observers, where:

- **Observable**: Represents a sequence of values or events that can be asynchronously emitted over time.

- **Observer**: Listens and reacts to those values or events emitted by an observable.

[Top](#top)

## Observable
- Core to RxSwift, an observable is a sequence that produces elements over time.

- Observables can emit events like .next (when a new element is emitted), .completed (when the observable sequence completes), and .error (when an error occurs).

```swift
let observable = Observable.of("Hello", "World")
```

[Top](#top)

## Observer
- Observers or subscribers, are interested in receiving elements from observables. Once an observer subscribes to an observable, it will start receiving values or events.

```swift
observable.subscribe { event in
    print(event)
}
```

[Top](#top)

## Operators
- RxSwift includes many operators (similar to Combine) to help transform, filter, and combine observables. Some commonly used operators include `map`, `filter`, `merge`, `combineLatest`, `flatMap` and `reduce`.

```swift
let numbers = Observable.of(1, 2, 3)

numbers.map { $0 * 2 }
    .subscribe(onNext: { print($0) })
```

[Top](#top)

## Subjects
- Subjects are special types of observables that are also observers. They can subscribe to other observables and emit their own values.

- There are four main types of subjects:
  - **PublishSubject**: Starts empty and only emits new items to subscribers.

  - **BehaviorSubject**: Requires an initial value and emits the last or latest element to new subscribers.

  - **ReplaySubject**: Replays a specific number of past elements to new subscribers.

  - **AsyncSubject**: Emits the last element and only completes the sequence.

```swift
let subject = PublishSubject<String>()

subject.onNext("Hello")  // No subscribers yet, so no emission

subject.subscribe(onNext: { print($0) })

subject.onNext("World")  // Emits "World" to subscribers
````

[Top](#top)

## Disposables and dispose bags
- RxSwift uses `DisposeBag` to manage the lifecycle of subscriptions. When a subscription is added to a `DisposeBag`, it is automatically disposed of when the bag itself is deallocated, preventing memory leaks.

```swift
let disposeBag = DisposeBag()
observable
    .subscribe(onNext: { print($0) })
    .disposed(by: disposeBag)
```

[Top](#top)

## Schedulers
` Schedulers allow you to specify on which thread or queue code should run. Commonly used schedulers in RxSwift are `MainScheduler` (for UI updates), `ConcurrentDispatchQueueScheduler` (for background tasks) and `SerialDispatchQueueScheduler`.

```swift
observable
    .observe(on: MainScheduler.instance)
    .subscribe(onNext: { print($0) })
    .disposed(by: disposeBag)
```

[Top](#top)

## Benefits of RxSwift
- **Asynchronous handling**: Simplifies handling asynchronous events, especially when working with complex event-driven programming.

- **Declarative code**: Reactive code is more declarative, focusing on "what" should happen rather than "how" it happens.

- **Composition**: The operators make it easy to compose and chain different asynchronous sequences, which is often cleaner than nested callbacks.

- **Thread management**: Provides built-in thread management, making it easier to handle work on background threads and update the UI on the main thread.

[Top](#top)

## Common use cases
- **Networking**: Handle API responses and error handling, especially when chaining multiple API calls.

- **Form validation**: Combine different input fields’ states to enable or disable a submit button dynamically.

- **Real-time search**: Stream user input in a search field and make network requests in real-time while throttling requests.

- **UI binding**: Bind observable sequences to UI components, such as updating a label’s text when a property changes.

[Top](#top)

## Example with 2 fields and button
Let's look at an example where a simple login form is created with two fields, username and password, and a loginButton that becomes enabled only when both fields are non-empty.

```swift
let username = BehaviorSubject<String>(value: "")

let password = BehaviorSubject<String>(value: "")

Observable.combineLatest(username, password) { username, password in
    return !username.isEmpty && !password.isEmpty
}
.bind(to: loginButton.rx.isEnabled)
.disposed(by: disposeBag)
```

In this example:
- `BehaviorSubject` emits an initial value and the latest values of `username` and `password`.

- `combineLatest` combines both observables and emits true only if both `username` and `password` are non-empty.

- `.bind(to:)` binds the result to the `isEnabled` property of `loginButton`.

[Top](#top)

## What is RxCocoa?
RxCocoa is an extension of the RxSwift framework that provides reactive extensions specifically for Apple’s Cocoa and UIKit frameworks. It enables seamless integration of RxSwift’s reactive programming model into the iOS and macOS UI components, such as `UIButton`, `UILabel`, `UITextField` and more.

While RxSwift focuses on reactive programming in general, RxCocoa adds reactive capabilities to Cocoa touch frameworks, making it easier to manage UI state changes, handle user input, and respond to UI events in a declarative and reactive way.

[Top](#top)

## Reactive bindings for UI components
- RxCocoa allows you to create observable properties for UI elements. For instance, you can reactively observe text changes in a `UITextField`, the title of a `UIButton` or the value of a `UISlider`.

- RxCocoa makes it easy to bind reactive observables directly to UI elements without needing traditional delegation or callback methods.

```swift
// Bind text changes from textField to label
textField.rx.text
    .orEmpty // RxCocoa extension
    .bind(to: label.rx.text)
    .disposed(by: disposeBag)
```

[Top](#top)

## Handling UI Events
- RxCocoa provides reactive wrappers for common UI events such as taps, swipes, scrolling, and editing changes. Instead of implementing delegate methods, you can subscribe directly to these events and handle them in closures.

```swift
button.rx.tap
    .subscribe(onNext: { print("Button tapped") })
    .disposed(by: disposeBag)
```

[Top](#top)

## Driver
- `Driver` is a specialized type in RxCocoa designed for UI-related sequences that must always run on the main thread and cannot fail.

- It is ideal for binding asynchronous data to the UI because it guarantees the sequence will deliver the last known value to new subscribers and always work on the main thread.

- `Driver` can be created from any observable using `.asDriver(onErrorJustReturn:)`

```swift
let textDriver = textField.rx.text.orEmpty.asDriver()

textDriver
    .drive(label.rx.text)
    .disposed(by: disposeBag)
```

[Top](#top)

## Relay
Relay is a wrapper around subjects that never emit a completion event. There are two main types:
- `PublishRelay`: Starts empty and only emits new elements to subscribers.

- `BehaviorRelay`: Starts with an initial value and replays the latest value to new subscribers.

Relays are useful for UI elements because they don’t complete, which matches the behavior expected in most UI-driven applications.

```swift
let relay = BehaviorRelay(value: "Initial value")

relay.accept("Updated value")

relay.bind(to: label.rx.text)
    .disposed(by: disposeBag)
```

[Top](#top)

## Built-in UI bindings
- RxCocoa offers a variety of built-in bindings to easily connect reactive streams to UIKit properties.

- Common bindings include:
  - `rx.isEnabled` for enabling/disabling buttons.

  - `rx.text` for setting or observing text in `UILabel` or `UITextField`.

  - `rx.value` for `UISlider`, `UISwitch`, etc.

[Top](#top)

## DelegateProxy
RxCocoa uses `DelegateProxy` to enable delegation-based APIs to work with RxSwift. It allows events from delegate methods to be converted to observables, making them compatible with RxSwift’s declarative syntax.

[Top](#top)

## Example of `UITextField` and `UIButton` tap
Imagine an app where a `UITextField` and `UIButton` are used to enable a search feature. The button should only be enabled when the user has entered at least three characters in the text field.

```swift
import RxSwift
import RxCocoa

let disposeBag = DisposeBag()

textField.rx.text.orEmpty
    .map { $0.count >= 3 }
    .bind(to: button.rx.isEnabled)
    .disposed(by: disposeBag)

button.rx.tap
    .subscribe(onNext: { print("Search button tapped!") })
    .disposed(by: disposeBag)
```

Here’s what’s happening in this example:
- `textField.rx.text.orEmpty`: Creates a reactive stream that observes changes to the text in the UITextField.

- `.map { $0.count >= 3 }`: Maps the text to a Boolean, where `true` is returned if the text has three or more characters.

- `.bind(to: button.rx.isEnabled)`: Binds this Boolean to the `isEnabled` property of the `UIButton`.

- `button.rx.tap`: Subscribes to the tap event on the button, triggering a search action.

[Top](#top)

## Use cases for RxCocoa
- **Two-way binding**: For example, binding a text field to a model so that updates in the model reflect in the UI.

- **Form validation**: Enabling/disabling buttons based on the validity of form input fields.

- **TableView/CollectionView binding**: RxCocoa provides convenient extensions to bind observable data to `UITableView` or `UICollectionView` data sources.

- **UI event handling**: Handling taps, drags, gestures, and other UI interactions reactively.

[Top](#top)

## Advantages of RxCocoa
- **Declarative UI code**: Code is more concise and declarative, making it easier to understand and maintain.

- **Unified data flow**: Simplifies state management and reduces the need for delegation, callback, and NotificationCenter patterns.

- **Enhanced code readability**: By using RxCocoa bindings, you can eliminate the need for much boilerplate code, improving readability.

- **Reactive patterns for UI**: Makes it easier to adopt reactive patterns across both data and UI components, improving modularity and maintainability.

[Top](#top)

## What is Subject?
A Subject is a type that is both an Observable (it can emit events) and an Observer (it can subscribe to and receive events from other observables). Subjects act as bridges or proxies, relaying or emitting events to their subscribers. They are often used when you need to inject new values into a stream or manage shared state.

There are four primary types of subjects in RxSwift:
- PublishSubject
- BehaviorSubject
- ReplaySubject
- AsyncSubject

Each has unique properties and use cases.

[Top](#top)

## PublishSubject
- **Description**: `PublishSubject` starts empty and only emits new elements to its subscribers.
- **Use case**: Use when you want subscribers to receive events only after they’ve subscribed.

Example:
```swift
import RxSwift

let publishSubject = PublishSubject<String>()
let disposeBag = DisposeBag()

// Subscriber 1
publishSubject.subscribe(onNext: { print("Subscriber 1: \($0)") })
    .disposed(by: disposeBag)

publishSubject.onNext("Hello")  // Output: "Subscriber 1: Hello"

// Subscriber 2 joins after the first event
publishSubject.subscribe(onNext: { print("Subscriber 2: \($0)") })
    .disposed(by: disposeBag)

publishSubject.onNext("World")  // Output: "Subscriber 1: World", "Subscriber 2: World"
```

[Top](#top)

## BehaviorSubject
- **Description**: `BehaviorSubject` requires an initial value and replays the latest value to new subscribers.
- **Use case**: Use when you want subscribers to immediately receive the latest value upon subscribing, even if they join late.

Example:
```swift
let behaviorSubject = BehaviorSubject(value: "Initial")
let disposeBag = DisposeBag()

behaviorSubject.onNext("Hello")  // Latest value is "Hello"

// Subscriber 1
behaviorSubject.subscribe(onNext: { print("Subscriber 1: \($0)") })
    .disposed(by: disposeBag)

// Output: "Subscriber 1: Hello"

// Subscriber 2 joins later
behaviorSubject.subscribe(onNext: { print("Subscriber 2: \($0)") })
    .disposed(by: disposeBag)

// Output for Subscriber 2: "Hello"
behaviorSubject.onNext("World")  // Both Subscriber 1 and 2 receive "World"
```

[Top](#top)

## ReplaySubject
- **Description**: `ReplaySubject` stores a buffer of recent values (specified at creation) and replays them to new subscribers.

- **Use case**: Use when you want new subscribers to catch up on recent events (up to a specified limit) when they subscribe.

Example:
```swift
let replaySubject = ReplaySubject<String>.create(bufferSize: 2)
let disposeBag = DisposeBag()

replaySubject.onNext("First")
replaySubject.onNext("Second")
replaySubject.onNext("Third")

// Subscriber joins and receives the last two values
replaySubject.subscribe(onNext: { print("Subscriber: \($0)") })
    .disposed(by: disposeBag)

// Output:
// "Subscriber: Second"
// "Subscriber: Third"
```

[Top](#top)

## AsyncSubject
- **Description**: `AsyncSubject` only emits the last value and only after the sequence completes.

- **Use case**: Use when you only care about the final value after completion (e.g., a result of a lengthy computation).

Example:
```swift
let asyncSubject = AsyncSubject<String>()
let disposeBag = DisposeBag()

// Subscriber
asyncSubject.subscribe(onNext: { print("Subscriber: \($0)") })
    .disposed(by: disposeBag)

asyncSubject.onNext("Hello")
asyncSubject.onNext("World")
asyncSubject.onCompleted()  // Only emits "World" upon completion

// Output:
// "Subscriber: World"
```

[Top](#top)

## Common use cases for subjects
- **Event dispatching**: Use `PublishSubject` for one-time events, like button taps or notifications.

- **State management**: Use `BehaviorSubject` for maintaining and sharing state that might change, such as form inputs.

- **Caching events**: Use `ReplaySubject` if you want new subscribers to "catch up" on recent events (up to a limit).

- **Final results**: Use `AsyncSubject` for sequences where only the last emitted item upon completion is important.

[Top](#top)

## Binder
In RxCocoa, Binder is a specialized observer type used to bind UI elements in a safe, consistent way. A Binder is an observer that’s always bound to the main thread, making it ideal for UI updates. It provides a convenient way to update UI components in a reactive fashion without worrying about thread safety.

Key characteristics of Binder
- **Main thread execution**: Ensures that the UI updates always happen on the main thread, which is crucial for UIKit interactions.

- **Memory management**: Automatically disposes of the binding when the observer is deallocated, helping to prevent memory leaks.

- **Error handling**: Unlike typical RxSwift observers, Binder does not handle errors. It's designed this way because UI elements don’t usually have a way to handle or display errors directly.

[Top](#top)

## Creating a Binder
A Binder can be created with an `onNext` closure that defines how to update the UI. The syntax requires specifying the type of the value the Binder will observe and how it should handle that value.

```swift
let label = UILabel()
let disposeBag = DisposeBag()

let textBinder = Binder<String>(label) { label, text in
    label.text = text
}
```
In this example:
- `textBinder` is a Binder for `String` values.
- The closure `label.text = text` defines how each new string will update the `UILabel`'s text.

[Top](#top)

## Using a `Binder` to bind data to UI components
Binder works well with RxSwift’s `bind(to:)` syntax, which allows for binding observable data streams directly to UI elements.

```swift
let textObservable = Observable.just("Hello, RxCocoa!")

textObservable
    .bind(to: label.rx.text) // Using RxCocoa’s built-in binders
    .disposed(by: disposeBag)
```
In this example, label.rx.text is a Binder provided by RxCocoa that updates the UILabel text property with each new emitted value.

[Top](#top)

## Benefits of `Binder`
- **Safe UI updates**: Always executes on the main thread, so you don’t need to worry about thread management for UI work.

- **Cleaner code**: Helps you create reusable, declarative bindings for UI components.

- **Reduces boilerplate**: RxCocoa provides many built-in binders for common properties like `rx.text`, `rx.isEnabled` and others, which minimizes the need for custom bindings.

[Top](#top)

## What is RxRelay?
RxRelay is a part of the RxSwift ecosystem and provides special wrappers around Subjects that are stateful, meaning they maintain and emit the latest value, and non-completing, which means they never emit a completed or error event. This makes RxRelay ideal for managing state in reactive applications, especially UI-driven ones, where you generally don't want streams to terminate unexpectedly.

The main types in RxRelay are:
- `PublishRelay`
- `BehaviorRelay`
- `ReplayRelay`

Each has its unique properties and use cases

[Top](#top)

## PublishRelay
- `PublishRelay` is essentially a wrapper around `PublishSubject` that does not emit completion events.
- It starts as an empty relay and only emits new elements to subscribers.
- It’s great for emitting events like button taps or other one-time actions.

Example:
```swift
import RxRelay
import RxSwift

let publishRelay = PublishRelay<String>()
let disposeBag = DisposeBag()

// Subscriber 1
publishRelay.subscribe(onNext: { value in
    print("Subscriber 1: \(value)")
})
.disposed(by: disposeBag)

publishRelay.accept("Hello")  // Output: "Subscriber 1: Hello"
publishRelay.accept("World")  // Output: "Subscriber 1: World"
```
In this example:
- The `PublishRelay` emits "Hello" and "World" only to active subscribers.
- If a new subscriber subscribes after these values are emitted, they won't receive these past values.

[Top](#top)

## BehaviorRelay
- `BehaviorRelay` is a wrapper around `BehaviorSubject` and requires an initial value.
- It stores the latest value and replays it to new subscribers immediately upon subscription.
- It’s ideal for managing state that needs to be observed as well as retained (like form inputs or user settings).

Example:
```swift
import RxRelay
import RxSwift

let behaviorRelay = BehaviorRelay(value: "Initial Value")
let disposeBag = DisposeBag()

// Subscriber 1
behaviorRelay.subscribe(onNext: { value in
    print("Subscriber 1: \(value)")
})
.disposed(by: disposeBag)

behaviorRelay.accept("New Value")  // Output: "Subscriber 1: New Value"

// Subscriber 2, joining later
behaviorRelay.subscribe(onNext: { value in
    print("Subscriber 2: \(value)")
}).disposed(by: disposeBag)

// Output:
// "Subscriber 2: New Value" (immediately receives the latest value)
```
In this example:
- `BehaviorRelay` starts with an initial value of "Initial Value".
- When "New Value" is emitted, both subscribers receive it.
- If a new subscriber joins later, it will immediately receive the latest value, "New Value".

[Top](#top)

## Why use RxRelay?
- **Ideal for state management**: RxRelay helps you manage state in a way that’s predictable and ensures that you always have access to the latest data without unexpected termination.

- **No termination events**: Unlike `Subject`s, relays don’t emit `.completed` or `.error` events. This is perfect for UI events and state management where completion events aren’t meaningful.

- **Simplifies state sharing**: Because `BehaviorRelay` retains the latest value, it simplifies state sharing across the app by ensuring new subscribers get the most current data.

[Top](#top)

## Practical use cases for RxRelay
- **UI events**: Use `PublishRelay` for UI events like button taps, where you just want to send one-time actions without retaining state.

- **Form inputs**: Use `BehaviorRelay` to manage form input states, where each input should be retained and accessible by other components.

- **App settings or state**: Use `BehaviorRelay` to manage app settings or any state that might be modified and should always be accessible by new subscribers.

[Top](#top)

## Choosing the right publisher/observable
- **Single-value emissions**: Use `just`, `of` or `from`.

- **Custom emission logic**: Use `create` or `deferred`.

- **Time-based emissions**: Use `interval` or `timer`.

- **Subjects**: Use `Subjects` for shared sequences or state that can both emit and receive values.

[Top](#top)

## `Observable.create`
- Allows creating custom observable sequences by providing an observer.

- Use Case: For custom observable creation with specific events or values.

```swift
let observable = Observable<String>.create { observer in
    observer.onNext("Start")
    observer.onCompleted()
    return Disposables.create()
}
```

[Top](#top)

## `Observable.interval`
- Creates an observable that emits sequential numbers over a specified interval.

- Use Case: Timed events, like a countdown or polling.

```swift
let observable = Observable<Int>.interval(.seconds(1), scheduler: MainScheduler.instance)
```

[Top](#top)

## `Observable.timer`
- Creates an observable that emits the initial value after a delay and then emits values periodically.

- Use Case: Similar to `interval` but allows an initial delay before starting.

```swift
let observable = Observable<Int>.timer(.seconds(5), period: .seconds(1), scheduler: MainScheduler.instance)
```

[Top](#top)

## `Observable.deferred`
- Defers creation of an observable sequence until a subscriber subscribes.

- Use Case: Delays observable creation, useful when the state needs to be captured at the time of subscription.

```swift
let observable = Observable.deferred {
    return Observable.just("Generated on subscription")
}
```

[Top](#top)

## Transforming operators
- `map`: Transforms each element emitted by an observable sequence by applying a function.
  ```swift
  observable.map { $0 * 2 }
  ```

- `flatMap`: Transforms each item into a new observable sequence and merges the emissions from all observables.
  ```swift
  observable.flatMap { item in
      return someAsyncOperation(item)
  }
  ```

- `flatMapLatest`: Like `flatMap` but only emits items from the most recent observable.
  ```swift
  observable.flatMapLatest { item in
      return someAsyncOperation(item)
  }
  ```

- `scan`: Applies a function over time, accumulating results.
  ```swift
  observable.scan(0) { acc, element in
      acc + element
  }
  ```

[Top](#top)

## Filtering operators
- `filter`: Emits only items that satisfy a condition.
  ```swift
  observable.filter { $0 > 5 }
  ```

- `distinctUntilChanged`: Suppresses consecutive duplicate items.
  ```swift
  observable.distinctUntilChanged()
  ```

- `take`: Takes only the first n items.
  ```swift
  observable.take(3)
  ```

- `skip`: Skips the first n items.
  ```swift
  observable.skip(2)
  ```

- `takeUntil`: Takes items until another observable emits.
  ```swift
  observable.takeUntil(triggerObservable)
  ```

[Top](#top)

## Combining operators
- `merge`: Merges multiple observable sequences into one.
  ```swift
  Observable.merge(observable1, observable2)
  ```

- `concat`: Concatenates observable sequences, emitting elements from one observable after the other completes.
  ```swift
  Observable.concat(observable1, observable2)
  ```

- `combineLatest`: Combines the latest values from two observables into pairs.
  ```swift
  Observable.combineLatest(observable1, observable2) { val1, val2 in
      return "\(val1) \(val2)"
  }
  ```

- `zip`: Combines values from two or more observables by pairing items at the same index.
  ```swift
  Observable.zip(observable1, observable2) { val1, val2 in
      return "\(val1) \(val2)"
  }
  ```

- `withLatestFrom`: Takes the latest value from a secondary observable whenever the primary observable emits.
  ```swift
  primaryObservable.withLatestFrom(secondaryObservable)
  ```

[Top](#top)

## Error handling operators
- `catchError`: Replaces an error with a fallback observable sequence.
  ```swift
  observable.catchError { error in
      return Observable.just("Fallback value")
  }
  ```

- `retry`: Retries the observable sequence on error.
  ```swift
  observable.retry(3)  // retries up to 3 times
  ```

[Top](#top)

## Time-based operators
- `debounce`: Emits an item only after a specified duration has passed without another emission.
  ```swift
  observable.debounce(.milliseconds(300), scheduler: MainScheduler.instance)
  ```

- `throttle`: Emits the first item and then suppresses subsequent items until a specified duration has passed.
  ```swift
  observable.throttle(.seconds(1), scheduler: MainScheduler.instance)
  ```

- `delay`: Delays the emission of items.
  ```swift
  observable.delay(.seconds(2), scheduler: MainScheduler.instance)
  ```

- `interval`: Emits a sequence of integers at specified intervals.
  ```swift
  Observable<Int>.interval(.seconds(1), scheduler: MainScheduler.instance)
  ```

[Top](#top)

## Utility operators
- `do`: Allows executing side-effects (logging, debugging) without modifying the observable sequence.
  ```swift
  observable.do(onNext: { print("Element: \($0)") })
  ```

- `observeOn`: Specifies the scheduler where the observer observes the emitted items.
  ```swift
  observable.observeOn(MainScheduler.instance)
  ```

- `subscribeOn`: Specifies the scheduler where the observable subscription occurs.
  ```swift
  observable.subscribeOn(ConcurrentDispatchQueueScheduler(qos: .background))
  ```

- `timeout`: Emits an error if an item is not emitted within a specified time frame.
  ```swift
  observable.timeout(.seconds(3), scheduler: MainScheduler.instance)
  ```

[Top](#top)

## Conditional and boolean operators
- `takeWhile`: Takes items while a condition is true.
  ```swift
  observable.takeWhile { $0 < 5 }
  ```

- `skipWhile`: Skips items while a condition is true.
  ```swift
  observable.skipWhile { $0 < 3 }
  ```

- `all`: Checks if all items emitted by an observable sequence satisfy a condition.
  ```swift
  observable.all { $0 > 0 }
  ```

[Top](#top)
