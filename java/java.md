# oop
**Object-oriented programming** or **OOP** is the paradigm where the program is written as a collection of classes. Each class has instances called objects.

A class is a way of describing an entity in general, defining the usual state and behavior that depends on that state, as well as the usual rules for interacting with this entity. Formally, a class is viewed as a set of data like fields, attributes, class members, and functions, i.e. methods for working with them.

For example, we have an entity _cat_ and we want to describe it using a class. So, the _cat_ will be an object of the corresponding _Cat_ class. A cat has some attributes, for example, a tail, paws, claws, muzzle, ears, and whiskers. A cat's behavior is what it usually does, for example, it can run, jump, meow, eat, and rip off the wallpaper. All of these will be _cat_ methods.

OOP can handle almost all kinds of common real-life problems where you need to model typical objects and work with them.

Programming languages that have implemented the OOP paradigm are Ruby, Java, C++, Python, Simula (the first OOP language), Smalltalk, Visual Basic .NET, and Objective-C.

---
# functional programming
**Functional programming** is a programming paradigm in which the computation process is interpreted as the computation of the values of functions. The function, in this case, is similar to a mathematical one. That is, a function in which the input is an array that is not changed, and the output is a new array with new data. This makes a mathematical function different from a function in procedural programming, where a function is a sequence of actions that change the original data.

Here's a simple example: you might have a function that takes a list of numbers as input and returns a new list with the squares of those numbers. This does not change the original list of numbers.

Programming languages that have implemented the Functional programming paradigm are JavaScript, Haskell, Scala, Erlang, Lisp, ML, Clojure, OCaml, and F#.

---
# IDE: IntelliJ IDEA

- `main` : makes program runnable, the first to be executed when the program runs
```java
public class HelloWorldProgram {
	public static void main(String[] args) {
		System.out.println("Hello World");
	}
}
```

```java
// declaration
DataType variableName = initialization;

String language = "java";
int numberOfApples = 5;

String dayOfWeek = "Monday";
System.out.println(dayOfWeek); // Monday

int one = 1;
int num = one;
System.out.println(num); // 1

String dayOfWeek = "Monday";
System.out.println(dayOfWeek); // Monday

dayOfWeek = "Tuesday";
System.out.println(dayOfWeek); // Tuesday

int number = 10;
number = 11; // ok
number = "twelve"; // it does not work!

String language = "java", version = "8 or newer"

int age; // declaration
age = 35; // initialization

// Type inference
var variableName = initialization;

var language = "Java"; // String
var version = 10; // int

```

