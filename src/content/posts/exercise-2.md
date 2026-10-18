---
author: Borislav Galabov
pubDatetime: 2026-10-03T10:40:08Z
modDatetime: 2026-10-08T20:59:05Z
title: Second Exercise
slug: second-exercise
featured: false
draft: false
tags:
  - java
  - second-lab
  - beginner
description: Second Exercise for the Platform Independent Programming Languages course. 
---

![Boy learning Arrays in Java](/assets/images/exercise-2/boy-programming-java-arrays.webp)

Arrays
====================

## Table of contents

## 1. Introduction to Arrays

An **Array** is a data structure that holds sequence of elements of the same type. 
We can create arrays in two ways: 

```java
//new array with size 5 of type int
int[] arr = new int[5];

//new array of type int, with elements 1, 2 and 3.
int[] anotherArray = {1, 2, 3};

```

When we create an Array, we dynamically allocate memory for it, just like when creating new Objects: 

![Java Memory Model Simplified: Stack and Heap](/assets/images/exercise-2/stack-heap-simplified.png)



Arrays have: 
- type of the elements they hold
- fixed size
- random access to any element

These characteristics make them very efficient. 


```java
int[] arr = {1, 2, 3};

System.out.println(arr[0]);

```

```java
//set the value 123 to element with index 2
arr[2] = 123;

//print out the value of element with index 2
System.out.println(arr[2]);
```


## 2. Printing and assigning (changing) values

To print an array, we have to iterate through it's elements via loop: 

Example with `for` and `foreach` loops: 

```java
int[] numbers = {1, 2, 3, 4, 5};

//print array values via for-loop
for(int i = 0; i < numbers.length; i++) {
    System.out.println(numbers[i]);
}

System.out.println("----------------------")

//print array values via foreach-loop
for(int num : numbers) {
    System.out.println(num);
}
```

To fill our array with values, we also have to iterate it via loops. Here `foreach` is not an option: 

```java
int size = 5;
int[] numbers = new int[5];

Scanner scanner = new Scanner(System.in);

System.out.print("Enter " +size +" numbers, separated by space: ");

for(int i = 0; i < numbers.length; i++) {
    numbers[i] = scanner.nextInt();
}

```

## 3. Passing arrays to methods

Before passing arrays to methods, we need to understand how Java passes arguments to methods.
Java is always **pass-by-value**. This means that when we pass an argument to a method, the method receives a copy of the value we provide.

For primitive types, such as `int`, `double`, `float`, etc.., the copied value is the number itself. 

For **Arrays** and other **Objects**, the copied value is a reference to the same object. (i.e. two reference variables pointing to the same **Object**). 
As a result, a method can modify the elements of an existing array, but assigning a new array to the parameter does not replace the caller's original array: 

![Passing Arrays to Methods](/assets/images/exercise-2/passing-arrays-to-methods.png)


Example of passing primitive variable to method: 

```java file="Main.java"
public class Main {

    public static void main(String[] args) {

        int num = 21;

        changeNumber(num);

        //21 or 100?
        System.out.println(num);

    }

    public static void changeNumber(int number) {
        number = 100;
    }

}
```

Example of passing Array (Reference variable) to method: 

```java file="Main.java"
public class Main {

    public static void main(String[] args) {

        int[] numbers = {1, 2, 3};

        changeFirstElement(numbers);
        changeArray(numbers);

        //print array size
        System.out.println("Array size: " +numbers.length);

        //print array
        for(int i = 0; i < numbers.length; i++) {
            System.out.println(numbers[i]);
        }

    }

    public static void changeFirstElement(int[] numbers) {
        numbers[0] = 100;
    }

    public static void changeArray(int[] numbers) {
        numbers = new int[4];
        numbers[1] = 200;
    }

}
```

## 4. The java.util.Arrays class

The `java.util.Arrays` Class gives us a powerful set of methods which operate over Arrays. Here is part of them: 


| Method | Description |
| --- | --- |
| `Arrays.toString(arr)` | Converts the array's elements into a string representation. |
| `Arrays.equals(arr1, arr2)` | Compares two arrays element by element. |
| `Arrays.sort(arr)` | Sorts the original array in place. |
| `Arrays.binarySearch(arr, value)` | Searches a **sorted** array and returns the index if found; otherwise returns a negative value based on the insertion point. |
| `Arrays.fill(arr, value)` | Fills the array with the specified value. |
| `Arrays.copyOf(arr, length)` | Returns a copy of the array with the specified length (truncating or padding as needed). |


`Arrays.toString(arr)` example:

```java
    int[] arr = {1, 3, 5};
    System.out.println(Arrays.toString(arr));

```

`Arrays.equals(...)` example: 

```java
    int[] arr1 = {3, 4, 5};
    int[] arr2 = {3, 4, 5};
    int[] arr3 = {5, 4, 3};

    boolean areEqualArr12 = Arrays.equals(arr1, arr2);
    System.out.println(areEqualArr12);

    boolean areEqualArr23 = Arrays.equals(arr2, arr3);
    System.out.println(areEqualArr23);
```

`Arrays.sort(arr)` example: 
```java
    int[] arr = {5, 8, 2, 3};
    Arrays.sort(arr);
```

`Arrays.binarySearch(...)` example:  

```java
    int[] arr = {5, 8, 2, 3};
    Arrays.sort(arr);

    //returns the index of element with value 5 within arr. 
    int index = Arrays.binarySearch(arr, 5)
    System.out.println(index);

```

`Arrays.fill(arr, value)` example: 

```java
    int[] arr = new int[5];

    Arrays.fill(arr, 99);
```

`Arrays.copyOf(arr, length)` examples: 

```java
    int[] arr = {3, 5, 6, 1};

    int[] arr1 = {3, 5, 6, 1};

    int[] newArr = Arrays.copyOf(arr, 2);
    int[] newArr1 = Arrays.copyOf(arr, 10);

    //truncated
    System.out.println(Arrays.toString(newArr));

    //padded
    System.out.println(Arrays.toString(newArr1));

```


## 5. OOP throwback

Remember the `class Person` from our last exercise? 
We used to create new objects this way: 

```java
Person person = new Person();
person.name = "Ivan";
person.age = 20;

person.sayHello();
```
Basically what we did was: 

1. Created a *blank* **Person** object. 
2. Directly set values for in the `name` and `age` fields.  

This is not good practice, as the user can type anything as value to the `Person`'s fields and we have no mechanism for validation.  

Therefore, now we will add some fundamentals to safeguard our Class/Objects: 
1.  Declare the fields `name` and `age` as `private` -> No direct access with dot. `person.name` = "Ivan" will no longer work. 

2. Provide a **Constructor** which takes `name` and `age` as arguments. -> This way we can later add validation in it. We don't want people with negative `age`, right? :)

3. Provide **setter** methods, so there is mechanism to **change** `Person`'s data if necessary, and apply the same validation mechanism's as in the **Constructor**. -> Not always a good practice, but for now we stick to it. 

4. Provide **getter** methods, so there is mechanism to read `Person`'s data. 

Summary of our changes: 

```java fileName="Person.java"
class Person {

    String name;// [!code --]
    int age;// [!code --]

    private String name;// [!code ++]
    private int age;// [!code ++]

    //Constructor // [!code ++]
    Person(String personName, int personAge) { // [!code ++]
        name = personName; // [!code ++]
        age = personAge; // [!code ++]
    } // [!code ++]

    int getAge() { // [!code ++]
        return age; // [!code ++]
    } // [!code ++]

    void setAge(int newAge) { // [!code ++]
        age = newAge; // [!code ++]
    } // [!code ++]

    String getName() { // [!code ++]
        return name; // [!code ++]
    } // [!code ++]

    void setName(String newName) { // [!code ++]
        name = newName; // [!code ++]
    } // [!code ++]

    void sayHello() {
        System.out.println("Hello! My name is " + name +" and I am " + age + " years old.");
    }

}
```

For now, we stick to the above way of defining classes. 

## 6. Arrays of Objects

We can create Arrays of Objects as well: 

```java fileName="Person.java"
class Person {

    private String name;
    private int age;

    Person(String personName, int personAge) {
        name = personName;
        age = personAge;
    }

    int getAge() {
        return age;
    }

    void setAge(int newAge) {
        age = newAge;
    }

    String getName() {
        return name;
    }

    void setName(String newName) {
        name = newName;
    }

    void sayHello() {
        System.out.println("Hello! My name is " + name +" and I am " + age + " years old.");
    }

}
```

```java fileName="Main.java"
public class Main {

    public static void main(String[] args) {

        Person[] people = new Person[3];

        initializePeople(people);

        printPeopleData(people);



    }

    public static void initializePeople(Person[] people) {
        Scanner scanner = new Scanner(System.in);


        for(int i = 0; i < people.length; i++) {
            System.out.println("Enter data for Person " + i + ": ");

            System.out.print("Name: ");
            String name = scanner.nextLine();

            System.out.print("Age: ");
            int age = scanner.nextInt();
            //consume the \n character
            scanner.nextLine();

            people[i] = new Person(name, age);
        }
    }

     public static void printPeopleData(Person[] people) {
        for(int i = 0; i < people.length; i++) {
            System.out.println("Person: " +i ", Name: ", +people[i].getName + ", Age: " +people[i].getAge());
        }
     }
}
```


## 7. Tasks

### Task 1: Sum of Array elements

Write a program that has the following method: `public static int sum(int[] numbers)`. 
The method must take Array of integers as an argument and return a sum of the numbers. 


### Task 2: Multiply Array elements with certain value

Write a program that has the following method: `public static void multiply(int[] numbers, int factor)`. 
The method must take Array of integers as an argument and multiply the array elements with `int factor`. 

### Task 3: Printing and Comparing Arrays

Declare two arrays with same elements. Compare them by using: 
1. `Arrays.equals(arr1, arr2)`
2. `arr1 == arr2`

What is the output in these two cases? 

### Task 4: Sorting Arrays

Declare the following array: 
`int[] numbers = {8, 3, 1, 9, 4, 2};`

1. Use the `Arrays.sort(numbers)` method to sort it in ascending order. 
2. Now, use the `Arrays.copyOf(...)` method to create a copy, prior sorting. 
3. Print both arrays: prior- and post- sorting. 

### Task 5: Linear Search

Write the following method: `public static int linearSearch(int[] numbers, int target)`. 
The method must return the index of the first match of the `target` number within the `numbers` array. In case of no match, method must return `-1`.

### Task 6: Reverse an Array

Write a method that takes an int[] array as argument and reverses it, without creating a new array: `public static void reverseArray(int[] array)`. 

### Task 7: Count Occurrences

Write the following method: `public static int countOccurences(int[] numbers, int n)`.
The method must take an array of integers and count the occurences of a specific `int n` number. Returns `0` if number has no occurences. 

### Task 8: Remove Dupplicates

Write a method that takes an array of integers and returns new array, which contains only the unique elements, i.e. numbers. Use only arrays and loops. Do not use collections such as ArrayList or HashSet.


### Final Task – Implementing a Dynamic Book Stack Using Arrays

In this task, you will implement a **BookStack** application that manages a collection of books using an array. The stack should follow the **LIFO (Last In, First Out)** principle, meaning that the last book added is the first one removed.

The application should support adding and removing books, searching for books by price, and displaying the contents of the stack.

### Part 1 – The Book Class

Implement a `Book` class with the following properties:

- `String title` – the title of the book.
- `String author` – the author of the book.
- `double price` – the price of the book.

Your class should provide:

- A constructor to initialize the book's properties: `Book(String bookTitle, String bookAuthor, double bookPrice)`
- getter-methods, for reading information about the Book: 
`public String getTitle()`, `public String getAuthor()`, `public double getPrice()`

### Part 2 – The BookStack Class

You are provided with a skeleton of the `BookStack` class containing an array of `Book` objects and a variable that tracks the number of books currently stored.

Complete the following methods:

**1. `push(Book book)`**

Adds a book to the top of the stack.

- Store the book at the next available position in the array.
- If the array is full, increase its capacity before adding the new book. Otherwise you will end up outside of array bounds and your program will crash. 
- Update the number of books in the stack.

**2. `pop()`**

Removes and returns the most recently added book.

- Follow the LIFO principle.
- Update the number of books in the stack.
- Clear the array position previously occupied by the removed book.
- If the stack is empty, return `null`.

**3. `resize()`**

Increases the capacity of the internal array.

- Create a new array with twice the current capacity.
- Preserve all existing books.
- Use `Arrays.copyOf()` to perform the resizing.

**4. `searchByPrice(double minPrice)`**

Searches for books whose prices are greater than or equal to the specified value.

- Iterate through the books currently stored in the stack.
- Print all books that satisfy the condition.
- Display an appropriate message if no matching books are found.

**5. `printStackInformation()`**

- Prints information about the stack: current size and capacity
- Display all books currently stored in the stack.
- **Do not print unused array positions.**
- Display an appropriate message if the stack is empty.

Here is the `BookStack` class skeleton: 

```java fileName="BookStack.java"
public class BookStack {

    private Book[] books;
    private int size;

    public BookStack(int initialCapacity) {
        books = new Book[initialCapacity];
        size = 0;
    }

    public void push(Book book) {
        // TODO
    }

    public Book pop() {
        // TODO
        return null;
    }

    private void resize() {
        // TODO
    }

    public void searchByPrice(double minPrice) {
        // TODO
    }

    public void printStackInformation() {
        // TODO
    }
}
```

### Part 3 – Console Menu

You are provided with a skeleton of the `Main` class containing a console menu.

Complete the missing parts by calling the appropriate methods of `BookStack`.

The application should support the following operations:

```text
========== BOOK STACK ==========
1. Add a book
2. Remove a book
3. Search books by minimum price
4. Print stack information
0. Exit
================================
Enter your choice:
```

**Menu requirements:**

- **Option 1:** Read the book's title, author, and price from the console, create a `Book` object, and push it onto the stack.
- **Option 2:** Pop the most recently added book and print its details. Display a message if the stack is empty.
- **Option 3:** Read a minimum price from the console and display all books whose prices are greater than or equal to that value.
- **Option 4:** Display the number of books in the stack, the current array capacity, and the stored books.
- **Option 0:** Exit the application.

The menu should continue running until the user selects option `0`.

```java fileName="Main.java"
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        BookStack stack = new BookStack(2);

        int choice;

        do {
            System.out.println("\n=== BOOK STACK MENU ===");
            System.out.println("1. Add book");
            System.out.println("2. Remove book");
            System.out.println("3. Search books by minimum price");
            System.out.println("4. Print stack information");
            System.out.println("0. Exit");
            System.out.print("Choose an option: ");

            choice = Integer.parseInt(scanner.nextLine());

            switch (choice) {
                case 1:
                    System.out.print("Book title: ");
                    String title = scanner.nextLine();

                    System.out.print("Book author: ");
                    String author = scanner.nextLine();

                    System.out.print("Book price: ");
                    double price = Double.parseDouble(
                        scanner.nextLine()
                    );

                    // TODO: Create a new book
                    // TODO: Push the book onto the stack
                    break;

                case 2:
                    // TODO: Pop the last book
                    // TODO: Print the removed book
                    break;

                case 3:
                    System.out.print("Minimum price: ");
                    double minPrice = Double.parseDouble(
                        scanner.nextLine()
                    );

                    // TODO: Find and print matching books
                    break;

                case 4:
                    // TODO: Print stack information
                    break;

                case 0:
                    System.out.println("Goodbye!");
                    break;

                default:
                    System.out.println("Invalid option!");
            }

        } while (choice != 0);

        scanner.close();
    }
}
```

### Additional Requirements

- Do not use `ArrayList`, `Stack`, or other collection classes.
- The initial array capacity should be `2`.
- The array capacity should double whenever the stack becomes full.
- Distinguish between the **number of stored books (`size`)** and the **array capacity (`books.length`)**.
- Do not decrease the array capacity when books are removed.
- Test your implementation by adding more books than the initial capacity, removing books, and searching for books by price.

### Expected Behavior

For example, if the user adds three books to a stack with an initial capacity of `2`, the internal array should automatically expand to accommodate the third book.

After adding three books:

```text
Number of books: 3
Array capacity: 4
```

After removing one book:

```text
Number of books: 2
Array capacity: 4
```

**Goal:** Practice working with arrays of objects, implementing methods, performing linear searches, and using `Arrays.copyOf()` to build a dynamically resizing data structure.
















