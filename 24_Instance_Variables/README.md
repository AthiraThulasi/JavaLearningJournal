
# Accessing instance Variables

## What are Instance Variables?
```
Instance variables are variables declared inside a class but outside any method, constructor, or block.

Instance variables are stored in heap memory along with the object, and if not explicitly initialized, they are automatically assigned default values.
```
```java
class Student {
    String name;    // instance variable
    int age;        // instance variable
    double marks;   // instance variable
}

```
## Part 1 – Defining Instance Variables in a Class

```
This class defines the properties (instance variables) of a Student. These variables are stored in heap memory when an object is created.
```

```java

1. package com.student.management.system.oops;

2. public class Student {    // Student is the class name
3.     
4.     int age;
5.     int rollNumber;
6.     double marksObtainedInEnglish;        // variables created inside the class → instance variables - stored in Heap memory
7.     String name;                          // instance variables are properties of class
8.     double marksObtainedInMaths;
9.     double marksObtainedInScience;
10.    String grade;

// Functionality → task / Non - static Method - which performs calculation of marks
11.    public void calculateTotalMarks() { // Method name should describe the action it performs
12.        double totalMarks = marksObtainedInEnglish + marksObtainedInMaths + marksObtainedInScience;
13.        System.out.println("Total Marks Obtained: " + totalMarks); // print the result
14.    }
15. }
```
## Part 2 – Creating an Object and Accessing Instance Variables
```
This Runner class creates a Student object and shows how to access its instance variables using a reference variable.
```

```java


1. package com.student.management.system.oops;

2. public class Runner {                   // Class that contains the main method
3.     public static void main(String[] args) {  // Entry point of the program
4.         int name; // Local variable — stored in Stack
5.         
6.         Student s1 = new Student(); // Object in Heap, reference (s1) in Stack

7.         System.out.println(s1);      // Prints: packageName.className@hashcode (in hexadecimal) — it's the hashcode from Object.hashCode()

8.         
9.         // Accessing instance variables
10.        System.out.println(s1.name); // Prints 'null' (default value)
11.        System.out.println(s1.age);  // Prints 0 (default value)
12.    }
13. }

```
## Recap on what happens during an object creation!

```java
----------------------------
 Student s1 = new Student();
------------------------------
```
```
RHS : new Student();

 Java executes RHS first → new Student()

 new keyword = always creates a new object in the heap.

 A new object is created in heap memory.

 When an object is created in the heap, 3 things happen in order:

      Step 1: The Student class is loaded into memory called Method Area.

                 Method Area - Stores class-level information — not object data. 
                 Method Area is part of JVM memory from the start, but it’s empty until classes are loaded.
                 class loading into the Method Area happens only the first time when we use that class in our program. Class loading is done by class loader

      Step 2: Instance variables for that object are created in heap and initialized with default values (e.g., int = 0, String = null).

      Step 3: Constructor is called.

 If no constructor is defined, Java provides a default no-arg constructor and executes it.

 Constructor then sets the instance variables to the values we specify (if any).

 The object’s memory address (e.g.101 or a hashcode) is created internally.

 LHS : Student s1

 s1 is a reference variable stored in the stack.

 It holds the address/hashcode that points to the object in heap.
 ```

## Now, Let's understand - What is a reference variable ?

``` 
Imagine we have a locker in a gym.

The locker contains our gym shoes, water bottle, and towel (locker is our object with its items = instance variables).

We don’t carry the entire locker around. Instead, we are given a locker key with a number written on it.

That key doesn’t hold the items itself — it just points to where our locker is in the gym.

In Java terms:

Object = The locker (where all instance variables live).

Reference variable = The locker key (knows the location of the locker in memory).

Instance variables = The items inside the locker (the actual data).

We can have multiple keys (references) to the same locker (object), but the data is still stored in one place.

No matter how many keys we have, they all open the same locker and see the same things inside.

If we change something in the locker using one key, the change is visible to anyone using the other keys.
```


## What happens if we print reference variable - s1?

```java
System.out.println(s1);  // o/p - com.student.management.system.oops.Student@512ddf17
```
```

Printing a reference variable gives the hashcode generated by the hashCode() method 

Hashcode > com.student.management.system.oops.Student@512ddf17

        com.student.management.system.oops → The package name where the Student class is located.

        Student → The class name of the object.

        @ → Separator between the class name and the hashcode.

        512ddf17 → The hashcode of the object, represented in hexadecimal (base 16).

```

## How to access instance variables?
```
We can access instance variables using the object reference variable followed by a dot (.) and the variable name.

If we haven’t assigned any value yet, Java prints the default value for that variable’s type.
```
```java

 System.out.println(s1.name); // Prints 'null' (default value of String)

 System.out.println(s1.age);  // Prints 0 (default value of age)

```

## How to assign values to instance variabels?

```java
1. package com.student.management.system.oops;

2. public class Runner {    
3.                   // Class that contains the main method
4.   public static void main(String[] args) {  // Entry point of the program
5.
6. Student s1 = new Student(); // Object creation

7. s1.name = "Neil";  // Assigning values to instance variables
8. s1.age = 10;
9. s1.rollNumber = 30;
10. s1.marksObtainedInEnglish = 50;
11. s1.marksObtainedInMaths = 48;
12. s1.marksObtainedInScience = 47;
13. s1.grade = "A";

14. System.out.println(s1.name); //  Retrieving the value of 'name' and printing it
15. System.out.println(s1.age);
16. System.out.println(s1.rollNumber); //Retrieving the value of 'rollNumber' and printing it
17. System.out.println(s1.grade);
18. System.out.println(s1.marksObtainedInEnglish); // Retrieving the value of 'name' and printing it
19. System.out.println(s1.marksObtainedInMaths);
20. System.out.println(s1.marksObtainedInScience);

21. s1.calculateTotalMarks();

```
## How this value assignment happens ?

### Line 6 
```java

Student s1 = new Student(); 
```
```
An object is created in heap memory, and its instance variables are allocated space and initialized with default values.

         Stack Memory                      Heap Memory
+---------------------------+      +-----------------------------------+
| main()                    |      |  777  (Student object)            |
|                           |      |  +---------------------------+    |
| s1 ---> 777 --------------+----->|  name         = null           |  |
|                           |      |  age          = 0              |  |
|                           |      |  rollNumber   = 0              |  |
|                           |      |  marksEnglish = 0              |  |
|                           |      |  marksMaths   = 0              |  |
|                           |      |  marksScience = 0              |  |
|                           |      |  grade        = null           |  |
+---------------------------+      +---------------------------+---+
```
### Line 7 

```java
s1.name = "Neil";
```

```

Java checks where s1 is stored — it’s a local variable in stack memory (s1 is a local variable inside main() method).

In the stack, s1 holds the value 777 (a reference/address pointing to the object in heap).

Java follows this reference 777 into the heap memory to locate the Student object.

Inside that object, Java finds the name instance variable.

The default value null is replaced with "Neil".

Same process happens for Lines 8–13:
```

```
         Stack Memory                      Heap Memory
+---------------------------+      +-----------------------------------+
| main()                    |      |  777  (Student object)            |
|                           |      |  +---------------------------+    |
| s1 ---> 777 --------------+----->|  name         = "Neil"        |   |
|                           |      |  age          = 10            |   |
|                           |      |  rollNumber   = 30            |   |
|                           |      |  marksEnglish = 50            |   |
|                           |      |  marksMaths   = 48            |   |
|                           |      |  marksScience = 47            |   |
|                           |      |  grade        = "A"           |   |
+---------------------------+      +---------------------------+---+
```

## How to retrieve values from instance variables?

```java

14. System.out.println(s1.name); // retrieving values by printing it off
15. System.out.println(s1.age);
16. System.out.println(s1.rollNumber);
17. System.out.println(s1.grade);
18. System.out.println(s1.marksObtainedInEnglish);
19. System.out.println(s1.marksObtainedInMaths);
20. System.out.println(s1.marksObtainedInScience);
```

### Line 14

```java
System.out.println(s1.name);
```

```
Java looks in the stack memory for the variable s1.

It finds that s1 holds the reference value 777 (hashcode/address of the object in heap).

Using this reference, Java goes to the heap memory and locates the Student object.

It checks if the object has a variable named name —  Yes.

Java retrieves the current value stored in name ("Neil") and prints it to the console.
```
## Now We Understand –How Are Objects and Classes Related?
```
We first created the Student class — this is like a blueprint.

The class only describes what a student has (properties) and can do (methods).

To actually use these properties, we need to create an object from the class.

After creating the object, we can assign values to its variables and use its methods.

```

## In short:
```
A class is the plan — like a blueprint of a student, describing properties like name, age, marks, and grade, and methods like calculating total marks.

An object is the real thing made from that plan — a real student with an actual name, age, marks, and grade.

```
## What Are the Problems or Drawbacks Here?
```
Right now, instance variables in our Student class can be accessed directly from outside the class.

This means anyone can assign invalid values to them without any checks.

Example:

Setting age = -110 — clearly invalid, but nothing stops us from doing it.

Setting rollNumber = 0 — may not be valid for our system.

Setting grade = "ABC" — might not match our allowed grading system.
```
```java

7.  s1.name = "123@Neil";                 // Assigning invalid name
8.  s1.age = -110;                    //  Invalid age
9.  s1.rollNumber = 0;                //  Invalid roll number
13. s1.grade = "ABC";                 //  Invalid grade format
```
## Key issue:
```

Direct access to instance variables breaks control over the data and can lead to incorrect or inconsistent objects.

```
## What Is the Solution to This Invalid Value Assignment Problem?

```
The solution is Encapsulation.

Encapsulation means hiding the internal details of a class (its variables) and allowing access only through controlled methods.

we will see it in detail in the next section with examples.

```





