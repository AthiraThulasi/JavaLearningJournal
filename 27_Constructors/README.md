# Constructors


## What is a Constructor?
```
A constructor is a special method in a class, which has the same name as the class name.

```
## What s the job of the constructor?

```
The job of the constructor is to initialize instance variables during object creation.

```

## How to create a constructor in an IDE (IntelliJ/Eclispse)?

```
Open class file in the editor.

Place the cursor inside the class but outside any existing methods.

Right-click → select Source → Generate Constructor using Fields.

```
## What is a default constructor?
```

It’s the constructor Java provides automatically if we don’t write any constructor in our class.

It has no parameters and no body code .
```
```java
class Student {
    int age;
    String name;

    // Default constructor (automatically created by Java):
    // Student() { super(); }
}
```
## Student Class - How constructor in a class look like?

```java

1. package com.student.management.system.oops;

2. public class Student {    // Student is the class name
3.     
4.      int age;         // variables created inside the class → instance variables - stored in Heap memory
5.      int rollNumber;  // instance variables are properties of class // cannot be static
6.      String name;     // instance variables are assigned with default values, if not initialized              
7.                              
8.     public Student(String name, int age, int rollNumber) {
10.        this.name = name;
11.        this.age = age;
12.        this.rollNumber = rollNumber;
13.     
   


// Constructor - has same name as the class
// parametres in the constructor - are local variables - created in stack memory
// constructor with parameter is called parameterized constructor

14.        this.marksObtainedInEnglish = marksObtainedInEnglish;
15.        this.marksObtainedInMaths = marksObtainedInMaths;
16.        this.marksObtainedInScience = marksObtainedInScience;
17.        this.grade = grade;
18.    }

19.      public void setRollNumber(int rollNumber){ // added a setter with validation for rollnumber
20.     if(rollNumber >=1)
21.              this.rollNumber = rollNumber;
22.   }
23.   else{
24.     System.out.print("Invalid roll number");
25.     }  
26. }

```
## Student Runner Class

```java
package com.student.management.system.oop;

public class Runner {

    public static void main(String[] args) {

        Student s1 = new Student("Neil", 10, 26, 40, 30, 41, "B");// // Object creation → calls the constructor and assigns values to instance variables

       s1.setName("John");   // Setter updates the 'name' instance variable from "Neil" → "John"
       s1.setRollNumber(-10); // Setter validation fails → rollNumber remains 26 (from constructor)

        System.out.println(s1.getName());
        System.out.println(s1.getRollNumber());
    }
}
```
## What happens during Object creation?

```
During object creation - we pass all the values of instance variables, and constructor pass it and use it for assigning to instance variables.

   Student s1 = new Student("Neil", 10, 26, 40, 30, 41, "B");

Constructor is called ONCE - ONLY DURING OBJECT CREATION. 

```
## 2. How is Constructor different from Setter ?

```
-------------------------------------------------------------------------------------------------------------------------------------------
| Constructor                                                 | Setter                                                                     |
| ----------------------------------------------------------- | -------------------------------------------------------------------------- |
| Constructor is Called ONLY ONCE during object creation.     | Setter can be called MULTIPLE TIMES after object creation.                        |
| 
| Initializes instance variables with initial values.         | Updates/modifies instance variables after object creation.                 |
| 
| Java provides a DEFAULT CONSTRUCTOR, if none is written.    | Must be explicitly created by the programmer.                              |
| 
| Has NO RETURN TYPE                                          | Has a return type, usually `void`                                          |
|                                                             |                                                                            |
| Example: `new Student("Neil", 17, 25)`                      | Example - `s1.setName("Uday")`                                             |
--------------------------------------------------------------------------------------------------------------------------------------------

```                               

## Properties of Constructors
```
(1) Has the same name as the class.

(2) No return type (not even void).

(3) Called automatically at object creation.

(4)Used for initial assignment of instance variables.

```

## Types of Constructors

### Default Constructor
```
Has no parameters.

If we don’t write any constructor, Java provides a default one.
```
```java
public Person() {
    System.out.println("Default Constructor");
}
```
## Parameterized Constructor
```
Accepts parameters to initialize instance variables.

```

```java
public Person(String name, int id) {
    this.name = name;
    this.id = id;
}
```

## Copy Constructor
```
Copy Constructor creates a copy of an existing object of the same class. Parameter is usually another object of the same class.
```
```java

public Person(Person other) {                // Copy constructor: takes another Person object as input
    this.name = other.name;                  // Copy 'name' from the given object
    this.id = other.id;                      // Copy 'id' from the given object
}

public static void main(String[] args) {
    Person p1 = new Person("John", 1);   // Normal constructor
    Person p2 = new Person(p1);          // Copy constructor → p2 is a copy of p1
}

```


## Constructor Overloading
```
Multiple constructors with same name inside a class but with different parameter lists.
```
```java

public Person() { }                     // Default
public Person(String name) { }          // 1 parameter
public Person(String name, int id) { }  // 2 parameters
```
## Constructor Chaining

```
When one constructor calls another constructor using this() or super(), It is called constructor chaining.

When we call one constructor inside another constructor, It should be the first line.

this() – calls another constructor in the same class.

super() – calls a constructor from the parent class.

```
```java

public Person(String name, int id) {
    this(); // Calls default constructor
    this.name = name;
    this.id = id;
}
```
## What is the benefit of Constructor overloading?
```
We want to give flexibility when creating objects :

    > Sometimes we may only know the name.

    > Sometimes both name and id.

```
## Private Constructors - why we need private constructors?
```
When we make a constructor private - we cannot create object outside the class.

Used to restrict object creation from outside the class.

commonly used in:

Singleton design pattern (only one object allowed).

Utility/helper classes (e.g., Math class in Java) to prevent object creation.

When we make a constructor public - we can create object outside the class.
```

```java

private Person() { 

}

```
## Code Execution - Constructor 

```java
1. class Student {
2.     String name;
3.     int age;
4. 
5.     Student(String name, int age) {         // Constructor
6.         this.name = name;  // Assign parameter to instance variable in Heap
7.         this.age = age;
8.     }
9. 
10.    public static void main(String[] args) {
11.        Student s = new Student("Neil", 10); // Object creation - constructor is called
12.    }
13. }

```
## Execution Steps: How Constructor Assigns Values to Instance Variables

1. main() starts in Stack memory.
   - Program begins with main method.
   - main() is loaded into the Stack memory.

```
      +----------------------+
      | Stack                |
      | -------------------  |
top ->| main()               |
      |                      |
      +----------------------+
```

2. Reference variable s created in Stack.
   - Code: Student s = new Student("Neil", 10);
   - s is a reference variable stored in the Stack.
   - It will point to the Student object in the Heap.
   - new Student(...) creates an object in Heap > new keyword allocates memory in Heap.
   - Instance variables (name, age) are created with default values.

  ``` 
Step 2: new Student("Neil", 10) creates object in Heap

+----------------------+        +-------------------------------+
|        Stack         |        |              Heap             |
| -------------------  |        | ----------------------------  |
| main()               |        | Student object @777           |
|   s -> 777 --------+--------->|   name = null                 |
|                      |        |   age  = 0                    |
+----------------------+        +-------------------------------+


```
3.  Constructor is called, when the obj is created → parameters go to Stack.
   - Constructor Student(String name, int age) runs.
   - A stack is created for the constructor.
   - Parameters ("Neil", 10) are stored as local variables in Stack.
```

+----------------------+        +-------------------------------+
|        Stack         |        |              Heap             |
| -------------------  |        | ----------------------------  |
| main()               |        | Student object @777           |
|   s -> 777 --------+--------->|   name = null                 |
| Student()            |         |   age  = 0                   |
|  local name="Neil"   |         |                              |
|  local age = 10      |         |                              |
+----------------------+        +-------------------------------+                                                       

```
4. Values copied from Stack to Heap's instance variables.
     this.name = name;   // assigns "Neil"
     this.age = age;     // assigns 10

   - The local variable 'name' in Stack (value = "Neil") is assigned to the instance variable 'name' in Heap.
   - The local variable 'age' in Stack (value = 10) is assigned to the instance variable 'age' in Heap.

```
+----------------------+        +-------------------------------+
|        Stack         |        |              Heap             |
| -------------------  |        | ----------------------------  |  Values copied from Stack → Heap instance variables
| main()               |        | Student object - 777          |
|   s -> 777 --------+--------->|  instance var: name = "Neil"  |
| Student()           |         |  instance var: age  = 10      |
|  local name="Neil"  |         |                               |
|  local age = 10     |         |                               |
+----------------------+        +-------------------------------+
```


5. When the Constructor finishes excecution→ local variables disappear.
   - Constructor  is removed from stack.
   - Local variables in Stack are gone.
   - Heap object remains with values updated.

6. Object remains in Heap, referenced by s in Stack.
   - s in Stack holds the reference (e.g., 777).
   - That points to the Student object in Heap.
   - Object lives as long as a reference exists.











