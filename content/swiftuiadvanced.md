# Swift UI Advanced
Advanced topics and how-to's

* [Advanced `NavigationStack` usage example](#Advanced-NavigationStack-usage-example)
* [Specifying the view hierarchy of an app using a scene](#Specifying-the-view-hierarchy-of-an-app-using-a-scene)
* [Example of defining a view hierarchy using a Scene](#Example-of-defining-a-view-hierarchy-using-a-Scene)
* [Multi-scene apps](#Multi-scene-apps)
* [Maintaining the adaptable sizes of built-in views](#Maintaining-the-adaptable-sizes-of-built-in-views)
* [Automatic sizing of views](#Automatic-sizing-of-views)
* [View modifiers for sizing](#View-modifiers-for-sizing)
* [`GeometryReader`](#GeometryReader)
* [Using flexible views](#Using-flexible-views)
* [What is `LayoutPriority`?](#What-is-LayoutPriority)
* [`AspectRatio` and `ScaledToFit/Fill`](#AspectRatio-and-ScaledToFit-Fill)
* [Dynamic type support](#Dynamic-type-support)
* [`Grid` layout](#Grid-layout)
* [Example: Responsive card view](#Example-Responsive-card-view)
* [Scaling views to complement text](#Scaling-views-to-complement-text)
* [Scaling views to complement text: Using `GeometryReader`](#Scaling-views-to-complement-text-Using-GeometryReader)
* [Scaling views to complement text: Using `ScaleEffect`](#Scaling-views-to-complement-text-Using-ScaleEffect)
* [Scaling views to complement text: Using relative sizes](#Scaling-views-to-complement-text-Using-relative-sizes)
* [Scaling views to complement text: Dynamic type with `.scaledToFit()`](#Scaling-views-to-complement-text-Dynamic-type-with-scaledToFit)
* [Scaling views to complement text: Responsive design with `@ScaledMetric`](#Scaling-views-to-complement-text-Responsive-design-with-ScaledMetric)
* [Layering content](#Layering-content)
* [Layering content: Using `ZStack`](#Layering-content-Using-ZStack)
* [Layering content: Using `overlay`](#Layering-content-Using-overlay)
* [Layering content: Using `background`](#Layering-content-Using-background)
* [Layering content: Using `opacity` for layering effects](#Layering-content-Using-opacity-for-layering-effects)
* [Combining `ZStack` with overlays and backgrounds](#Combining-ZStack-with-overlays-and-backgrounds)
* [Layering content: Using `alignmentGuide`](#Layering-content-Using-alignmentGuide)
* [Choosing the right way to hide a view](#Choosing-the-right-way-to-hide-a-view)
* [Choosing the right method to hide a view](#Choosing-the-right-method-to-hide-a-view)
* [Hiding views: Using `.hidden()` modifier](#Hiding-views-Using-hidden-modifier)
* [Hiding views: Using `opacity()` modifier](#Hiding-views-Using-opacity-modifier)
* [Hiding views: Using conditional view `if` statement](#Hiding-views-Using-conditional-view-if-statement)
* [Hiding views: Using `isHidden` custom modifier](#Hiding-views-Using-isHidden-custom-modifier)
* [Hiding views: Using `opacity` with `allowsHitTesting`](#Hiding-views-Using-opacity-with-allowsHitTesting)
* [Hiding views: Using `mask` modifier](#Hiding-views-Using-mask-modifier)
* [Hiding views: Using `transition` and `animation`](#Hiding-views-Using-transition-and-animation)
* [Advanced `NavigationStack` usage example](#Advanced-NavigationStack-usage-example)
* [Creating a custom input control that binds to a value](#Creating-a-custom-input-control-that-binds-to-a-value)
* [Custom control: Define the input control](#Custom-control-Define-the-input-control)
* [Custom control: Use the custom control in a parent view](#Custom-control-Use-the-custom-control-in-a-parent-view)
* [Custom control: Test the custom input control](#Custom-control-Test-the-custom-input-control)
* [Defining the source of truth using a custom binding](#Defining-the-source-of-truth-using-a-custom-binding)
* [Custom binding: Understand the basics of bindings](#Custom-binding-Understand-the-basics-of-bindings)
* [Custom binding: Create a binding](#Custom-binding-Create-a-binding)
* [Custom binding: Use the custom binding](#Custom-binding-Use-the-custom-binding)
* [Custom binding: More complex use cases](#Custom-binding-More-complex-use-cases)
* [Custom binding: Test the custom binding](#Custom-binding-Test-the-custom-binding)
* [How to make a `List` scroll automatically?](#How-to-make-a-List-scroll-automatically)
* [MVVM in SwiftUI](#MVVM-in-SwiftUI)

## Advanced `NavigationStack` usage example
```
import SwiftUI

struct ContentView: View {
    @State private var path = NavigationPath()

    var body: some View {
        NavigationStack(path: $path) {
            List {
                Button("Go to Detail View") {
                    path.append(DetailView())
                }
                Button("Go to Profile View") {
                    path.append(ProfileView())
                }
            }
            .navigationTitle("Home")
            .toolbar {
                Button("Pop to Root") {
                    path.removeAll()
                }
            }
        }
    }
}

struct DetailView: View, Hashable {
    var body: some View {
        Text("This is the Detail View")
            .navigationTitle("Detail")
    }
}

struct ProfileView: View, Hashable {
    var body: some View {
        Text("This is the Profile View")
            .navigationTitle("Profile")
    }
}
```

## Specifying the view hierarchy of an app using a scene
In SwiftUI, the view hierarchy of an app is specified using a scene, which is an essential part of the app's lifecycle management. The scene defines the root view of your application and how it should be displayed. Starting from iOS 14 and macOS 11, SwiftUI introduced the concept of a scene in the `App` protocol, which is used to manage the content and behavior of your app.

### What is a Scene?
A scene in SwiftUI represents an instance of your app’s user interface and its associated state. Scenes allow your app to support multiple instances of the UI, such as when running on an iPad with multi-window support or macOS. Each scene contains a hierarchy of views that defines what is displayed to the user.

### Specifying the view hierarchy with a Scene
When you create a SwiftUI app, you typically start by defining a struct that conforms to the `App` protocol. Inside this struct, you specify the view hierarchy using one or more scenes. The most common scene type is `WindowGroup`, which represents a group of windows that share the same state and behavior.

## Example of defining a view hierarchy using a Scene
Here’s a simple example of how you might specify the view hierarchy of an app using a scene:

```swift
import SwiftUI

@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}

struct ContentView: View {
    var body: some View {
        NavigationStack {
            List {
                NavigationLink("Go to Detail View", destination: DetailView())
                NavigationLink("Go to Profile View", destination: ProfileView())
            }
            .navigationTitle("Home")
        }
    }
}

struct DetailView: View {
    var body: some View {
        Text("This is the Detail View")
            .navigationTitle("Detail")
    }
}

struct ProfileView: View {
    var body: some View {
        Text("This is the Profile View")
            .navigationTitle("Profile")
    }
}
```
Breakdown of the example
- **@main and MyApp Struct**:
The `@main` attribute indicates the entry point of the app. The `MyApp` struct conforms to the `App` protocol, which is where you define your app's scene and view hierarchy.

- **Scene**:
The `body` property of the `App` protocol returns a scene. In this case, we use a `WindowGroup` scene, which is suitable for apps with multiple windows or instances (like on iPad or macOS).

- **WindowGroup**:
`WindowGroup` is a type of scene that manages a collection of windows or tabs. Each instance of the window or tab will start with the `ContentView`.

- **ContentView**:
The `ContentView` is the root view of the app's UI, containing a navigation stack with links to other views (`DetailView` and `ProfileView`).

- **Other views (`DetailView` and `ProfileView`)**:
These are the destination views that are navigated to from the `ContentView`.

## Multi-scene apps
SwiftUI supports apps with multiple scenes. For example, on macOS, you can define multiple `WindowGroup` or even `DocumentGroup` scenes, allowing for a multi-window experience:

```swift
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup("Main Window") {
            ContentView()
        }
        
        WindowGroup("Secondary Window") {
            SecondaryView()
        }
        
        Settings {
            SettingsView()
        }
    }
}
```
In this example:
- **`WindowGroup`**: Defines multiple window scenes.

- **`Settings`**: Defines a settings window scene.

## Maintaining the adaptable sizes of built-in views
Maintaining adaptable sizes of built-in views in SwiftUI is crucial to creating a responsive and flexible user interface that works well across different screen sizes and device orientations. SwiftUI's layout system is designed to handle this automatically in many cases, but there are specific techniques and principles you can use to ensure your views adapt as intended.

### Key concepts for maintaining sdaptable sizes
- Automatic sizing of views

- Using `Spacer`

- View modifiers for sizing

- `GeometryReader`

- Using flexible views

- `LayoutPriority`

- `AspectRatio` and `ScaledToFit/Fill`

- Dynamic type support

- Grid layout

## Automatic sizing of views
SwiftUI’s built-in views like `Text`, `Image`, `Button`, etc., automatically adapt their sizes based on their content and the available space. This behavior is often sufficient for most interfaces.

## View modifiers for sizing
SwiftUI provides various modifiers that help control the size and layout of views, such as `frame`, `padding`, `fixedSize`, `layoutPriority` and `aspectRatio`.

Example with `frame`:
```swift
Text("Hello, World!")
    .frame(maxWidth: .infinity, maxHeight: .infinity)
```
This example makes the Text view take up all available space.

## `GeometryReader`
`GeometryReader` is a powerful tool for building adaptable layouts. It provides the size and position of the container view, allowing you to adjust your views dynamically.

Example:
```swift
GeometryReader { geometry in
    VStack {
        Text("Width: \(geometry.size.width)")
        Text("Height: \(geometry.size.height)")
    }
}
```

## Using flexible views
Views like `HStack`, `VStack`, and `ZStack` automatically adjust their layout based on their contents and available space, making them essential for adaptive layouts.

Example:
```swift
VStack {
    HStack {
        Text("Leading")
        Spacer()
        Text("Trailing")
    }
    .padding()
}
```

## What is `LayoutPriority`?
`layoutPriority` helps determine how much space a view should prioritize relative to others when space is constrained.

Example:
```swift
HStack {
    Text("Short Text")
        .layoutPriority(1)
    Text("This is a much longer piece of text that may need more space.")
}
```

## `AspectRatio` and `ScaledToFit/Fill`
`aspectRatio` maintains the aspect ratio of views like Image.
`scaledToFit` and `scaledToFill` adjust an image’s size while maintaining its aspect ratio within the available space.

Example:
```swift
Image("example")
    .resizable()
    .scaledToFit()
```

## Dynamic type support
Ensure text scales with the user’s preferred font size by using `Text` styles that support dynamic type, like `.title`, `.body`, etc.

Example:
```swift
Text("Hello, World!")
    .font(.body)
    .padding()
```

## `Grid` layout
Introduced in SwiftUI, `Grid` allows for more flexible and responsive layouts similar to CSS grids.

Example:
```swift
Grid {
    GridRow {
        Text("Name")
        Text("Age")
    }
    GridRow {
        Text("Alice")
        Text("25")
    }
}
```

## Example: Responsive card view
Here’s a practical example of how to create a card view that adapts to different screen sizes:

```swift
import SwiftUI

struct CardView: View {
    var body: some View {
        VStack(alignment: .leading) {
            Image("example")
                .resizable()
                .scaledToFit()
                .cornerRadius(10)
            
            Text("Title of the Card")
                .font(.headline)
                .padding(.top, 10)
            
            Text("Description of the card that may be longer or shorter depending on the content. The view adapts to this content.")
                .font(.subheadline)
                .padding(.top, 5)
            
            Spacer()
        }
        .padding()
        .background(Color.white)
        .cornerRadius(15)
        .shadow(radius: 5)
        .frame(maxWidth: 300)  // Max width constraint
    }
}

struct ContentView: View {
    var body: some View {
        ScrollView {
            VStack {
                CardView()
                    .padding()
                CardView()
                    .padding()
                CardView()
                    .padding()
            }
            .padding()
        }
        .background(Color(UIColor.systemGray6))
    }
}
```
### Key adaptability techniques in the example
- **Resizing images**: The image is resized and scaled to fit within the available space using `resizable` and `scaledToFit`.

- **Flexible text**: The text content adjusts naturally to the available width, thanks to SwiftUI’s built-in text handling.

- **Spacing**: `Spacer` and `padding` ensure there’s consistent spacing and adaptability within the view.

- **Responsive frame**: The `.frame(maxWidth: 300)` keeps the card's width constrained, but still allows it to be responsive.

## Scaling views to complement text
In SwiftUI, scaling views to complement text can be achieved by dynamically adjusting the size of views based on the text's size or by ensuring that the views adapt to different text sizes. This is particularly useful when you want to create a responsive design that maintains a consistent visual hierarchy, regardless of the content.

### Techniques for scaling views to complement Text
- Using `GeometryReader`
- Using `scaleEffect`
- Using relative sizes
- Dynamic type with `.scaledToFit()`
- Responsive design with `@ScaledMetric`

## Scaling views to complement text: Using `GeometryReader`
- You can use `GeometryReader` to get the size of the parent view and scale your views or text accordingly.

- This approach allows you to make the size of your views relative to the available space.

```swift
struct ScaledTextWithView: View {
    var body: some View {
        GeometryReader { geometry in
            VStack {
                Text("Hello, SwiftUI!")
                    .font(.system(size: geometry.size.width * 0.1))
                Spacer()
                Circle()
                    .frame(width: geometry.size.width * 0.3, height: geometry.size.width * 0.3)
            }
            .frame(width: geometry.size.width, height: geometry.size.height)
        }
    }
}
```
In this example, the text size is scaled based on the width of the `GeometryReader`, and the circle is also scaled relative to the width.

## Scaling views to complement text: Using `ScaleEffect`
You can use the `.scaleEffect()` modifier to proportionally scale a view relative to the text or another reference size.

```swift
struct ScaleEffectExample: View {
    var body: some View {
        VStack {
            Text("SwiftUI")
                .font(.largeTitle)
                .padding()
            
            Rectangle()
                .fill(Color.blue)
                .frame(width: 100, height: 100)
                .scaleEffect(1.5)
        }
    }
}
```
This example scales the rectangle by 1.5 times its original size, making it complement the text size.

## Scaling views to complement text: Using relative sizes
Another approach is to define relative sizes using `.frame(width:height:)` based on the size of the text.

```swift
struct RelativeSizeExample: View {
    var body: some View {
        VStack {
            Text("SwiftUI")
                .font(.largeTitle)
                .padding()
            
            Circle()
                .frame(width: 50, height: 50)
                .overlay(Text("Icon").foregroundColor(.white))
                .padding()
        }
        .frame(maxWidth: .infinity, maxHeight: .infinity)
    }
}
```
Here, the circle is defined with a fixed size, but you can adjust its size to be relative to the text size.

## Scaling views to complement text: Dynamic type with `.scaledToFit()`
If you're using images or other views that need to scale with text, you can use `.scaledToFit()` or `.scaledToFill()` to ensure they adapt to the available space.

```swift
struct DynamicTypeExample: View {
    var body: some View {
        VStack {
            Text("SwiftUI Scaling")
                .font(.largeTitle)
                .padding()
            
            Image(systemName: "star.fill")
                .resizable()
                .scaledToFit()
                .frame(width: 100, height: 100)
                .foregroundColor(.yellow)
        }
        .padding()
    }
}
```
This ensures the image scales proportionally within its frame, complementing the text size.

## Scaling views to complement text: Responsive design with `@ScaledMetric`
SwiftUI also provides `@ScaledMetric` which allows you to scale certain dimensions relative to the user's preferred text size.

```swift
struct ScaledMetricExample: View {
    @ScaledMetric var iconSize: CGFloat = 50

    var body: some View {
        HStack {
            Image(systemName: "star.fill")
                .resizable()
                .frame(width: iconSize, height: iconSize)
                .foregroundColor(.yellow)

            Text("Important")
                .font(.headline)
        }
    }
}
```
In this example, `iconSize` scales automatically based on the user’s text size preferences, ensuring consistency with the text.

## Layering content
In SwiftUI, layering content involves placing views on top of each other to create complex layouts, effects, or visual hierarchies. This can be achieved using a few different techniques such as using `ZStack`, overlays, backgrounds, and opacity modifiers. Below are some common methods for layering content in SwiftUI.

- Using `ZStack`
- Using `overlay`
- Using `background`
- Using `opacity` for layering effects
- Combining `ZStack` with overlays and backgrounds
- Using `alignmentGuide`

## Layering content: Using `ZStack`
`ZStack` is the primary container for layering views. Views added to a `ZStack` are stacked on top of each other along the z-axis (depth), with the first view at the back and subsequent views layered on top.

```swift
struct ZStackExample: View {
    var body: some View {
        ZStack {
            // Background layer
            Color.blue
                .edgesIgnoringSafeArea(.all)
            
            // Middle layer
            Circle()
                .fill(Color.yellow)
                .frame(width: 200, height: 200)
            
            // Top layer
            Text("Hello, SwiftUI!")
                .font(.largeTitle)
                .foregroundColor(.white)
        }
    }
}
```
In this example, the blue background fills the entire screen, the yellow circle is layered on top of the background, and the text is placed on top of the circle.

## Layering content: Using `overlay`
The `overlay` modifier allows you to place a view on top of another view. This is particularly useful for adding additional content like labels, icons, or custom shapes on top of existing views.

Example:
```swift
struct OverlayExample: View {
    var body: some View {
        Rectangle()
            .fill(Color.green)
            .frame(width: 200, height: 200)
            .overlay(
                Text("Overlay")
                    .font(.title)
                    .foregroundColor(.white)
            )
    }
}
```
Here, the `Text` view is placed on top of the green rectangle using the `overlay` modifier.

## Layering content: Using `background`
The `background` modifier places content behind a view. This can be combined with the `overlay` modifier to create more complex layering effects.

Example:
```swift
struct BackgroundExample: View {
    var body: some View {
        Text("SwiftUI")
            .font(.largeTitle)
            .foregroundColor(.white)
            .padding()
            .background(
                Circle()
                    .fill(Color.blue)
                    .frame(width: 150, height: 150)
            )
    }
}
```
In this example, the circle is placed behind the text using the `background` modifier, creating a layered effect where the text is centered on the circle.

## Layering content: Using `opacity` for layering effects
You can use the `opacity` modifier to create subtle layering effects where one view slightly shows through another.

Example:
```swift
struct OpacityExample: View {
    var body: some View {
        ZStack {
            Image(systemName: "star.fill")
                .resizable()
                .scaledToFit()
                .frame(width: 100, height: 100)
                .foregroundColor(.yellow)
                .opacity(0.5)

            Text("SwiftUI")
                .font(.largeTitle)
                .foregroundColor(.white)
        }
    }
}
```
The star icon is semi-transparent, allowing the text to be visible through it, creating a layered visual effect.

## Combining `ZStack` with overlays and backgrounds
You can combine `ZStack` with the `overlay` and `background` modifiers to achieve even more complex layering.

```swift
struct ComplexLayeringExample: View {
    var body: some View {
        ZStack {
            // Background color
            Color.black.edgesIgnoringSafeArea(.all)
            
            // Main content
            Circle()
                .fill(Color.red)
                .frame(width: 200, height: 200)
                .overlay(
                    Circle()
                        .stroke(Color.white, lineWidth: 5)
                        .padding(10)
                )
                .background(
                    Circle()
                        .fill(Color.blue)
                        .frame(width: 220, height: 220)
                )
            
            // Top text layer
            Text("SwiftUI")
                .font(.largeTitle)
                .foregroundColor(.white)
                .bold()
        }
    }
}
```
In this example:
- The `ZStack` layers a red circle, with a white stroke overlay and a blue background circle.
- The text "SwiftUI" is layered on top, creating a complex visual hierarchy.

## Layering content: Using `alignmentGuide`
You can also align layers in a specific way using `alignmentGuide` to control how elements are stacked in a `ZStack`.

Example:
```swift
struct AlignmentGuideExample: View {
    var body: some View {
        ZStack(alignment: .bottomTrailing) {
            Rectangle()
                .fill(Color.orange)
                .frame(width: 150, height: 150)
            
            Text("SwiftUI")
                .font(.title)
                .foregroundColor(.white)
                .alignmentGuide(.bottom) { _ in 10 }
                .alignmentGuide(.trailing) { _ in 10 }
        }
    }
}
```
This example aligns the text to the bottom-right corner of the orange rectangle using `alignmentGuide`.

## Choosing the right way to hide a view
Choosing the right way to hide a view in SwiftUI depends on the context and behavior you want to achieve. SwiftUI offers multiple methods to hide or conditionally display views, each with different implications for layout, performance, and user experience. Here's a guide on how to choose the right method for hiding a view:
- Using `.hidden()` modifier
- Using `opacity()` modifier
- Using conditional view (`if` statement)
- Using `isHidden` custom modifier
- Using `opacity` with `allowsHitTesting`
- Using `mask` Modifier
- Using `transition` and `animation`

## Choosing the right method to hide a view
- **Maintain layout**: Use `.hidden()` if you need to hide the view but keep its space in the layout.

- **Remove from layout**: Use conditional views (`if`) if you want the view to be completely removed from the layout when hidden.

- **Interactive but invisible**: Use `opacity(0)` if the view should remain interactive while being invisible.

- **Complex animations**: Use `transition` with `animation` for animated show/hide effects.

- **Reusable modifier**: Create a custom modifier for repeated use across your views.

By carefully choosing the right method for hiding views, you can achieve the desired behavior in your SwiftUI app while maintaining a clean and efficient codebase.

## Hiding views: Using `.hidden()` modifier
The `.hidden()` modifier hides the view visually but keeps the space it occupies in the layout. This means the view is still there, but it’s invisible.

Use case:
- When you want to hide a view but maintain the layout structure and spacing around it.

Example:
```swift
struct HiddenModifierExample: View {
    @State private var isHidden = false

    var body: some View {
        VStack {
            Text("This is always visible")
            
            Text("This text might be hidden")
                .hidden(isHidden)

            Button("Toggle Visibility") {
                isHidden.toggle()
            }
        }
    }
}
```

## Hiding views: Using `opacity()` modifier
The `opacity(0)` modifier makes the view completely transparent but still interactive and occupying space.

Use case:
- When you want to make a view invisible but still want it to respond to user interactions like taps.

Example:
```swift
struct OpacityModifierExample: View {
    @State private var isHidden = false

    var body: some View {
        VStack {
            Text("This is always visible")

            Text("This text might be hidden")
                .opacity(isHidden ? 0 : 1)

            Button("Toggle Visibility") {
                isHidden.toggle()
            }
        }
    }
}
```

## Hiding views: Using conditional view `if` statement
Using an `if` statement to conditionally add or remove a view from the view hierarchy. When the condition is false, the view is completely removed from the layout, and the space it occupied is reclaimed.

Use case:
- When you want to hide a view and remove it from the layout completely.

Example:
```swift
struct ConditionalViewExample: View {
    @State private var showText = true

    var body: some View {
        VStack {
            Text("This is always visible")

            if showText {
                Text("This text might be hidden")
            }

            Button("Toggle Visibility") {
                showText.toggle()
            }
        }
    }
}
```

## Hiding views: Using `isHidden` custom modifier
You can create a custom modifier that toggles between showing and hiding a view by conditionally applying the `.hidden()` modifier or by entirely removing the view.

Use case:
- When you want a more reusable and flexible solution that you can apply to different views.

Example:
```swift
extension View {
    func isHidden(_ hidden: Bool) -> some View {
        hidden ? AnyView(self.hidden()) : AnyView(self)
    }
}

struct IsHiddenModifierExample: View {
    @State private var isHidden = false

    var body: some View {
        VStack {
            Text("This is always visible")

            Text("This text might be hidden")
                .isHidden(isHidden)

            Button("Toggle Visibility") {
                isHidden.toggle()
            }
        }
    }
}
```

## Hiding views: Using `opacity` with `allowsHitTesting`
If you want a view to be invisible and non-interactive, you can combine `opacity` with `allowsHitTesting(false)`.

Use case:
- When you want to hide a view and also make sure it doesn’t respond to user interactions.

Example:
```swift
struct OpacityHitTestingExample: View {
    @State private var isHidden = false

    var body: some View {
        VStack {
            Text("This is always visible")

            Text("This text might be hidden")
                .opacity(isHidden ? 0 : 1)
                .allowsHitTesting(!isHidden)

            Button("Toggle Visibility") {
                isHidden.toggle()
            }
        }
    }
}
```

## Hiding views: Using `mask` modifier
The `mask` modifier allows you to hide a view by applying a mask that completely covers the view. This effectively hides the view but doesn’t remove it from the layout.

Use case:
- When you need more complex hiding behavior, like applying a mask that can have non-uniform shapes.

Example:
```swift
struct MaskModifierExample: View {
    @State private var isHidden = false

    var body: some View {
        VStack {
            Text("This is always visible")

            Text("This text might be hidden")
                .mask(isHidden ? Rectangle().size(CGSize(width: 0, height: 0)) : Rectangle())

            Button("Toggle Visibility") {
                isHidden.toggle()
            }
        }
    }
}
```

## Hiding views: Using `transition` and `animation`
For more sophisticated behavior, such as fading or sliding a view in and out of visibility, you can use `transition` with `animation`.

Use case:
- When you want to animate the appearance or disappearance of a view.

Example:
```swift
struct TransitionAnimationExample: View {
    @State private var showText = true

    var body: some View {
        VStack {
            Text("This is always visible")

            if showText {
                Text("This text might be hidden")
                    .transition(.slide)
                    .animation(.easeInOut, value: showText)
            }

            Button("Toggle Visibility") {
                withAnimation {
                    showText.toggle()
                }
            }
        }
    }
}
```

## Advanced `NavigationStack` usage example
```
import SwiftUI

struct ContentView: View {
    @State private var path = NavigationPath()

    var body: some View {
        NavigationStack(path: $path) {
            List {
                Button("Go to Detail View") {
                    path.append(DetailView())
                }
                Button("Go to Profile View") {
                    path.append(ProfileView())
                }
            }
            .navigationTitle("Home")
            .toolbar {
                Button("Pop to Root") {
                    path.removeAll()
                }
            }
        }
    }
}

struct DetailView: View, Hashable {
    var body: some View {
        Text("This is the Detail View")
            .navigationTitle("Detail")
    }
}

struct ProfileView: View, Hashable {
    var body: some View {
        Text("This is the Profile View")
            .navigationTitle("Profile")
    }
}
```

## Creating a custom input control that binds to a value
Creating a custom input control that binds to a value involves defining a custom view that accepts a `@Binding` to a state variable. This allows the custom input control to interact with and update the bound value, reflecting changes in the parent view. Here's a step-by-step guide to achieving this:

**Step 1: Define the custom input control**

**Step 2: Use the custom input control in a parent view**

**Step 3: Test the custom input control**

This approach allows you to create reusable, custom input controls that can bind to external state variables. The key is to use the `@Binding` property wrapper in the custom view, which provides a powerful way to create components that interact seamlessly with their parent views. This pattern is highly flexible and can be adapted to various types of custom controls, making your SwiftUI code more modular and maintainable.

## Custom control: Define the input control
Let's say we want to create a custom input control that allows the user to input a numerical value using a slider and a text field. The custom view will bind to an integer value so that it can update and reflect changes.

```swift
import SwiftUI

struct CustomNumberInput: View {
    // Binding to an external integer value
    @Binding var value: Int
    
    var range: ClosedRange<Int> // Define the range for the slider
    
    var body: some View {
        VStack {
            Slider(value: Binding(
                get: { Double(self.value) },
                set: { self.value = Int($0) }
            ), in: Double(range.lowerBound)...Double(range.upperBound))
            .padding()
            
            TextField("Enter number", value: $value, formatter: NumberFormatter())
                .textFieldStyle(RoundedBorderTextFieldStyle())
                .padding()
        }
    }
}
```
Explanation:
- **`@Binding var value: Int`**: This binds the `value` property to an external state, allowing two-way data flow. The parent view can provide a state variable that this custom input control can modify.

- **`Slider`**: The slider is used to modify the value within a specified range. We convert the `Int` value to `Double` for the slider and back to `Int` for the binding.

- **`TextField`**: The text field allows direct numerical input. The `value` is passed as a binding to the `TextField` and the `NumberFormatter` ensures the input is treated as an integer.

## Custom control: Use the custom control in a parent view
Now, let's use this custom input control in a parent view. We'll create a state variable in the parent view that the custom control will bind to.

```swift
struct ContentView: View {
    @State private var number: Int = 50
    
    var body: some View {
        VStack {
            Text("Selected Number: \(number)")
                .font(.largeTitle)
            
            CustomNumberInput(value: $number, range: 0...100)
                .padding()
            
            Spacer()
        }
        .padding()
    }
}
```
Explanation:
- **`@State private var number: Int`**: This state variable holds the integer value that the custom input control will modify.

- **`CustomNumberInput(value: $number, range: 0...100)`**: The `number` state is passed as a binding to the custom input control, allowing it to update the `number` state.

## Custom control: Test the custom input control
When you run the `ContentView`, the UI will display the `CustomNumberInput` control. You can interact with the slider and text field, and the value will update dynamically in both the custom input control and the text label in the parent view.

## Defining the source of truth using a custom binding
In SwiftUI, a source of truth is a single, authoritative state that determines the UI's behavior and appearance. When working with custom bindings, you often need to define a source of truth in a way that can drive multiple parts of your UI while ensuring that the state is consistent.

A custom binding allows you to control how a state is read and written, which is useful when you want to apply additional logic when the value changes, or when you want to derive a value from another source. Let’s go through the steps of defining the source of truth using a custom binding.

- **Step 1: Understand the basics of bindings**

- **Step 2: Create a custom binding**

- **Step 3: Use the custom binding**

- **Step 4: More complex use cases**

- **Step 5: Test the custom binding**

## Custom binding: Understand the basics of bindings
Before creating a custom binding, it's important to understand that a binding is simply a way of connecting a view to its underlying data model. A binding allows a view to read and write a value, keeping the UI and the data in sync.

## Custom binding: Create a binding
To create a custom binding, you can use SwiftUI’s Binding type. The Binding initializer takes two closures: one for getting the value and one for setting the value. Here's a basic example:

```swift
import SwiftUI

struct CustomBindingView: View {
    @State private var isOn: Bool = false // Source of truth
    
    var body: some View {
        VStack {
            Toggle("Switch", isOn: Binding(
                get: {
                    self.isOn // Get the current state
                },
                set: { newValue in
                    self.isOn = newValue // Set the new state
                    print("Switch is now \(self.isOn ? "On" : "Off")")
                }
            ))
            .padding()
            
            // Additional UI elements can use the same source of truth
            if isOn {
                Text("The switch is ON!")
            } else {
                Text("The switch is OFF!")
            }
        }
    }
}
```
Explanation:
- **`@State private var isOn: Bool = false`**: This is the source of truth for whether the switch is on or off.

- **Custom binding for `Toggle`**: We create a custom binding by using the `Binding` initializer, where:
  - **`get`**: returns the current value of `isOn`.
  - **`set`**: updates the `isOn` value with the new value and includes additional logic (like printing a message).

## Custom binding: Use the custom binding
In the example above, the custom binding is used with a `Toggle` control. The toggle reads the current value of `isOn` and updates it when the user interacts with the control. The custom logic in the `set` closure runs every time the value changes.

## Custom binding: More complex use cases
You might want to create a custom binding that manipulates the state or derives its value from another property. For example, if you have a temperature input in Celsius and you want to display it in Fahrenheit:

```swift
struct TemperatureView: View {
    @State private var celsius: Double = 0.0 // Source of truth
    
    var body: some View {
        VStack {
            Slider(value: Binding(
                get: {
                    self.celsius // Celsius is the source of truth
                },
                set: { newValue in
                    self.celsius = newValue
                }
            ), in: -50...50)
            
            TextField("Enter Fahrenheit", value: Binding(
                get: {
                    self.celsius * 9/5 + 32 // Convert Celsius to Fahrenheit
                },
                set: { newValue in
                    self.celsius = (newValue - 32) * 5/9 // Convert Fahrenheit to Celsius
                }
            ), formatter: NumberFormatter())
            .textFieldStyle(RoundedBorderTextFieldStyle())
            .padding()
        }
    }
}
```
Explanation:
- **Temperature conversion**: Here, the source of truth is the temperature in Celsius. The custom binding converts the Celsius value to Fahrenheit for display in the `TextField` and converts back from Fahrenheit when the user inputs a value.

## Custom binding: Test the custom binding
When you run the `TemperatureView`, you can move the slider to change the temperature in Celsius, and the value in Fahrenheit will update accordingly. Similarly, typing a new value in Fahrenheit will update the slider and the Celsius state.

## How to make a `List` scroll automatically?
Example solution:
```swift
ScrollViewReader { scrollView in
    ScrollView(.vertical) {
        LazyVStack {
            ForEach(notes, id: \.self) { note in
                MessageView(note: note)
            }
        }
        .onAppear {
            scrollView.scrollTo(notes[notes.endIndex - 1])
        }
    }
}
```

## MVVM in SwiftUI
SwiftUI naturally supports the MVVM pattern through its use of data binding and the `@ObservedObject`, `@State` and `@Published` property wrappers.

Example in SwiftUI:
```swift
struct ContentView: View {
    @ObservedObject var viewModel = UserViewModel(userService: UserService())

    var body: some View {
        VStack {
            Text(viewModel.userName)
            Button(action: {
                viewModel.loadUserData()
            }) {
                Text("Load User Data")
            }
        }
    }
}
```
Here, `ContentView` is the `View`, `UserViewModel` is the `ViewModel` and `UserService` handles the `Model` logic.
