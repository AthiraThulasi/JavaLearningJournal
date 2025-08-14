# This Keyword

```
This keyword is used to differentiate local variables with instance variables when they have the same name.

```

### Student Class

```java

1. package com.student.management.system.oops;  //  Package hierarchy: com (domain) → student → management → system → oops


2. public class Student {    // Student is the class name
3.     
4.     private int age;                    // Instance variables (fields) — stored on the heap as part of the object creation                                  
5.     private int rollNumber;
6.     private double marksObtainedInEnglish;        // variables created inside the class → instance variables 
7.     private String name;                          // instance variables are properties of class
8.     private double marksObtainedInMaths;          // instance variables are always assigned with default values when created
9.     private double marksObtainedInScience;
10.    private String grade;

11. public String getName(){.     // Getter: returns the student's name
12.    return name;
}
13. public void setName() {.     // setname - To assign name
14  this.name = name;            // assigning value from the method parameter 'name' to the instance variable 'name'

15.   }
16.  
17. public void setRollNumber(int rollNumber){ // Setter with validation: only accept positive roll numbers
18.   
19.     if(rollNumber >=1)                    // validation inside setter method
20.          this.rollNumber = rollNumber;
21.   }
22.   else{
23.     System.out.print("Invalid roll number");
24.     }      
25.                   // Functionality → task / Non - static Method - which performs calculation of marks
26.    public void calculateTotalMarks() { // Method name should describe the action it performs
27.        double totalMarks = marksObtainedInEnglish + marksObtainedInMaths + marksObtainedInScience;
28.        System.out.println("Total Marks Obtained: " + totalMarks); // print the result
29.    }
30. }

```

### Runner Class

```java


1. package com.student.management.system.oops;

2. public class Runner {                   // Class that contains the main method
3.     public static void main(String[] args) {  // Entry point of the program
4.       
5.         
6.         Student s1 = new Student(); // Object in Heap, reference (s1) in Stack

7.           s1.setName("Joe")// setmethod to set name
8.           s1.setRollNumber(-10);

9.         
10.         // Accessing instance variables
11.        System.out.println(s1.getname()); // Prints 'null' (default value)
12.        System.out.println(s1.getage());  // Prints 0 (default value)
13.    }
14. }

```

## Program Excecution
```
 Java executes code line by line starting from the class that contains the main() method.

 The main() method is the program’s entry point and runs first when the application starts.

```
## Line 1 (Runner Class): 
```
package com.student.management.system.oops - Class "Runner" belongs to this package.

```
## Line 2 (Runner Class) :

```

public class Runner {  

    Runner is a public class (public is called access modifier - public is a keyword in java)

    {  - opening braces of class - It is the entry point of a class.
        
```
## Line 3 (Runner Class):
```
public static void main(String[] args) > main method

For java to excecute the runner class, It should go inside main method.

Main method is excecuted in stack

```
## Line 6 (Runner Class):

```
Student s1 = new Student();

RHS : new Student();

Java executes RHS first → new Student()

new keyword = always creates a new object in the heap.

A new object is created in heap memory.

When an object is created in the heap, 3 things happen in order:

      Step 1: The Student class is loaded into memory called Method Area.

                 Method Area - Stores class-level information — not object data. 
                 Method Area is part of JVM memory from the start, but it’s empty until classes are loaded.
                 class loading into the Method Area happens only the first time when we use that class in our program. Class loading is done by class loader

      Step 2: Instance variables for that object are created in heap and initialized with default values (e.g.int = 0)- say object's hashcode is 777.

      Step 3: Constructor is called.

 
If no constructor is defined, Java provides a default no-arg constructor (dummy constructor) and executes it.

The object’s memory address (e.g.777 or a hashcode) is created internally. 


Now, java excecutes the left side - 

LHS : Student s1

Student is the data type and s1 is a reference variable stored in the stack.

s1 holds the address/hashcode (777) that points to the object in heap.

```
```

         Stack Memory                      Heap Memory
+---------------------------+      +-----------------------------------+
| main()                    |      |  777  (Student object)            |
|                           |      |  +---------------------------+    |
| s1 ---> 777 --------------+----->|  name         = null           |  |  these are all private instance variables which can't be accessed outside the class
|                           |      |  age          = 0              |  |
|                           |      |  rollNumber   = 0              |  |
|                           |      |  marksEnglish = 0              |  |
|                           |      |  marksMaths   = 0              |  |
|                           |      |  marksScience = 0              |  |
|                           |      |  grade        = null           |  |
+---------------------------+      +---------------------------+---+
```


## Setter Method  – How It Works
```
Why We Need Setters ?

Instance variables are usually declared as private to protect them from direct access outside the class, This prevents illegal value assignments from outside.

But then, how do we assign values to these private variables from outside?

By using setter methods - To assign values

Getter methods - For reading values.
```
## Line 7 (Runner Class):

```java

s1.setName("Joe"); //  Control goes to Line 13 in Student class - setName method()

```
```
Stack and Heap During setName("Joe") Execution - before the assignment to heap variable happens

+----------------------------+          +-------------------------------+
|        Stack               |          |              Heap             |
+----------------------------+          +-------------------------------+
top-> | setName("Joe")        |         |                               |
      |  local var: name="Joe"|         |                               |
      |  this -> 777          |         |                               |
+----------------------------+          |                               |
| main()                     |          |                               |
| s1 -> 777 -----------------+-------->   Student object                |
+----------------------------+          +-------------------------------+

```
```
s1 is a reference variable in the stack pointing to a Student object in the heap.

When we call s1.setName("Joe") > Java pushes the setName method into the stack for execution. (All methods are always executed inside the stack)

top points to setName() as its the top most in stack - and the method currently running.

s1.setName("Joe") tells Java: Look at the object that s1 is pointing to. Go into its class (Student) and execute the method named setName.

At the moment setName starts running, the parameter variable "name" is CREATED INSIDE STACK of setName and stores the value "Joe". 

(Method parameters are local variables and are always stored in the stack.)

Remember - When we created the "Student" object -  a "name" variable is created in heap.

```

## Two Variables Named "name"
```

So now, we have two different variables with the same name - "name":

           (1) One in the stack → method parameter.

           (2) One in the heap → instance variable of the object.

There is no conflict because they are in different memory locations.

```

## Line 13 (Student Class):Role of "this" Keyword !

```

// when java excecutes >> s1.setName("Joe") >> Control goes to Line 13 in Student class -  setName method()

"This" keyword helps to differentiate local variables with instance variables.

To assign the value from the local variable (stack) to the instance variable (heap), we use - "this" keyword.

"this" keyword - always refers to instance variable.

```
```java

                            // s1.setName("Joe") --> Control goes to Line num 13 in Student class
13.  public void setName(String name) { //  name in parameter is a local varaible
14.    this.name = name;  // value of local variable is assigned to instance variable
    
    // "this.name" → instance variable in heap
    // name = local variable
15. }
```
```
this.name → refers to the instance variable in heap. [with "this" keyword - It explicitly tells java that we are referring to the instance variables of the class]

name → refers to the local variable in stack.
```
## What If We Skip "this"?
```java
public void setName(String name) {
    name = name; // Both refer to the local variable → does nothing!
}
```
```
Java will confuse both variables as local variables.

The instance variable will never get updated.

```
## After this.name = name -> How it looks in memory?
```
+----------------------------+          +-------------------------------+
|        Stack (             |          |              Heap             |
+----------------------------+          +-------------------------------+
| setName("Joe")             |          |  777 (Student object)         |
|  local var: name = "Joe"   |          | +-------------------------+   |
|  this -> 777               |          | | name = "Joe"            |   |
+----------------------------+          | | (instance variable)     |   |
| main()                     |          | +-------------------------+   |
| s1 -> 777 -----------------+-------->   Student object                |
+----------------------------+          +-------------------------------+


```

## Line 15 (Student Class)
```
 
} – Closing brace for the setName method.

At this point, Java pops the setName method frame out of the stack.

Now, only main() remains in the stack, and top points back to main().
```
## Line 8 (Runner Class)

```java

 8. s1.setRollNumber(-22);// Control goes to Line 17 in student object

 ```

 ```
s1 is a reference variable in the stack pointing to student object in the heap.

When we call setRollNumber(-10), Java pushes the setRollNumber method into the stack for execution.(setRollNumber is a method - methods are always excecuted inside stack)

s1.setRollNumber(-10) tells Java - Look at the object s1 is pointing to, Go into its class (Student) and execute the method named setRollNumber.[Line 17 in Student class]

Roll num (local variable) is set as -10 inside the stack .
```
## Line 17 (Student Class) - How validation works inside setter?

``` java
17. public void setRollNumber(int rollNumber){
18.  
19.     if(rollNumber >=1)
20.          this.rollNumber = rollNumber;
21.   }
22.   else{
23.     System.out.print("Invalid roll number");
24.     }      
```
```
java will excecute Line num 17 - java checks the validation written inside the setRollNumber method

(1) Is rollNumber > 1? OR (2) Is rollNumber = 1  ? 

Both condition are false >> So java is not going to excecute 

So this.rollNumber = rollNumber >> assignment won't happen and java will excecute else block - and print - Invalid roll number.

"RollNumber" in heap will remain 0 as its default value.

When wrong values are rejected in a setter, the instance variable keeps its old value — which could be the default value if no valid assignment has been made yet.


```

## Line 24 (Student Class)
```
    }  - closing brace

    end of setName method

    java pops out the setName method rom the stack.

    We only have main() inside the stack and top will point to the main()
```