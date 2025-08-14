# Classes & Objects

### OOPS
```
Object-Oriented Programming (OOP) is a way of writing programs by grouping data (variables) and behavior (methods) into objects.

It makes code easier to understand, reuse, and maintain.

```
### Principles of  OOPS
```
(1) Classes and Objects (2) Encapsulation (3) Abstraction (4) Polymorphism (5) Inheritance
```

## What is a Class?
```
Classes are rules imposed on an object. 

ie class is a blueprint or set of rules that defines how objects behave and what they can do.
```
## What is an Object?
```
An object is a real-world entity that occupies memory space.

Objects are created → They should follow the rules → They perform various actions → When tasks are completed → Objects are destroyed.

```
## Class vs Object - Real World Example
```

Car is an object, a real world entity. When we create a Car object, it must follow the rules defined in the Car class.

Car class defines rules like maximum speed, number of wheels, type of fuel, braking system.

Actions (methods) could be: start(), accelerate(), brake(), refuel().

Properties (variables) could be: color, speed, fuelType. 

```
##  Real Object with Class's Properties and Methods!

```
From this blueprint (class), we can create different Car objects -

A black car with a speed of 110 km/hr that can start, accelerate, brake, and refuel.

A white car with a speed of 200 km/hr that can start and accelerate.

This shows how an object is a real instance of a class, with its own unique property values but the same set of actions defined by the class.

```

## Class, Object, and Methods — Explained with a Student Example

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
11. 
12.    // Functionality → task / Non - static Method - which performs calculation of marks
13.    public void calculateTotalMarks() { // Method name should describe the action it performs
14.        double totalMarks = marksObtainedInEnglish + marksObtainedInMaths + marksObtainedInScience;
15.        System.out.println("Total Marks Obtained: " + totalMarks); // print the result
16.    }
17. }
```

## Instance Variables

```
Variables created inside a Class are called Instance variables - age, rollNumber,marksObtainedInEnglish, marksObtainedInMaths, marksObtainedInScience,Grade.

They are non - static.

Instace variables are implicitly initialized with default values.

Stored in Heap Memory.
```

## Role of main() in program excecution .
```
To execute the program, we need a main method.

Best practice → Name the executable class as Runner (class containing the main method).
```
```java
1. package com.student.management.system.oops;

2. public class Runner {                   // Class that contains the main method
3. 
4.     public static void main(String[] args) {  // Entry point of the program
5.         int x = 10;                     // Local variable in stack memory
6.         int[] y = new int[3];           // Array object in heap, reference in stack
7.         Student s1 = new Student();     // Creating a Student object in heap
8.     }
9. }
```
## Local Variable
```
Variables created inside a method are called Local Variables.  

- They are stored in stack memory.

- Java does not initialize them with default values — we must assign a value before using them, otherwise we'll get a compile-time error.  

- Their lifetime is only until the method finishes execution, after that, they are removed from the stack.

```
``` java
public void show() {

    int x;  // Local variable, no default value
    
    System.out.println(x); //  Compile-time error: variable x might not have been initialized
}
```


## Program Execution Flow

**Java executes the program line by line:**

### Line 1 → package com.student.management.system.oops;
```
A package is like a folder that groups related classes together.

It also helps avoid name conflicts between classes with the same name in different projects.
```
### Line 2 → public class Runner
```
java enters this class only if it has a valid main method.
```
### Line 4 → public static void main( )
```
Execution starts here.

main() method is pushed into the stack memory.

The stack top pointer now points to main().
```
```   Stack Memory
+---------------------------+
|  main()                   |  ← top pointer
+---------------------------+
```
### Line 5 → int x = 10;
```
java excecutes RHS first → evaluate 10.

Type check → Is 10 an integer? ✅ Yes. Is it stored in an int variable? ✅ Yes.

Allocate 4 bytes for x in stack (inside main’s stack frame).

java intialize 10 to x.
```
```
Stack Memory
+---------------------------------------+
| main() is pushed into the stack       |
|                                       |
|---------------------------------------|
top -> | main()   | x = 10              |
+---------------------------------------+
```

### Line 6 → int[] y = new int[3];
```
java executes RHS first → `new int[3]` creates an array object in the heap with 3 memory slots.

Since an array is a non-primitive type, Java automatically initializes all elements to their default values. (For `int`, the default value is `0`)

When the array is created in the heap, it gets a memory address (e.g., `999`).  

When Java executes the LHS, this address is stored in `y` (in the stack), so `y` now points to that array in the heap.

```
```
Stack Memory                  Heap Memory
+------------------------+    +----------------------------+
| main                   |    |  999  (int[])              |
| x = 10                 |    |  +---+---+---+             |
| y ---> 999 ------------+--->|  | 0 | 0 | 0 |             |
+------------------------+    |  +---+---+---+             |
                               |   0   1   2                |
                               +----------------------------+
 ```                             
### Line 7 → Student s1 = new Student();
```
           Student s1 = new Student();

           Student - user defined data type

           s1 = reference variable

           new Student() - Object

           java excecutes RHS first - new Student() creates an object student in heap memory
```
```
java executes RHS first → new Student():

new keyword = always creates a new object in the heap.

When ever an object is created 3 things happen -

Step 1: Student class is loaded into memory called Method Area

                 Method Area - Stores class-level information — not per-object data. 
                 Method Area is part of JVM memory from the start, but it’s empty until classes are loaded.
                 Created when the class is first loaded by the JVM (before any object is created).

Step 2: Instance variables are created in heap and initialized with default values.

Step 3: Constructor is called (if not defined, Java provides a default constructor and executes it).

The object’s memory address (e.g., 101) is created.

LHS → s1 is a reference variable in stack; it stores the address/hashcode (e.g., 101) pointing to the Student object in heap.

```
```
Stack Memory                   Heap Memory
+------------------------+    +------------------------------------+
| main                   |    | 101 (Student object)               |
| x = 10                 |    | +------------------------------+   |
| y ---> 999             |    | | grade      = null             |   |
| s1 ---> 101 -----------+--->| | science    = 0                |   |
+------------------------+    | | maths      = 0                |   |
                              | | name       = null             |   |
                              | | age        = 0                |   |
                              | | marksEng   = 0                |   |
                              | | rollNumber = 0                |   |
                              | +------------------------------+   |
                              +------------------------------------+
 ``` 

### Line 8 → } (method closing brace)

```
Marks the end of the main() method.

When main() ends, the stack frame for main is removed (popped) from the stack memory.

All local variables (x, y, s1) are destroyed — but the objects they pointed to in heap remain in memory until garbage collection runs.
```
```
Stack Memory (after main ends)
+---------------------------+
|  (empty — main removed)   |
+---------------------------+
```

### Line 9 → } (class closing brace)
```
Marks the end of the Runner class.

At this point, program execution is complete (unless there are other threads running).
```                            
### Note:
```

All instance variables in heap get default values based on their type.

A real Student object is created in heap memory with its own name, age, rollNumber, marks, etc., ready to be used by the program, and can be accessed using the reference variable s1.

```



