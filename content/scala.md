# Scala Essential
Essential Scala programming concepts

* [What is Scala?](#What-is-Scala)
* [Write a simple Scala program that prints 'Hello, world!'](#Write-a-simple-Scala-program-that-prints-Hello-world)
* [What is the difference between 'val' and 'var' in Scala?](#What-is-the-difference-between-val-and-var-in-Scala)
* [How do you define a function in Scala that adds two integers?](#How-do-you-define-a-function-in-Scala-that-adds-two-integers)
* [What is a case class in Scala?](#What-is-a-case-class-in-Scala)
* [How do you create a list of integers from 1 to 5 in Scala?](#How-do-you-create-a-list-of-integers-from-1-to-5-in-Scala)
* [What is pattern matching in Scala?](#What-is-pattern-matching-in-Scala)
* [How do you double every element in a list using map in Scala?](#How-do-you-double-every-element-in-a-list-using-map-in-Scala)
* [What is a trait in Scala?](#What-is-a-trait-in-Scala)
* [How do you define a class Dog that extends class Animal in Scala?](#How-do-you-define-a-class-Dog-that-extends-class-Animal-in-Scala)
* [What is Option in Scala?](#What-is-Option-in-Scala)
* [What is the difference between Some and None in Scala?](#What-is-the-difference-between-Some-and-None-in-Scala)
* [How do you specify a type annotation in Scala?](#How-do-you-specify-a-type-annotation-in-Scala)
* [How do you write a for loop from 1 to 5 in Scala?](#How-do-you-write-a-for-loop-from-1-to-5-in-Scala)
* [What is a companion object in Scala?](#What-is-a-companion-object-in-Scala)
* [How do you define a singleton object in Scala with a method square?](#How-do-you-define-a-singleton-object-in-Scala-with-a-method-square)
* [What programming paradigms does Scala support?](#What-programming-paradigms-does-Scala-support)
* [How do you create a tuple with an Int, String, and Boolean in Scala?](#How-do-you-create-a-tuple-with-an-Int-String-and-Boolean-in-Scala)
* [What is a sealed trait in Scala?](#What-is-a-sealed-trait-in-Scala)
* [How do you create a Map from String to Int in Scala?](#How-do-you-create-a-Map-from-String-to-Int-in-Scala)
* [What is a higher-order function in Scala?](#What-is-a-higher-order-function-in-Scala)
* [How do you define a curried function in Scala?](#How-do-you-define-a-curried-function-in-Scala)
* [How do you filter even numbers from a list in Scala?](#How-do-you-filter-even-numbers-from-a-list-in-Scala)
* [What are common uses for companion objects in Scala?](#What-are-common-uses-for-companion-objects-in-Scala)
* [How do you define a function with a default parameter in Scala?](#How-do-you-define-a-function-with-a-default-parameter-in-Scala)
* [What is a by-name parameter in Scala?](#What-is-a-by-name-parameter-in-Scala)
* [How do you get the length of a string in Scala?](#How-do-you-get-the-length-of-a-string-in-Scala)
* [What can a trait contain in Scala?](#What-can-a-trait-contain-in-Scala)
* [How do you create a Set of integers in Scala?](#How-do-you-create-a-Set-of-integers-in-Scala)
* [What is a function literal in Scala?](#What-is-a-function-literal-in-Scala)
* [How do you write an if-else statement in Scala?](#How-do-you-write-an-if-else-statement-in-Scala)
* [How does Scala support multiple inheritance?](#How-does-Scala-support-multiple-inheritance)
* [How do you create an array of integers in Scala?](#How-do-you-create-an-array-of-integers-in-Scala)
* [What is a for-comprehension in Scala?](#What-is-a-for-comprehension-in-Scala)
* [How do you use a for-comprehension to multiply numbers in two ranges?](#How-do-you-use-a-for-comprehension-to-multiply-numbers-in-two-ranges)
* [What is a singleton object in Scala?](#What-is-a-singleton-object-in-Scala)
* [How do you define and use an anonymous function in Scala?](#How-do-you-define-and-use-an-anonymous-function-in-Scala)
* [What is a partial function in Scala?](#What-is-a-partial-function-in-Scala)
* [How do you define a partial function from Int to String in Scala?](#How-do-you-define-a-partial-function-from-Int-to-String-in-Scala)
* [What is a lazy val in Scala?](#What-is-a-lazy-val-in-Scala)
* [How do you define a lazy value in Scala?](#How-do-you-define-a-lazy-value-in-Scala)
* [What is a generic class in Scala?](#What-is-a-generic-class-in-Scala)
* [How do you define a generic function in Scala?](#How-do-you-define-a-generic-function-in-Scala)
* [What is a type parameter in Scala?](#What-is-a-type-parameter-in-Scala)
* [What is a view bound in Scala?](#What-is-a-view-bound-in-Scala)
* [What is a context bound in Scala?](#What-is-a-context-bound-in-Scala)
* [What is a self-type in Scala?](#What-is-a-self-type-in-Scala)
* [What is the relationship between a class and its companion object?](#What-is-the-relationship-between-a-class-and-its-companion-object)
* [What is a sealed class in Scala?](#What-is-a-sealed-class-in-Scala)
* [What is a case object in Scala?](#What-is-a-case-object-in-Scala)
* [What is a package object in Scala?](#What-is-a-package-object-in-Scala)
* [How do you overload a method in Scala?](#How-do-you-overload-a-method-in-Scala)
* [How do you override a method in Scala?](#How-do-you-override-a-method-in-Scala)
* [What is a block expression in Scala?](#What-is-a-block-expression-in-Scala)
* [What is string interpolation in Scala?](#What-is-string-interpolation-in-Scala)
* [How do you use a match expression in Scala?](#How-do-you-use-a-match-expression-in-Scala)
* [What does it mean for a function to be partial in Scala?](#What-does-it-mean-for-a-function-to-be-partial-in-Scala)
* [What is a closure in Scala?](#What-is-a-closure-in-Scala)
* [What is a tail-recursive function in Scala?](#What-is-a-tail-recursive-function-in-Scala)
* [How do you write a tail-recursive factorial function in Scala?](#How-do-you-write-a-tail-recursive-factorial-function-in-Scala)
* [How do you define a companion object in Scala?](#How-do-you-define-a-companion-object-in-Scala)
* [Can a trait extend other traits and classes in Scala?](#Can-a-trait-extend-other-traits-and-classes-in-Scala)
* [How do you mix a trait into a class in Scala?](#How-do-you-mix-a-trait-into-a-class-in-Scala)
* [What is a type alias in Scala?](#What-is-a-type-alias-in-Scala)
* [What is a Map in Scala?](#What-is-a-Map-in-Scala)
* [What is the difference between mutable and immutable collections in Scala?](#What-is-the-difference-between-mutable-and-immutable-collections-in-Scala)
* [How do you create and modify a mutable ListBuffer in Scala?](#How-do-you-create-and-modify-a-mutable-ListBuffer-in-Scala)
* [What is a Stream in Scala?](#What-is-a-Stream-in-Scala)
* [What is a view in Scala collections?](#What-is-a-view-in-Scala-collections)
* [With which types can you use for-comprehensions in Scala?](#With-which-types-can-you-use-for-comprehensions-in-Scala)
* [What is a monad in Scala?](#What-is-a-monad-in-Scala)
* [How are functions treated in Scala?](#How-are-functions-treated-in-Scala)
* [What is the difference between a method and a function in Scala?](#What-is-the-difference-between-a-method-and-a-function-in-Scala)
* [How do you pass a block of code as a parameter in Scala?](#How-do-you-pass-a-block-of-code-as-a-parameter-in-Scala)
* [Can a function return another function in Scala?](#Can-a-function-return-another-function-in-Scala)
* [How do you check if a partial function is defined for a value in Scala?](#How-do-you-check-if-a-partial-function-is-defined-for-a-value-in-Scala)
* [What kind of members can a trait have in Scala?](#What-kind-of-members-can-a-trait-have-in-Scala)
* [How does Scala handle multiple inheritance?](#How-does-Scala-handle-multiple-inheritance)
* [What is the purpose of a sealed trait in Scala?](#What-is-the-purpose-of-a-sealed-trait-in-Scala)
* [What are the main properties of a case class in Scala?](#What-are-the-main-properties-of-a-case-class-in-Scala)
* [What methods are automatically provided by a case class in Scala?](#What-methods-are-automatically-provided-by-a-case-class-in-Scala)
* [How are case classes used in pattern matching in Scala?](#How-are-case-classes-used-in-pattern-matching-in-Scala)
* [Why use a sealed trait in Scala?](#Why-use-a-sealed-trait-in-Scala)
* [Why use type parameters in Scala?](#Why-use-type-parameters-in-Scala)
* [What is a context bound in Scala?](#What-is-a-context-bound-in-Scala)
* [What is a view bound in Scala?](#What-is-a-view-bound-in-Scala)
* [What is a self-type in Scala?](#What-is-a-self-type-in-Scala)
* [What is a package object in Scala?](#What-is-a-package-object-in-Scala)
* [How do you overload a method in Scala?](#How-do-you-overload-a-method-in-Scala)
* [How do you override a method in Scala?](#How-do-you-override-a-method-in-Scala)
* [What is a block expression in Scala?](#What-is-a-block-expression-in-Scala)
* [What is string interpolation in Scala?](#What-is-string-interpolation-in-Scala)
* [How do you use a match expression in Scala?](#How-do-you-use-a-match-expression-in-Scala)
* [What is a closure in Scala?](#What-is-a-closure-in-Scala)
* [What is a tail-recursive function in Scala?](#What-is-a-tail-recursive-function-in-Scala)
* [How do you write a tail-recursive factorial function in Scala?](#How-do-you-write-a-tail-recursive-factorial-function-in-Scala)
* [How do you define a companion object in Scala?](#How-do-you-define-a-companion-object-in-Scala)
* [Can a trait extend other traits and classes in Scala?](#Can-a-trait-extend-other-traits-and-classes-in-Scala)
* [How do you mix a trait into a class in Scala?](#How-do-you-mix-a-trait-into-a-class-in-Scala)
* [What is a type alias in Scala?](#What-is-a-type-alias-in-Scala)

## What is Scala?
Scala is a modern multi-paradigm programming language designed to express common programming patterns in a concise, elegant, and type-safe way.

[Top](#top)

## Write a simple Scala program that prints 'Hello, world!'
object HelloWorld {
  def main(args: Array[String]): Unit = {
    println("Hello, world!")
  }
}

[Top](#top)

## What is the difference between 'val' and 'var' in Scala?
A 'val' is an immutable variable (like a final variable in Java), while a 'var' is mutable and can be reassigned.

[Top](#top)

## How do you define a function in Scala that adds two integers?
def add(x: Int, y: Int): Int = x + y

[Top](#top)

## What is a case class in Scala?
A case class is a special type of class in Scala that is immutable by default and compared by value. It is often used for modeling immutable data.

[Top](#top)

## How do you create a list of integers from 1 to 5 in Scala?
List(1, 2, 3, 4, 5)

[Top](#top)

## What is pattern matching in Scala?
Pattern matching is a mechanism for checking a value against a pattern. It is similar to switch statements in other languages but more powerful.

[Top](#top)

## How do you double every element in a list using map in Scala?
val doubled = List(1, 2, 3).map(x => x * 2) // List(2, 4, 6)

[Top](#top)

## What is a trait in Scala?
A trait is like a Java interface with partial implementation. It is used to share interfaces and fields between classes.

[Top](#top)

## How do you define a class Dog that extends class Animal in Scala?
class Animal
class Dog extends Animal

[Top](#top)

## What is Option in Scala?
Option is a container for zero or one element of a given type. It is used to avoid nulls.

[Top](#top)

## What is the difference between Some and None in Scala?
Some(5) represents a value, None represents no value.

[Top](#top)

## How do you specify a type annotation in Scala?
val x: Int = 42 // type annotation
val y = 42 // type inferred

[Top](#top)

## How do you write a for loop from 1 to 5 in Scala?
for (i <- 1 to 5) println(i)

[Top](#top)

## What is a companion object in Scala?
A companion object is an object with the same name as a class and is defined in the same file. It can access the class's private members.

[Top](#top)

## How do you define a singleton object in Scala with a method square?
object MathUtils {
  def square(x: Int): Int = x * x
}

[Top](#top)

## What programming paradigms does Scala support?
Scala supports both object-oriented and functional programming paradigms.

[Top](#top)

## How do you create a tuple with an Int, String, and Boolean in Scala?
val tuple = (1, "hello", true)

[Top](#top)

## What is a sealed trait in Scala?
A sealed trait can only be extended in the same file. This helps with exhaustive pattern matching.

[Top](#top)

## How do you create a Map from String to Int in Scala?
val map = Map("a" -> 1, "b" -> 2)

[Top](#top)

## What is a higher-order function in Scala?
A higher-order function is a function that takes other functions as parameters or returns a function.

[Top](#top)

## How do you define a curried function in Scala?
def add(x: Int)(y: Int): Int = x + y

[Top](#top)

## How do you filter even numbers from a list in Scala?
val even = List(1,2,3,4).filter(_ % 2 == 0) // List(2, 4)

[Top](#top)

## What are common uses for companion objects in Scala?
A companion object is used for factory methods, constants, and static members.

[Top](#top)

## How do you define a function with a default parameter in Scala?
def greet(name: String = "World"): String = s"Hello, $name!"

[Top](#top)

## What is a by-name parameter in Scala?
A by-name parameter is evaluated each time it is used, not when the function is called. Syntax: def f(x: => Int)

[Top](#top)

## How do you get the length of a string in Scala?
val s = "hello"
s.length // 5

[Top](#top)

## What can a trait contain in Scala?
A trait can have both abstract and concrete members (methods and fields).

[Top](#top)

## How do you create a Set of integers in Scala?
val set = Set(1, 2, 3)

[Top](#top)

## What is a function literal in Scala?
A function literal is an anonymous function, e.g., (x: Int) => x * 2

[Top](#top)

## How do you write an if-else statement in Scala?
val x = 10
if (x > 5) println("big") else println("small")

[Top](#top)

## How does Scala support multiple inheritance?
A class can extend only one class but multiple traits.

[Top](#top)

## How do you create an array of integers in Scala?
val arr = Array(1, 2, 3)

[Top](#top)

## What is a for-comprehension in Scala?
A for-comprehension is a concise way to build collections using for/yield.

[Top](#top)

## How do you use a for-comprehension to multiply numbers in two ranges?
val result = for (x <- 1 to 3; y <- 1 to 2) yield x * y

[Top](#top)

## What is a singleton object in Scala?
A singleton object is an object that is defined only once. It is used for static members.

[Top](#top)

## How do you define and use an anonymous function in Scala?
val inc = (x: Int) => x + 1
inc(5) // 6

[Top](#top)

## What is a partial function in Scala?
A partial function is a function that does not provide an answer for every possible input value.

[Top](#top)

## How do you define a partial function from Int to String in Scala?
val pf: PartialFunction[Int, String] = {
  case 1 => "one"
  case 2 => "two"
}

[Top](#top)

## What is a lazy val in Scala?
A lazy val is evaluated only when it is first accessed.

[Top](#top)

## How do you define a lazy value in Scala?
val lazyValue = lazy val x = { println("init"); 42 }

[Top](#top)

## What is a generic class in Scala?
A generic class or method works with any type. Syntax: class Box[T](value: T)

[Top](#top)

## How do you define a generic function in Scala?
def identity[T](x: T): T = x

[Top](#top)

## What is a type parameter in Scala?
A type parameter is a parameterized type, e.g., List[Int], Option[String].

[Top](#top)

## What is a view bound in Scala?
A view bound is a context bound that requires an implicit conversion. Syntax: T <% Ordered[T]

[Top](#top)

## What is a context bound in Scala?
A context bound requires an implicit value of a type class. Syntax: T: Ordering

[Top](#top)

## What is a self-type in Scala?
A self-type is a way to declare that a trait must be mixed into another type.

[Top](#top)

## What is the relationship between a class and its companion object?
A companion object can access private members of its companion class and vice versa.

[Top](#top)

## What is a sealed class in Scala?
A sealed class can only be extended in the same file.

[Top](#top)

## What is a case object in Scala?
A case object is like a case class but with no parameters. It is used for enumerations and pattern matching.

[Top](#top)

## What is a package object in Scala?
A package object is used to hold functions, variables, and type aliases for a package.

[Top](#top)

## How do you overload a method in Scala?
A method can be overloaded by defining multiple methods with the same name but different parameter lists.

[Top](#top)

## How do you override a method in Scala?
A method can be overridden using the 'override' keyword.

[Top](#top)

## What is a block expression in Scala?
A block expression is a group of expressions surrounded by braces, returning the value of the last expression.

[Top](#top)

## What is string interpolation in Scala?
A string interpolator allows embedding variables in strings. Syntax: s"Hello, $name!"

[Top](#top)

## How do you use a match expression in Scala?
A match expression is used for pattern matching, e.g., x match { case 1 => ... }

[Top](#top)

## What does it mean for a function to be partial in Scala?
A partial function is defined only for certain input values.

[Top](#top)

## What is a closure in Scala?
A closure is a function which uses one or more variables declared outside this function.

[Top](#top)

## What is a tail-recursive function in Scala?
A tail-recursive function is a function where the recursive call is the last operation. Use @tailrec annotation.

[Top](#top)

## How do you write a tail-recursive factorial function in Scala?
import scala.annotation.tailrec
@tailrec
def fact(n: Int, acc: Int = 1): Int =
  if (n <= 1) acc else fact(n - 1, n * acc)

[Top](#top)

## How do you define a companion object in Scala?
A companion object is defined using 'object' with the same name as the class.

[Top](#top)

## Can a trait extend other traits and classes in Scala?
A trait can extend other traits and classes.

[Top](#top)

## How do you mix a trait into a class in Scala?
A trait can be mixed into a class using 'extends' or 'with'.

[Top](#top)

## What is a type alias in Scala?
A type alias is a new name for an existing type. Syntax: type MyInt = Int

[Top](#top)

## What is a Map in Scala?
A map is an immutable collection of key-value pairs.

[Top](#top)

## What is the difference between mutable and immutable collections in Scala?
A mutable collection can be changed after it is created, while an immutable collection cannot.

[Top](#top)

## How do you create and modify a mutable ListBuffer in Scala?
import scala.collection.mutable.ListBuffer
val buf = ListBuffer(1,2,3)
buf += 4

[Top](#top)

## What is a Stream in Scala?
A stream is a lazy list where elements are computed only when needed.

[Top](#top)

## What is a view in Scala collections?
A view is a lazy version of a collection. Use .view to create one.

[Top](#top)

## With which types can you use for-comprehensions in Scala?
A for-comprehension can be used with Option, List, and other monads.

[Top](#top)

## What is a monad in Scala?
A monad is a design pattern used to handle computations as a series of steps.

[Top](#top)

## How are functions treated in Scala?
A function value is an object, so you can pass it as a parameter.

[Top](#top)

## What is the difference between a method and a function in Scala?
A method is part of a class or object, while a function is a value that can be assigned to a variable.

[Top](#top)

## How do you pass a block of code as a parameter in Scala?
A block of code can be passed as a function literal.

[Top](#top)

## Can a function return another function in Scala?
A function can return another function. This is called a higher-order function.

[Top](#top)

## How do you check if a partial function is defined for a value in Scala?
A partial function is defined only for certain input values and can be checked with isDefinedAt.

[Top](#top)

## What kind of members can a trait have in Scala?
A trait can have abstract and concrete members.

[Top](#top)

## How does Scala handle multiple inheritance?
A class can extend only one class but multiple traits.

[Top](#top)

## What is the purpose of a sealed trait in Scala?
A sealed trait can only be extended in the same file.

[Top](#top)

## What are the main properties of a case class in Scala?
A case class is immutable and compared by value.

[Top](#top)

## What methods are automatically provided by a case class in Scala?
A case class automatically provides equals, hashCode, and toString methods.

[Top](#top)

## How are case classes used in pattern matching in Scala?
A case class can be used in pattern matching.

[Top](#top)

## Why use a sealed trait in Scala?
A sealed trait is used to restrict which classes can extend it, helping with exhaustive pattern matching.

[Top](#top)

## Why use type parameters in Scala?
A type parameter allows you to write generic classes and methods.

[Top](#top)

## What is a context bound in Scala?
A context bound requires an implicit value of a type class.

[Top](#top)

## What is a view bound in Scala?
A view bound requires an implicit conversion.

[Top](#top)

## What is a self-type in Scala?
A self-type is a way to declare that a trait must be mixed into another type.

[Top](#top)

## What is a package object in Scala?
A package object is used to hold functions, variables, and type aliases for a package.

[Top](#top)

## How do you overload a method in Scala?
A method can be overloaded by defining multiple methods with the same name but different parameter lists.

[Top](#top)

## How do you override a method in Scala?
A method can be overridden using the 'override' keyword.

[Top](#top)

## What is a block expression in Scala?
A block expression is a group of expressions surrounded by braces, returning the value of the last expression.

[Top](#top)

## What is string interpolation in Scala?
A string interpolator allows embedding variables in strings. Syntax: s"Hello, $name!"

[Top](#top)

## How do you use a match expression in Scala?
A match expression is used for pattern matching, e.g., x match { case 1 => ... }

[Top](#top)

## What is a closure in Scala?
A closure is a function which uses one or more variables declared outside this function.

[Top](#top)

## What is a tail-recursive function in Scala?
A tail-recursive function is a function where the recursive call is the last operation. Use @tailrec annotation.

[Top](#top)

## How do you write a tail-recursive factorial function in Scala?
import scala.annotation.tailrec
@tailrec
def fact(n: Int, acc: Int = 1): Int =
  if (n <= 1) acc else fact(n - 1, n * acc)

[Top](#top)

## How do you define a companion object in Scala?
A companion object is defined using 'object' with the same name as the class.

[Top](#top)

## Can a trait extend other traits and classes in Scala?
A trait can extend other traits and classes.

[Top](#top)

## How do you mix a trait into a class in Scala?
A trait can be mixed into a class using 'extends' or 'with'.

[Top](#top)

## What is a type alias in Scala?
A type alias is a new name for an existing type. Syntax: type MyInt = Int

[Top](#top)
