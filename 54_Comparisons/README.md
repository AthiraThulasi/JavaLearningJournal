# Comparisons

## (1) Local Variable Vs Instance Variable

```

| Feature                   | Local Variable                                         | Instance Variable                                                    |
|-------------------------- |--------------------------------------------------------|----------------------------------------------------------------------|
| Declaration               | Declared inside a method or block                      | Declared inside a class                                              |
| Scope                     | Only accessible within the method/block where declared | Accessible by all methods of the class (via object)                  |
| Memory Allocation.        | Stored in stack memory                                 | Stored in heap memory                                                |
| Default Value             | No default value, must be initialized before use       | Default values (e.g., null, 0, false)                                |
| Lifetime.                 | Exists only during method execution                    | Exists as long as the object exists                                  |
| Access Modifier.          | No access modifier                                     | Can have access modifiers (public, private, protected)               |
| Storage Location          | Stored in the stack                                    | Stored in the heap (object)                                          |
| Connection to Heap.       | No connection to heap                                  | Reference variable in the stack points to the object in the heap     |
-------------------------------------------------------------------------------------------------------------------------------------------------------------
```

```java

    // Instance variables declared inside class - reference variable (name,age,address) is stored in stack and points to object (john,25,)in stack
    public class Person {

    // Instance variables with different access modifiers
    private String name = "John";  // Private instance variable
    public int age = 25;           // Public instance variable
    protected String address = "123 Main St";  // Protected instance variable

    // Method to display local variable - stored in stack
    public void displayInfo() {
        // Local variable (no access modifier)// 
        int x = 10; //  local variable

        // Main method to run the program
    public static void main(String[] args) {
        // Creating an object of Person class
        Person person = new Person(); 
      
    }
}
```
```
+-------------------------------------------+        +-------------------------------------------+
|       Stack   -  Local Variable           |        |    Heap - Instance Variables              |
+-------------------------------------------+        +-------------------------------------------+
| Reference variable: person -> 0x12345     |  --->  | Object: Person                            |
| Local variable: x = 10                    |        |  - name = "John"                          |
+-------------------------------------------+        |  - age = 25                               |
                                                     |  - address = "123 Main St"                |
                                                     +-------------------------------------------+
                                                     |  (The reference 'person' in the stack     |
                                                     |   points to the memory address of the     |
                                                     |   object in the heap)                     |
                                                     +-------------------------------------------+
```

## Key points
```
 Local variables must be explicitly initialized before they can be accessed. If they are not initialized, trying to access them will lead to a compiler error.

 Instance variables do not require initialization explicitly, they will be initialized to default values when the object is created. 
```
```java

int x;  // Declaring local variable without initializing

System.out.println(x);  // Error: variable x might not have been initialized

```


## (2) Constructors Vs Setters


| Constructor                                                                          | Setter                                                                         
| -------------------------------------------------------------------------------------| ------------------------------------------------------------------------------ |
| Special method with the SAME NAME AS CLASS                                           | NORMAL METHOD follows camelCase naming.                                        |
| Has NO RETURN TYPE                                                                   | Has a return type (commonly `void`).                                           |
| Called ONCE during object creation.                                                  | Can be called **multiple times** after object creation.                        |
| Used to INITIALIZE instance variables.                                               | Used to UPDATE/CHANGE instance variables.                                      |
| If only constructors are used → object is **Immutable** (values fixed after creation).| Using setters makes object **Mutable** (values can be updated).                |
| Can be **overloaded** (multiple constructors with different parameters).             | Setters are **not overloaded**, but multiple setters exist (one per variable). |
| Values are assigned only **once** when the object is created.                        | Values can be updated **any number of times**.                                 |

------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Constructor Example

```java
class Person {
    String name;

    Person(String name) {
        this.name = name;
    }
}

Person p1 = new Person("John");
// Name fixed, cannot change later
```

### Setter Example

```java
class Person {
    private String name;

    public void setName(String name) {
        this.name = name;
    }
}

Person p1 = new Person();
p1.setName("John");  // can update later

```

## (3) this Vs super Keyword

```

| Aspect                   |           this                                                                   |                super      
| ------------------------ | -------------------------------------------------------------------------------------------------------------------                         | 
|   Meaning                | Refers to the current object                                                     | Refers to the *parent (super) class*                     |
|   Constructor Call       | Used to call another constructor in the same class.                              | Used to call a constructor of the parent class.          |
|   Variable Access        | Differentiates local variables from instance variables when they have same name  | Accesses parent’s variables (if not private)             |
|   Method Access          | Can call current class methods                                                   | Can call parent class methods (even if overridden)       |
|   Constructor Chaining.  | Used for chaining within the same class                                          | Used for chaining between child → parent                 |
|   Restrictions           | Must be the first statement in the constructor                                    | Must be the first statement in the child constructor    |
```

## this

```java
class Student {
    private String name;

    // Constructor 1
    Student() {
        this("Unknown"); // calls another constructor in SAME class
    }

    // Constructor 2
    Student(String name) {
        this.name = name; // differentiates local var and instance var
    }

    void display() {
        System.out.println("Name: " + name);
    }
}

public class Runner {
    public static void main(String[] args) {
        Student s1 = new Student();
        s1.display(); // Name: Unknown
    }
}
```

## Understanding variable search in java

```java
class Person {
    protected int x;

    Person(int x) {
        this.x = x;
    }
}

class Student extends Person {
    private int y;

    Student(int x, int y) {
        super(x);
        this.y = y;
    }

    void display() {
        int x = 99; // local variable shadows parent’s x
        System.out.println(x);   // Case 1
        System.out.println(this.x); // Case 2
        System.out.println(super.x); // Case 3
    }
}

public class Runner {
    public static void main(String[] args) {
        Student s = new Student(10, 20);
        s.display();
    }
}


public class Runner {
    public static void main(String[] args) {
        Student s1 = new Student(10, 20);
        s1.display();
    }
}
```

## How Java Searches for x ?

```java

display()
System.out.println(x):

```

## First Priority
```
When the compiler sees System.out.println(x) >> java first search whether a local variable x exists inside the current method?

If an x exists in the current method (display), that shadows everything else.

In the above example, int x = 99; will be printed for Case 1.
```
## Second priority 
```
If local variable is not present, java looks for Instance variable in the same class
```
## Third priority → Parent class variable
```
If not found in current class, Java climbs up the inheritance chain to check the parent (Person).

That’s why this.x or super.x points to the value initialized in the parent constructor (10).

```

## output

```
99       // local variable shadows everything
10       // parent's x (through this.x)
10       // parent's x (through super.x)
```

## If Parent and Child Have Same Method - How to Call Parent’s One?
```java
  class Parent {
    void display() {
        System.out.println("Parent display()");
    }
}

class Child extends Parent {
    @Override
    void display() {
        System.out.println("Child display()");
        super.display(); // calls parent’s version
    }
}

public class Test {
    public static void main(String[] args) {
        Child c = new Child();
        c.display();
    }
}
```

## To call child’s version :

```
When a child class overrides a method, calling display() on the child object will run the child’s method.

display()
```
## To call parent’s version :
```
To explicitly run the parent’s method, use super.display() inside the child method.

super.display()

```