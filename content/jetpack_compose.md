# Jetpack Compose
Basics

* [What is Jetpack Compose?](#What-is-Jetpack-Compose)
* [What is `@Composable`?](#What-is-Composable)
* [Calling composable functions](#Calling-composable-functions)
* [A `@Composable` function in a basic app](#A-Composable-function-in-a-basic-app)
* [Modifiers: Chaining](#Modifiers-Chaining)
* [Modifiers: Layout control](#Modifiers-Layout-control)
* [Modifiers: Appearance customization](#Modifiers-Appearance-customization)
* [Modifiers: Interaction handling](#Modifiers-Interaction-handling)
* [Modifiers: Alignment and arrangement](#Modifiers-Alignment-and-arrangement)
* [Modifiers: State-based modifications](#Modifiers-State-based-modifications)
* [Common modifiers](#Common-modifiers)

## What is Jetpack Compose?
Jetpack Compose is a modern toolkit for building native Android user interfaces (UIs) using a declarative programming approach. Developed by Google, it simplifies UI development by allowing developers to describe the UI in code, which then updates automatically in response to changes in the application state.

### Key features of Jetpack Compose:
1. **Declarative UI**: Instead of using XML layouts, developers define the UI in Kotlin code. This approach lets you declare "what" the UI should look like for a given state, and Compose handles the "how" part of rendering it efficiently.

2. **State management**: UI components automatically update when the underlying data (state) changes, reducing the need for manual UI updates. This is facilitated by Compose's built-in support for reactive programming patterns.

3. **Integration with Android Framework**: Jetpack Compose integrates seamlessly with existing Android views and other Jetpack libraries, so developers can mix Compose and traditional XML-based views if needed.

4. **Reusable components**: Compose encourages building small, reusable UI components called "composables," which can be composed together to create complex interfaces.

5. **Performance**: Compose is designed to optimize UI rendering performance. It only updates parts of the UI that need to change, which helps reduce overhead and improve responsiveness.

6. **Tooling support**: Jetpack Compose has great support in Android Studio, with live previews, interactive editing, and advanced debugging tools.

### Benefits:
- **Less boilerplate**: Compose requires less code compared to traditional XML-based Android UI, reducing development time and effort.

- **Kotlin-based**: Since Compose is built using Kotlin, it leverages Kotlin's features like lambdas, extensions, and null-safety.

- **Composable UIs**: With composables, it's easy to break down UIs into modular, reusable components.

## What is `@Composable`?
The `@Composable` annotation is used to mark a function as composable, meaning it is part of the declarative UI system provided by Jetpack Compose. Functions annotated with `@Composable` can define and build the UI elements in a Compose application.

The @Composable annotation allows you to create UIs in a declarative manner. Rather than manually updating the UI when data changes, you define what the UI should look like based on the current state, and Compose handles updating the UI automatically.
```kotlin
@Composable
fun Greeting(name: String) {
    Text(text = "Hello, $name!")
}
```
In this example, Greeting is a composable function that creates a Text element, displaying a greeting message.

## Calling composable functions
A composable function can only be called from another composable function. This means you can't call a `@Composable` function from a normal Kotlin function, but inside a composable, you can call other composables.
```kotlin
@Composable
fun MyScreen() {
    Column {
        Greeting(name = "Alice")
        Greeting(name = "Bob")
    }
}
```

## A `@Composable` function in a basic app
Here’s how you’d use a `@Composable` function in a basic app:

```kotlin
@Composable
fun Greeting(name: String) {
    Text(text = "Hello, $name!")
}

@Composable
fun MyApp() {
    Column {
        Greeting(name = "Android")
        Greeting(name = "Compose")
    }
}

@Preview
@Composable
fun PreviewMyApp() {
    MyApp()
}
```
In this example:
- `Greeting` is a simple composable that displays text.
- `MyApp` composes two `Greeting` composables.
- The `@Preview` annotation allows you to preview the UI in Android Studio.

## Modifiers: Chaining
Modifiers can be combined or "chained" together to apply multiple modifications to a single composable element. The order in which modifiers are applied matters because it determines how each modification is interpreted.
```kotlin
@Composable
fun MyText() {
    Text(
        text = "Hello, Compose!",
        modifier = Modifier
            .padding(16.dp)
            .background(Color.Yellow)
            .size(200.dp)
    )
}
```
In this example:
- The `Text` composable is first padded with 16dp of space.
- It is then given a yellow background.
- Lastly, the size is set to 200dp.

## Modifiers: Layout control
Modifiers can control how a composable is laid out within its parent, such as specifying width, height, padding, margins, or alignment.

```kotlin
@Composable
fun LayoutExample() {
    Box(
        modifier = Modifier
            .size(100.dp)
            .padding(8.dp)
    ) {
        Text(text = "Box with padding")
    }
}
```
Here, the `Box` will have a size of 100dp and will be padded by 8dp from its edges.

## Modifiers: Appearance customization
Modifiers can change the visual appearance of a composable, such as setting the background color, borders, or elevation (for shadows).

```kotlin
@Composable
fun StyledText() {
    Text(
        text = "Styled Text",
        modifier = Modifier
            .background(Color.Cyan)
            .border(2.dp, Color.Black)
            .padding(10.dp)
    )
}
```

## Modifiers: Interaction handling
You can use modifiers to add click listeners, gestures, or other interactions to a composable.

```kotlin
@Composable
fun ClickableText() {
    Text(
        text = "Click me",
        modifier = Modifier
            .clickable { /* Handle click */ }
            .padding(16.dp)
    )
}
```

## Modifiers: Alignment and arrangement
Modifiers are useful for aligning composables within layouts, like aligning items within rows or columns.

```kotlin
@Composable
fun AlignedRow() {
    Row(
        modifier = Modifier.fillMaxWidth(),
        horizontalArrangement = Arrangement.Center
    ) {
        Text(text = "Centered Text")
    }
}
```

## Modifiers: State-based modifications
You can conditionally apply modifiers based on certain states, for example, changing the background color when a button is clicked or hovered.
```kotlin
@Composable
fun ColorChangingBox(isClicked: Boolean) {
    Box(
        modifier = Modifier
            .size(100.dp)
            .background(if (isClicked) Color.Green else Color.Red)
    )
}
```

## Common modifiers
- `padding()` Adds padding around a composable.
```kotlin
Modifier.padding(16.dp)
```

- `size()` Sets the width and height of a composable.
```kotlin
Modifier.size(100.dp)
```

- `fillMaxWidth() / fillMaxHeight()` Makes a composable fill the available width or height.
```kotlin
Modifier.fillMaxWidth()
```

- `background()` Sets a background color or drawable for a composable.
```kotlin
Modifier.background(Color.Blue)
```

- `border()` Adds a border around a composable.
```kotlin
Modifier.border(2.dp, Color.Black)
```

- `clickable()` Adds click functionality to a composable.
```kotlin
Modifier.clickable { /* onClick action */ }
```

- `align()` Aligns a composable within its parent.
```kotlin
Modifier.align(Alignment.Center)
```
