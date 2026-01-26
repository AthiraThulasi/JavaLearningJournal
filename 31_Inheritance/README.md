# Inheritance

```
Inheritance teaches  - ' IS A ' relationship.

Inheritance is the relationship between similar entities.

Inheritance is a parent–child relationship, where the child class (subclass) can acquire
the properties and behaviors (variables and methods) of the parent class (superclass) WITHOUT CREATING THE OBJECT.

Parent: Person has name, age.

Child: Student → automatically gets name, age from Person without rewriting.

```

## Why Inheritance?
```
Reduces code duplication

Improves maintenance

Represents a parent–child relationship between classes.

```

## Inheritance - Parent & child Relationship

```
CHILD uses KEYWORD "extends" to inherit parent's properties.

Parent is called SUPER CLASS

Child is called SUB-CLASS

```
```java

class Parent {
    // variables & methods
}

class Child extends Parent {
    // can use parent's non-private variables & methods
}
```

## Important Terms

```
Superclass (Parent Class) → the class whose properties are inherited.

Subclass (Child Class) → the class that inherits the parent’s properties.

Child can only access non-private features of the parent.

```

## Types of Inheritance

## Single Inheritance - One child inherits from one parent.

```
Class A (Parent)
      | 
      | extends
      |
Class B (Child)
```
```java

class A 
{
    
}

class B extends A 
{

 }
```
## Multilevel Inheritance

```
Class A (Grandparent)
        |
        | extends
        |
Class B (Parent)
        |
        | extends
        |
Class C (Child)

```

```java
class A { }

class B extends A { }

class C extends B { }
```
##  Multiple Inheritance  (Not Supported in Java)
```
   Class A        Class B
       \          /                    Reason: Ambiguity
        |        |                      Solution: Use Interfaces if multiple inheritance is needed.
        \        /
         \      /
          Class C  ← Error

```
## How to define instance variables in parent class when a child class extends the parent?

```
We use "protected" as access modifier, so that child classes can directly access parent class variables, while still keeping them hidden from the outside world.

```
```java
// Parent class
class Person {
    // protected → accessible in child classes, but not outside the package
    protected String name;
    protected int age;
}

// Child class inheriting parent class
class Student extends Person {
    private int rollNo; // child’s own variable

}

```

## Constructor Chaining (with super())

```
If the parent class has a PARAMETERIZED CONSTRUCTOR:

       >> It is the job of the child class to call the parent's constructor with SUPER  keyword - It is called Constructor chaining.
       
       >> It ensures that the parent portion of the object is initialized first before the child’s own members are set.

When we create an object of child class → parent class constructor runs first, then child constructor.

This ensures the parent is always initialized before the child.

constructor chaining happens with 2 keywords

       > this keyword - calls constructor within the same class

       > super keyword - to call parent class constructor from child class constructor

```

## Class Student (child)  extends Person (parent)
```java
 1 class Person {
 2     protected String name;  protected int age;
 3
 4     // Constructor 1 (overloaded)
 5     public Person(String name) {
 6         this.name = name;
 7         this.age = 18;   // default
 8         System.out.println("Parent Constructor 1 (name only)");
 9     }
10
11     // Constructor 2 (overloaded)
12     public Person(String name, int age) {
13         this.name = name; this.age = age;
14         System.out.println("Parent Constructor 2 (name and age)");
15     }
16 }
17
18 class Student extends Person {
19     int rollNo;
20
21     // Child constructor → calls parent Constructor 2
22     public Student(String name, int age, int rollNo) {
23         super(name, age);   // super() → calls parent Constructor 2
24         this.rollNo = rollNo;
25         System.out.println("Child(Student) constructor called");
26     }
27
28     // Another Child constructor → calls parent Constructor 1
29     public Student(String name, int rollNo) {
30         super(name);   // super() → calls parent Constructor 1
31         this.rollNo = rollNo;
32         System.out.println("Child(Student) constructor called (via super(name))");
33     }
34 }

```
## Runner Class
```java

 1 public class Runner {
 2     public static void main(String[] args) {
 3         Student s1 = new Student("Athira", 25, 101); // → calls parent Constructor 2
 4         Student s2 = new Student("Neil", 202);       // → calls parent Constructor 1
 5     }
 6 }

```

## How constructor chaining works in the above code?

```java
Student s1 = new Student("Athira", 25, 101); 
```
```
Line num 3 in Runner class calls the Student constructor (String, int, int).

Inside it → super(name, age) is invoked (Line 23 in the Student class).

This triggers Parent Constructor 2 (String, int) (Line 12 in Person class).

"Athira", 25 are passed to parent.

After parent finishes, child constructor sets rollNo = 101.

Flow - Runner (line 3) → Student(String,int,int) → super(name, age) → Person(String,int)
```

```java
Student s2 = new Student("Neil", 202);
```
```
Calls the Student constructor (String, int).

Inside it → super(name) is invoked (Line 30 in the Student class).

This triggers Parent Constructor 1 (String) (Line 5 in Person class).

Parent assigns name = "Neil" and gives default age = 18.

After parent finishes, child constructor sets rollNo = 202.

Flow - Runner → Student(String,int) → super(name) → Person(String)
```
## Summary
```
Constructor chaining is shown where Student(String,int,int) chains to Person(String,int) via super(name, age) and Student(String,int) chains to Person(String) via super(name).

s1 → goes to Constructor 2 in parent because super(name, age) matches (String,int).

s2 → goes to Constructor 1 in parent because super(name) matches (String).

```

## 2 ways to do constructor chaining - super & this !

```
super() → In Inheritance, super() is used, if we want to call parent class constructor from the child class constructor.

this() → this keyword is used to do constructor chaining within the same class.

Note : 

this (without parenthesis) → Refers to the current object’s instance variables, usually when local variables or constructor parameters have the same name.

Example: this.name = name;


```

# Excecution - Class B (Superclass/Parent) & Class C (Sub-class/Child)

```java
------------------- B.java -------------------        ------------------- C.java -------------------
 1 package com.inheritance;                              1 package com.inheritance;
 2                                                       2
 3 public class B {                                      3 public class C extends B {
 4     private int x;                                    4     private int z;
 5     private int y;                                    5
 6                                                       6     public C(int x, int y, int z) {
 7     public B(int x, int y) {                          7         super(x, y);   // call parent constructor
 8         super();   // calls Object constructor        8         this.z = z;
 9         this.x = x;                                   9     }
10         this.y = y;                                  10
11     }                                                11     @Override
12                                                      12     public void add() {
13     public void add() {                              13         System.out.println(getX() + z);
14         System.out.println(x + y);                   14     }
15     }                                                15
16                                                      16     // inherits getX(), setX() from B
17     public int getX() {                              17
18         return x;                                    18 }
19     }                                                19
20                                                      20
21     public void setX(int x) {                        
22         this.x = x;                                  
23     }                                                
24 }                                                    
                                                  }

```
## Runner Class

``` java

 1 package com.inheritance;
 2
 3 public class Runner {
 4     public static void main(String[] args) {
 5         B b = new B(10, 20);
 6         b.add();
 7
 8         C c = new C(10, 20, 30);
 9         c.add();
10     }
11 }
```

## Excecution

```
Program execution begins from the main method inside the Runner class.
 
Line 4: Runner - Excecution happens in stack - main is loaded to mmry >> top points to main()

Line 5: B b = new B(10, 20);  > Java excecutes RHS First

         > object is created 
         > class is loaded into method area
         > instance variables r created
         > constructor is called

        > obj  B is created in heap mmry 
        > x & y - instance variables r created and initialized with default values

constructor is called and control goes to class B - Line 7

public B(int x,inty) - constructor's parameters x and y are local variables, created in stack memory

x and y in stack get values 10 and 20

this.x = x 

       > Here value of local variable x is passed to instance variable x.

       > value of local variable y is passed to instance variable y.

when the constructor finishes excecution - local variables r removed from stack n control goes to main().

Now java excecutes LHS - B is assigned a hashcode and is pointed towards onject in heap 


Next, control goes to class B - Line 13 - add ()

add() method is loaded in stack

       > (1) java first checks - Is there a local variable x and y - No.

       > (2) Then java checks - whether the class has instance variable x and y - yes 

   Java calculates x + y = 20


Now, control goes to Runner class > Line 8 > C c = new C(10, 20, 30) > Java excecutes RHS first

        > object is created 
        > class is loaded into method area
        > instance variables r created
        > constructor is called

        > obj C is created in heap mmry 
        > x, y and z - instance variables r created and initialized with default values

constructor is called and control goes to class C - Line 6 - parameterized constructor of C

Constructor is a method and it is excecuted in stack memory.

constructor's parameters x and y are local variables, created in stack memory

x,y and z are in stack get values 10 ,20 & 30.

this.x = x 

        > Here value of local variable x is passed to instance variable x.

        > Value of local variable y is passed to instance variable y

        > When the constructor finishes excecution - local variables r removed from stack n control goes to main().

Now java excecutes LHS - C is assigned a hashcode and is pointed towards onject in heap.
```
## Summary
```
Inheritance = relationship between similar entities

Use extends keyword to establish parent-child relationship

Only single & multilevel inheritance supported in Java

Multiple inheritance not supported → use interfaces

Constructor chaining ensures parent constructor always runs first

Child can access only non-private features of parent

```
## Relationship between A,B & C using Extends Keyword - Concept Check!
```java

----------------- A.java -------------------       ------------------- B.java ----------------          -------- C.java------------
 1 package com.inheritance;                          1 package com.inheritance;                           1 package com.inheritance;
 2                                                   2                                                    2
 3 public class A {                                  3 public class B extends A {                         3 public class C extends B {
 4     protected int x;                              4                                                    4     private int z;
 5     protected int y;                               5                                                    5
 6                                                   6     public B(int x, int y) {                       6     public C(int x, int y, int z) {
 7     public A(int x, int y) {                      7         super(x, y);                               7         super(x, y);   // call parent (B)
 8         super();                                  8     }                                              8         this.z = z;
 9         this.x = x;                               9                                                    9     }
10         this.y = y;                              10     public void add() {                            10
11     }                                            11         System.out.println(getX() + getY());       11     @Override
12                                                  12     }                                              12     public void add() {
13     public int getX() {                          13                                                    13.   System.out.println (getX()getY(z);
14         return x;                                14     public int getX() {                            14      }   
15     }                                            15         return super.getX();                       15
16                                                  16     }                                              16     public int getZ() {
17     public void setX(int x) {                    17                                                    17         return z;
18         this.x = x;                              18     public void setX(int x) {                      18     }
19     }                                            19         super.setX(x);                             19
20                                                  20     }                                              20     public void setZ(int z) {
21     public int getY() {                          21                                                    21         this.z = z;
22         return y;                                22     public int getY() {                            22     }
23     }                                            23         return super.getY();                       23 }
24                                                  24     }                                              
25     public void setY(int y) {                    25                                                   
26         this.y = y;                              26     public void setY(int y) {                      
27     }                                            27         super.setY(y);                              
28                                                  28     }                                              
29     @Override                                    29                                                  
30     public String toString() {                   30     @Override                                       
31         return "A [x=" + x + ", y=" + y + "]";   31     public String toString() {                      
32     }                                            32         return "B [x=" + getX() + ", y=" + getY() + "]";
33 } 
                                   
```


```                                                      ```                                                               ```
## Runner Class  for A , B & C                                                                            
```java                                                                                                                                                      
                                                                                                                                
1 public class ARunner {                                  public class BRunner {                                            public class CRunner {
2 public static void main(String[] args) {                public static void main(String[] args) {                          public static void main(String[] args) {
3 A a = new A(10, 20);                                    B b = new B(30, 40);  // calls A(int,int) via super()             C c = new C(50, 60, 70);
4 System.out.println(a);                                  b.add();              // prints ?                                 c.add();
5 System.out.println(a.getX());                           System.out.println(b); // calls B.toString()                      System.out.println(c.getZ())         
6 System.out.println(a.getY()); }                         }                                                                 System.out.println(c);}

}                                                              }                                                             }
                                                                                                                             
```                                                        
## Concept Check!                                                              
```    
1. When we run new C(10, 20, 30), in what order do the constructors of A, B, and C execute? Why?

2. Why must B(int x, int y) call super(x, y)? What happens if we remove it?

3. Since x and y are private in class A, how can class B and class C still access them?

4. What happens if you remove super(x, y) from B’s constructor?

5. In A(int x, int y), why do we write this.x = x; instead of super.x = x;?
   In which situations do we use this() and super() inside constructors?

6. Both B and C override add(). If we create C c = new C(1, 2, 3); c.add();, which add() executes, and why?

7. For System.out.println(c) where c is a C object, which toString() method is used?
   What if C does not override toString()?   

8. If z in C is private, can B access it directly? If not, how should B get its value?

9. How would you use this() to call one constructor of A from another constructor in the same class?
```



   


