---
author: Borislav Galabov
pubDatetime: 2026-10-03T10:40:08Z
modDatetime: 2026-10-08T20:59:05Z
title: First Exercise
slug: first-exercise
featured: false
image: /assets/images/exercise-1/boy-programming-in-java.png
ogImage: /assets/images/exercise-1/boy-programming-in-java.png
draft: false
tags:
  - java
  - first-lab
  - beginner
description: First Exercise for the Platform Independent Programming Languages course. 
---

![Boy, programming in Java](/assets/images/exercise-1/boy-programming-in-java.png)

Java Fundamentals
====================

In this exercise, we will learn how Java programs are compiled and executed and explore some of the fundamental constructs of the Java language.

## Table of contents

## What is an Object?

Before we start writing Java code, let's introduce one of the fundamental ideas behind **Object-Oriented Programming (OOP)** - we need to define what is an **object**. 

An **object** combines **data** and **behavior**.

The data stored inside an object represents its **state**, while the operations that the object can perform are represented by its **methods**.

For example, let's think about a car.

A particular car can have some state, defined by its properties:

- brand
- model
- color
- current speed
- fuel level

It can also have behavior:

- start
- accelerate
- brake
- stop

In an object-oriented program, we could represent a particular car as an object.

However, there are many different cars. Although they may have different values for their properties, they share the same general structure and behavior.

For example, all cars may have:

- a model
- an engine
- a transmission
- wheels
- a current speed

and all cars may be able to:

- start
- accelerate
- stop

OOP allows us to describe these common characteristics using a **class**.

### Class vs Object

A **class** defines a type of object — what data objects of that type can contain and what operations they can perform: 

This is how we decide to model a car:

![Car](/assets/images/exercise-1/car.png)

In Java, the above definition would look like this:

```java
class Car {

    String model;
    int currentSpeed;

    void start() {
        System.out.println("The car has started.");
    }

    void accelerate(int speed) {
        currentSpeed = currentSpeed + speed;
    }

    void stop() {
        currentSpeed = 0;
    }
}
```

The `Car` class describes what a car in our program looks like and what it can do.

We can then create individual objects from that class:

```java
Car firstCar = new Car();
firstCar.model = "VW Golf";
firstCar.start();
firstCar.accelerate(30);

Car secondCar = new Car();
secondCar.model = "Honda Civic";
...
secondCar.start();
secondCar.accelerate(50);
secondCar.stop();
```

Here:

- `Car` is the **class** (and the type).
- `firstCar` and `secondCar` refer to two different **objects**.
- Each object can have its own **state**.
- Both objects provide the behavior defined by the `Car` class.

A simple way to think about it is:


- `Class`  → definition of a type
- `Object` → particular instance of that type

Object-Oriented Programming allows us to model concepts from the problem we are solving — such as `Car`, `Person`, `Building`, `BankAccount`, or `Service` — as objects in our programs.

## How Java programs run

**Java is a compiled language, but unlike C/C++, Java is not normally compiled directly to machine code.**

Java source code is compiled by `javac` into bytecode, which is stored in `.class` files.

The bytecode is then executed by the **Java Virtual Machine (JVM)**.

This allows the same Java bytecode to run on different platforms, as long as an appropriate JVM is available.

**Java source → **`javac`** → bytecode → JVM → operating system / CPU**

This is the idea behind "Write once, run anywhere."

![Language Types](/assets/images/exercise-1/languages_types.png)

<details>
<summary>Read more about compiled, interpreted and Java programs</summary>

### Compiled languages

- In languages such as **C, C++, and Go**, the source code usually goes through a process called **compilation**. A compiler is a program that transforms the code written by the programmer into machine code or another form intended for execution on a specific platform. By *platform*, we can mean a combination of an **operating system and processor architecture** — for example, Windows + x86-64, Linux + x86-64, or Linux + ARM64. The resulting executable file is usually specific to the platform for which it was compiled.

### Interpreted languages

- Languages such as **Python, PHP, and Ruby** are commonly executed using a special program called an **interpreter**. The interpreter takes the source code and executes it without first producing a standalone machine-code executable. **Note:** The distinction between "compiled" and "interpreted" languages is not always that strict. For example, CPython also compiles Python source code into bytecode.

### Java

- Java uses a different approach. The Java compiler (`javac`) compiles Java source code into an intermediate form called **bytecode**, which is stored in `.class` files. The bytecode is then executed by the **Java Virtual Machine (JVM)**. 
This is where the famous idea comes from: "Write once, run anywhere."

</details>

Now, let's compile and run our first *Hello World* Java program: 

- Create a directory, named `HelloWorld`. 
- Paste the following contents into `HelloWorld.java` file: 

```java file="HelloWorld.java"
public class HelloWorld {
    
    //the main(...) method is the entry-point of our program
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
    
}
```
- To compile your Java program, open a terminal and run the following command: 
```shell
javac HelloWorld.java
```

- At this point, you should see a newly created file `HelloWorld.class`, which contains the Java bytecode. 

- Go back to the Terminal and run your Java program, by using the following command: 
```shell
java HelloWorld
```

- Now you should see the "Hello World!" message in your Terminal. Congratulations, you have run your first Java program!

## IntelliJ IDEA

Compiling and running Java programs manually from the terminal is useful
for understanding what happens behind the scenes. As you can see, it can be a tedious process, especially for big and more complicated programs. Therefore, in practice
we usually use an *Integrated Development Environment (IDE)*.

For this course, we will use **IntelliJ IDEA**.

An IDE provides us with tools for writing, compiling, running and
debugging our programs.

### Creating our first IntelliJ IDEA project

1. Open **IntelliJ IDEA**.
2. Select **New Project**.
3. Select **Java** as the project language.
4. Make sure that a **JDK** is selected.
5. Name the project `FirstProject`.
6. Create the project.

Inside the `src` directory, create a new Java class named `Main`.

```java
public class Main {

    public static void main(String[] args) {
        System.out.println("Hello from IntelliJ IDEA!");
    }

}
```

Run the program using the **Run** button next to the `main` method.

> **Note:** As your programs become larger and more complex, you will need to organize your code into logical groups.
>
> Java provides **packages** for this purpose. A package groups related classes and helps organize the structure of your application.
>
> In a typical Java project, packages correspond to directories inside the `src` directory.
>
> For example, we could place our `Car` class inside a package named `model`:
>
> ```text
> src/
> ├── model/
> │   └── Car.java
> └── Main.java
> ```
>
> The `Car` class would then declare that it belongs to the `model` package:
>
> ```java
> package model;
>
> public class Car {
>     String model;
>     int currentSpeed;
>
>     void start() {
>         System.out.println("The car has started.");
>     }
> }
> ```
>
> If we want to use `Car` from another package, we can import it. `import` statements must be on the top of the `.java` file. 
>
> ```java
> import model.Car;
> ```

So, to do a quick recap:

- **JDK (Java Development Kit)** — contains the tools needed to develop Java programs, such as the `javac` compiler, which compiles Java source code into bytecode (`.java` → `.class`).
- **JRE (Java Runtime Environment)** — contains the **JVM and the Java class libraries** needed to run Java applications.
- **JVM (Java Virtual Machine)** — executes Java bytecode.

In other words:

```text
JDK
├── Development tools (javac, jar, ...)
│
└── JRE
    ├── JVM
    └── Java Class Libraries
```

When we download and install the **JDK**, we get everything we need to both develop and run Java programs.


## Variables and Data Types

Now that we know how to create and run a Java program, let's start working with data.

A **variable** is a named location used to store a value. In Java, every variable has a **data type**, which determines what kind of value can be stored in it.

Unlike Python, Java is a **statically typed** language. This means that the type of a variable is known at compile time.

For example, in Python we can write:

```python
age = 20
name = "John"
```

In Java, we explicitly specify the type of each variable:

```java
int age = 20;
String name = "John";
```

The general syntax for declaring and initializing a variable is:

```text
type variableName = value;
```

For example:

```java
int studentsCount = 25;
double averageGrade = 5.25;
boolean passed = true;
char group = 'A';
String courseName = "Java";
```

### Primitive and Reference Types

Java data types can be divided into two main categories:

- **Primitive types** — store simple values such as numbers, characters and boolean values.
- **Reference types** — variables of these types hold references to objects.

Java has exactly **8 primitive types**:

| Type | Example | Description | Range |
| --- | --- | --- | --- |
| `byte` | `byte age = 20;` | 8-bit signed integer | -128 to 127 |
| `short` | `short year = 2026;` | 16-bit signed integer | -32,768 to 32,767 |
| `int` | `int count = 100;` | 32-bit signed integer | -2,147,483,648 to 2,147,483,647 |
| `long` | `long population = 8000000000L;` | 64-bit signed integer | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |
| `float` | `float length = 10.5f;` | 32-bit floating-point number | Precision: ~6-7 decimal digits |
| `double` | `double grade = 5.75;` | 64-bit floating-point number | Precision ~15-16 decimal digits |
| `char` | `char group = 'A';` | 16-bit Unicode character | '\u0000' (0) to '\uffff' (65,535) |
| `boolean` | `boolean passed = true;` | `true` or `false` | true or false |

> **Note:** Unlike the other primitive types, the Java Language Specification does not define a precise storage size for boolean. It can only have the values true and false.

> **Note:** `String` is **not** a primitive type in Java. `String` is a class, which makes it a reference type. We will discuss classes, objects and reference types in more detail later.

For integer types, the ranges can also be expressed as:

- byte: `−2⁷` to `2⁷ − 1`
- short: `−2¹⁵` to `2¹⁵ − 1`
- int: `−2³¹` to `2³¹ − 1`
- long: `−2⁶³` to `2⁶³ − 1`

`float` and `double` are data types with **Limited Precision**: 

```java
double a = 0.1;
double b = 0.2;

//is it 0.3 ?
System.out.println(a + b);
```

Do not use float or double when exact decimal arithmetic is required, for example for monetary calculations.



### Changing Variable Values

The value stored in a variable can be changed:

```java
int age = 20;

age = 21;

System.out.println(age);
```

The output will be:

```text
21
```

However, we cannot assign a value of an incompatible type:

```java
int age = 20;

age = "twenty"; // Compilation error
```

Since Java is statically typed, the compiler can detect this error **before the program is executed**. Trying to run the program will result in compilation error. 


## Console Input and Output

Java has three standard **streams**.

Think of a **stream** as a pipe through which data flows. The pipe represents the stream, while the data flowing through it represents the information being transferred.

The three standard streams are:

- `System.in` — **standard input stream**. By default, it receives input from the console, usually entered through the keyboard.
- `System.out` — **standard output stream**. By default, its output is displayed in the console.
- `System.err` — **standard error stream**. It is intended for error and diagnostic messages and is also displayed in the console by default.

### Output

Now that we know about the standard streams, let's take a closer look at output.

We have already used `System.out.println(...)` to print information:

```java id="vcfcl8"
// Have a good day!
System.out.println("Have a good day!");

// Have a good night!
System.out.print("Have a good ");
System.out.print("night!");

// Print information about an error
System.err.println("An error occurred.");

// Another error message
System.err.print("Another ");
System.err.print("error occurred.");
```

- `println()` — writes data and terminates the line with a newline character, moving the cursor to the next line.
- `print()` — writes data but leaves the cursor on the same line.

Both `System.out` and `System.err` are of type `PrintStream`, so they provide methods such as `print()` and `println()`.

For example:

```java id="1l319s"
System.out.println("Normal program output.");
System.err.println("Error or diagnostic output.");
```

### Input

`System.in` represents the **standard input stream**.

It allows us to read raw input data. For example, the stream provides methods such as `read()` for reading bytes.

Working directly with raw bytes, however, is inconvenient for most console applications.

For that reason, Java provides higher-level classes such as `Scanner`, which make reading different types of data much easier.

First, we need to import the `Scanner` class:

```java id="x6jp54"
import java.util.Scanner;
```

Then we can create a `Scanner` object that reads data from `System.in`:

```java id="rhpgl1"
Scanner scanner = new Scanner(System.in);
```

Conceptually, the data flows like this:

```text id="qs7j4o"
Keyboard
   ↓
System.in
   ↓
Scanner
   ↓
nextLine(), nextInt(), nextDouble(), ...
```

The `Scanner` class provides different methods for reading different types of data:

| Data type | Scanner method | Example |
| --- | --- | --- |
| `String` | `nextLine()` | `String name = scanner.nextLine();` |
| `String` | `next()` | `String word = scanner.next();` |
| `int` | `nextInt()` | `int age = scanner.nextInt();` |
| `long` | `nextLong()` | `long population = scanner.nextLong();` |
| `float` | `nextFloat()` | `float length = scanner.nextFloat();` |
| `double` | `nextDouble()` | `double grade = scanner.nextDouble();` |
| `boolean` | `nextBoolean()` | `boolean active = scanner.nextBoolean();` |

For example:

```java id="8vs3bv"
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter your name: ");
        String name = scanner.nextLine();

        System.out.print("Enter your age: ");
        int age = scanner.nextInt();

        System.out.print("Enter your grade: ");
        double grade = scanner.nextDouble();

        System.out.print("Are you a student (true/false): ");
        boolean student = scanner.nextBoolean();

        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Grade: " + grade);
        System.out.println("Student: " + student);
    }
}
```

#### `next()` vs `nextLine()`

There are two commonly used methods for reading text:

```java id="wj47vv"
scanner.next();
scanner.nextLine();
```

`next()` reads a single token, usually one word, while `nextLine()` reads the entire line.

For example, if the input is:

```text id="wc7cb5"
Ivan Ivanov
```

then:

```java id="eqp3re"
String name = scanner.next();
```

will read only:

```text id="ymxo12"
Ivan
```

while:

```java id="kzuq80"
String name = scanner.nextLine();
```

will read:

```text id="9rablf"
Ivan Ivanov
```

#### A Common Scanner Pitfall

There is an important difference between methods such as `nextInt()` and `nextLine()`.

Consider the following code:

```java id="knu021"
System.out.print("Enter your age: ");
int age = scanner.nextInt();

System.out.print("Enter your name: ");
String name = scanner.nextLine();

System.out.println("Hello " + name);
```

You may notice that `nextLine()` does not wait for you to enter the name.

This happens because `nextInt()` reads the integer value, but leaves the newline character (`\n`) in the input stream. The following `nextLine()` reads that remaining newline.

One way to solve this is to consume the remaining newline first:

```java id="ap0itp"
System.out.print("Enter your age: ");
int age = scanner.nextInt();

scanner.nextLine(); // consume the remaining newline

System.out.print("Enter your name: ");
String name = scanner.nextLine();

System.out.println("Hello " + name);
```

> **Note:** `Scanner` does not provide a `nextChar()` method. A single character can be read as a `String` and then accessed using `charAt(0)`:

```java id="62a3ka"
char group = scanner.next().charAt(0);
```


## Operators

Now that we know how to store values in variables, let's see what we
can do with them.

### Arithmetic Operators

Java provides the following basic arithmetic operators:

| Operator | Description | Example |
| --- | --- | --- |
| `+` | Addition | `a + b` |
| `-` | Subtraction | `a - b` |
| `*` | Multiplication | `a * b` |
| `/` | Division | `a / b` |
| `%` | Remainder | `a % b` |

For example:

```java
int a = 10;
int b = 3;

System.out.println(a + b); // 13
System.out.println(a - b); // 7
System.out.println(a * b); // 30
System.out.println(a / b); // 3
System.out.println(a % b); // 1

```

### Comparison operators

| Operator | Description | Example |
| --- | --- | --- |
| `>` | Greater than | `a > 3` |
| `<` | Less than | `a < 3` |
| `>=` | Greater than or equal | `a >= 3` |
| `<=` | Less than or equal | `a <= 3` |
| `==` | Equal | `a == 3` |
| `!=` | Not Equal | `a != b` |

```java
int age = 20;

System.out.println(age >= 18); // true
System.out.println(age == 20); // true
System.out.println(age != 20); // false

int a = 3;
int b = 5;

System.out.println(a == b); //false
System.out.println( !(a == b)); //true

```

### Logical Operators

| Operator | Name and Description | Example |
| --- | --- | --- |
| `&&` | Logical AND. Returns `true` if both statements are `true` | `a > 5 && a < 10` |
| `\|\|` | Logical OR. Returns `true` if one statement is `true` | `a > 5 \|\| b < 10` |
| `!` | Negation. Reverses the result, if statement is `true` returns `false` | `!(a > 0)` |


```java
boolean hasTicket = true;
int age = 20;

boolean canEnter = age >= 18 && hasTicket;

System.out.println(canEnter); //true

```

## Classes and Objects

As we mentioned in the beginning, in the OOP world, we can define our classes. 
Let's define a `class` named `Person`. 
In Java (and other OOP languages), we usually define classes in separate files. 
The file name must be the same as the class name:

1. Create `Person.java` file with the following content: 

```java file="Person.java"
public class Person {
  String name;
  int age;
  
  void sayHello() {
    System.out.println("Hello! My name is " + name +" and I am " + age + " years old.");
  }
}
```

A class defines the data and behavior that objects of that type will have.
In our example:
- `name` and `age` are fields — they represent the data of a `Person`.
- `sayHello()` is a method — it represents behavior of a Person. 

2. Now let's create an object of type `Person`:

```java file="Main.java"
public class Main {

    public static void main(String[] args) {
        Person person = new Person();
        person.name = "Ivan";
        person.age = 20;

        person.sayHello();
    }
}
```

The expression:

```java
new Person();
```

creates a new object, also called an instance of the Person
class.

```java
Person person
```
is a variable of type Person that holds a reference to the newly
created object, hence in the statement: 

```java
Person person = new Person();
```
- `Person` -> type
- `person` -> variable
- `new Person()` -> object


A class can be thought of as a definition of a type, while an
object is a particular **instance** of that class.

3. Now, lets add another person: 

```java file="Main.java"
public class Main {

    public static void main(String[] args) {
        Person person = new Person();
        person.name = "Ivan";
        person.age = 20;

        person.sayHello();

        Person anotherPerson = new Person();
        anotherPerson.name = "Maria";
        anotherPerson.age = 22;

        anotherPerson.sayHello();
    }
}
```

Here we have two **instances** of the `Person` class: `person` and `anotherPerson`. 

---

### Task 1

Write a program that reads a person's **name** and **age** from the console and uses them to create and populate a `Person` object.

After that, call the `sayHello()` method of the created object.

---

## Methods

A **method** is a named block of code that performs a specific operation. Methods can receive input through parameters and may return a value.

Methods declared in a class can be used to define the behavior of its objects.

In our `Person` class, we have already created a method:

```java
void sayHello() {
  System.out.println("Hello! My name is " + name + " and I am " + age + " years old.");
}
```

The general syntax of a method is:

```
returnType methodName(parameters) {
    // method body
}
```

In our example: 
```java
void sayHello() {
  /* method body */
}
```

- void is the return type;
- sayHello is the method name;
- () contains the method's parameters.
The keyword void means that the method does not return a value.

Methods can also return values:

```java
int getAge() {
    return age;
}
```

The return type of this method is int, so the method must return an
integer value:

```java
int personAge = person.getAge();
```

Methods can also receive values through parameters:

```java
void sayHelloTo(String name) {
    System.out.println("Hello, " + name + "!");
}
```

We can call it by passing an argument:

```java
person.sayHelloTo("Maria");
```

This is also a method: 
```java
public static void main(String[] args)
```
Here: 
- `void` - is the return type. `void` means nothing is returned.
- `main` - is the method name.
- `String[] args` — is a parameter named args of type String[] (an array of String objects).- `public static` - these are keywords. We will talk about them later.  

We'll discuss arrays in some of the next exercises. 

---

## Control Flow

So far, our programs have executed statements one after another, from top to bottom.

**Control flow statements** allow us to change this behavior. They allow our programs to:

- make decisions;
- execute different code depending on a condition;
- repeat a block of code multiple times.

### Conditional Statements

Conditional statements allow us to execute code only when a certain condition is satisfied.

### `if`

The simplest conditional statement is `if`:

```java
if (condition) {
    // code executed when the condition is true
}
```

For example:

```java
int age = 20;

if (age >= 18) {
    System.out.println("You are an adult.");
}
```

The expression:

```java
age >= 18
```

produces a `boolean` value — either `true` or `false`.

The body of the `if` statement is executed only when the condition evaluates to `true`.

We can also use a value entered by the user:

```java
Scanner scanner = new Scanner(System.in);

System.out.print("Enter your age: ");
int age = scanner.nextInt();

if (age >= 18) {
    System.out.println("You are an adult.");
}
```

### `if` / `else`

Sometimes we want to execute one block of code when the condition is `true` and another when it is `false`.

```java
if (condition) {
    // executed when condition is true
} else {
    // executed when condition is false
}
```

For example:

```java
System.out.print("Enter your age: ");
int age = scanner.nextInt();

if (age >= 18) {
    System.out.println("You are an adult.");
} else {
    System.out.println("You are a minor.");
}
```

We can also use the `Person` class that we created earlier:

```java
Person person = new Person();

System.out.print("Enter name: ");
person.name = scanner.nextLine();

System.out.print("Enter age: ");
person.age = scanner.nextInt();

if (person.age >= 18) {
    System.out.println(person.name + " is an adult.");
} else {
    System.out.println(person.name + " is a minor.");
}
```

### `else if`

When we have more than two possible cases, we can use `else if`:

```java
if (condition1) {
    // ...
} else if (condition2) {
    // ...
} else {
    // ...
}
```

For example:

```java
System.out.print("Enter your grade: ");
double grade = scanner.nextDouble();

if (grade >= 5.50) {
    System.out.println("Excellent");
} else if (grade >= 4.50) {
    System.out.println("Very good");
} else if (grade >= 3.50) {
    System.out.println("Good");
} else if (grade >= 3.00) {
    System.out.println("Passed");
} else {
    System.out.println("Failed");
}
```

The conditions are checked from top to bottom.

As soon as one condition evaluates to `true`, its block is executed and the remaining branches are skipped.

### Combining Conditions

We can combine multiple conditions using logical operators:

```java
&&   // AND
||   // OR
!    // NOT
```

For example:

```java
int age = 20;
boolean hasTicket = true;

if (age >= 18 && hasTicket) {
    System.out.println("You can enter.");
}
```

Another example:

```java
int temperature = 25;

if (temperature < 0 || temperature > 35) {
    System.out.println("Extreme temperature.");
}
```

### `switch`

When we compare one value against several predefined values, a `switch` statement can sometimes be easier to read than multiple `else if` statements.

In Java 8, the syntax looks like this:

```java
switch (value) {
    case value1:
        // code
        break;

    case value2:
        // code
        break;

    default:
        // code
        break;
}
```

For example:

```java
System.out.print("Enter day number: ");
int day = scanner.nextInt();

switch (day) {
    case 1:
        System.out.println("Monday");
        break;

    case 2:
        System.out.println("Tuesday");
        break;

    case 3:
        System.out.println("Wednesday");
        break;

    case 4:
        System.out.println("Thursday");
        break;

    case 5:
        System.out.println("Friday");
        break;

    case 6:
        System.out.println("Saturday");
        break;

    case 7:
        System.out.println("Sunday");
        break;

    default:
        System.out.println("Invalid day.");
        break;
}
```

The `break` statement stops the execution of the `switch` after a matching `case` has been executed.

Without `break`, execution continues into the following `case`.

---

### Task 2

Write a program that reads an integer from the console and prints whether the number is:

- `positive`
- `negative`
- `zero`

*Sample input*: 10
*Sample output*: positive

---

### Task 3

Write a program that reads an integer and determines whether it is **even** or **odd**.

Hint:

```java
number % 2
```
*Sample input*: 2
*Sample output*: even
---
*Sample input*: 11
*Sample output*: odd
---

### Task 4

Extend the `Person` program from Task 1. 

Create a method `void showSocialStage()` which: 

- prints `"Minor"` if the person's age is below 18;
- prints `"Adult"` if the person's age is between 18 and 64;
- prints `"Senior"` if the person's age is 65 or above.

Make a call to `showSocialStage()` method in main(...);

*Sample input*: 
Ivan
20
*Sample output*: Adult



---

## Loops

Loops allow us to execute a block of code repeatedly.

### `while`

A `while` loop executes its body while a condition remains `true`.

```java
while (condition) {
    // repeated code
}
```

For example:

```java
int number = 1;

while (number <= 5) {
    System.out.println(number);
    number++;
}
```

Output:

```text
1
2
3
4
5
```

### `for`

A `for` loop is commonly used when we know how many times we want to repeat an operation.

```java
for (initialization; condition; update) {
    // repeated code
}
```

For example:

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

This produces the same output:

```text
1
2
3
4
5
```

The three parts of the `for` loop are:

```java
for (int i = 1; i <= 5; i++)
```

- `int i = 1` — initialization, executed once before the loop starts;
- `i <= 5` — condition, checked before every iteration;
- `i++` — update, executed after every iteration.

### Task 5

Read an integer `n` from the console and print all numbers from `1` to `n`.

*Sample input*: 3
*Sample output*: 
1
2
3


### Task 6

Read an integer `n` and print all even numbers from `1` to `n`.

*Sample input*: 11
*Sample output*: 
2
4
6
8
10

### Task 7

Read an integer `n` and calculate the sum of all integers from `1` to `n`.

*Sample input*: 6
*Sample output*: 21







