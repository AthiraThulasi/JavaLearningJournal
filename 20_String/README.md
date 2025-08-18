# String
```
A String is a sequence of characters.  Eg: "java". ( String should be enclosed in double quotes)
 
String is a class from the java.lang package. It is a non-primitive data type .
```
## How to declare a String?
```
 2 ways to declare a String - (1) Using String Literal and (2) Using new Keyword (String Object)
```

## (1) Using String Literal

``` java
S in caps  non -primitive variable 
↑           ↑
String    name  =  "Every Second Counts";
   ↑        ↑              └───────► String Literal                    Literal is a fixed value assigned to a variable.
   │        │                
        
   │        └───────► reference var   // Stores memory address (reference) — acts as unique identification to locate the object
   ↓                       
non-primitive Datatype   
                  
```

## (2) Using new Keyword (String Object)


We can create a String Object using the **`new`** keyword. [ new keyword creates object in Heap Memory]

```java

1. String s1 = new String("Java");
2. String s2 = new String("Java");

```
```
Stack Memory                      Heap Memory                         
┌────────────┐               ┌────────────────────┐                
│   s1       │──────────────►│  "Java" (object)   │                
└────────────┘               └────────────────────┘               
┌────────────┐               ┌────────────────────┐
│   s2       │──────────────►│  "Java"(object)    │
└────────────┘               └────────────────────┘

reference variables
```
### What happens in here?

```java

new String("Java") creates a new object in the Heap.

One object is created in the heap for s1.

Another separate object is created in the heap for s2.

Each call to new creates a separate object in heap memory - meaning s1 and s2 point to different memory addresses, even though their content is the same.
```

## Where is this String Literal stored in Memory?
```
String literal is stored in a special memory called STRING INTERN POOL.

STRING INTERN POOL lets us store only unique value (No duplicates) - Efficient memory usage.

```
## How Java Stores String Literals in the Intern Pool ?

```java

1.   public static void main(String[] args()){

2.   String Name1 = "Alexa";
3.   String Name2 = "Alexa";   // Sring Literal is stored in String Intern Pool

}
```

## Excecution Flow

```java
Stack Memory:                              String Intern Pool:
+----------+                               +---------+
| main()   | TOP                           |   777   | <- (Memory Address)
|          |                       |---->  | "Alexa" |
|  777     | name1 (Reference) ----|       +---------+
|----------|                                    ^
|  777     | name2 (Reference) -----------------|
+----------+
```
```java
Program Execution Starts from main() >> The main method is loaded into the stack memory (Top of the Stack).

>> Line 2: String Name1 = "Alexa";

Java checks if "Alexa" is already present in the String Intern Pool - NO, it is not present >> so "Alexa" is added to the String Intern Pool.

A reference is created for Name1 in the stack (777), pointing to the memory address of "Alexa" (777) in the String Intern Pool.

>> Line 3: String Name2 = "Alexa";

Java checks if "Alexa" is already present in the String Intern Pool. >> YES, it is already there.

Java assigns the same reference (memory address - 777) to Name2, pointing to the same memory location as Name1, as String Intern Pool do not allow duplicates.

```

## What is the purpose of String Intern Pool ?
```
To save memory by reusing immutable string literals.
```

## String is an Immutable Class - What Does That Mean? How String Immutability Works?
```
String is an immutable class, which means that once a String object is created, its value cannot be changed.

Any modification of a String results in the creation of a new String object, leaving the original one unchanged.
```
```java

1.   public static void main(String[] args()){

2.   String Name1 = "Alexa";
3.   String Name2 = "Alexa";   // Sring Literal is stored in String Intern Pool
4.   String Name1 = Name1 + Name2; // Concatenation operation - adding 2 strings.
}
```
## Excecution Flow


```java

Stack Memory:                                String Intern Pool:
+----------+                                   +---------+
| main()   | TOP                            |     888       | <- (Memory Address)
|          |                       |---->   | "Alexa Alexa" | name1 = name1 + name2 
|  888     | name1 (Reference) ----|           +---------+
|----------|
|  777     | name2 (Reference) --------------------| 
|----------|                                       |
                                                   |
                                                +---------+
                                                | "Alexa " | 777   String Intern Pool
                                                +---------+

```

```java

Line 2: String Name1 = "Alexa";

The string "Alexa" is stored in the String Intern Pool. The reference Name1 now points to the memory address of "Alexa" in the intern pool.

Line 3: String Name2 = "Alexa";

Since "Alexa" is already in the String Intern Pool, Name2 points to the same memory address as Name1.[ shown in image 1]

Line 4: Name1 = Name1 + Name2; //Alexa Alexa

This line performs String concatenation, adding Name1 ("Alexa") and Name2 ("Alexa") - The result is "Alexa Alexa".

Java checks if "Alexa Alexa" already exists in the String Intern Pool. Since it doesn't, Java adds "Alexa Alexa" to the pool.

>> Important: Now, Name1 points to a new memory reference 888 (where "Alexa Alexa" is stored) and the previous reference (777) pointing to "Alexa" is removed.

```

## How Does Java Compare Objects?
```
Java compares objects in two ways:

 (1) Using the reference comparison operator  ==

 (2) Using the .equals() method

```
## How Reference Comparison Operator ( == )  Compare Primitives ?
```
>For primitive types (like int, char, boolean, etc.), == compares the actual values stored in the variables, not memory addresses.
```
```java 


int a = 10; // a is primitive type

int b = 10; // b is primitive type

System.out.println(a == b); // == compares values for primitives // true because both values are same. [ 10 == 10]

For Primitive types (like int, char, boolean)

Reference Comparison Operator ( == )compares actual values stored in the variable.

```

## How Reference Comparison Operator ( == ) Compares Non - Primitives ?
```
For non-primitive types, == compares the memory address (i.e., whether two reference variables point to the same object in memory)
```
``` java

String s1 = new String("Java"); //  s1 -  reference variable

String s2 = new String("Java"); // s2 - reference variable

System.out.println(s1 == s2); //  false → different memory addresses

s1 and s2 are reference variables in the stack, each pointing to separate objects (i.e., different memory addresses) in the heap, both containing the same content: "Java".

```
```java

String s3 = "Java"; // s3 is stored in the String Intern Pool

String s4 = "Java"; // s4 points to the same object as s3, since the content is identical

System.out.println(s3 == s4); // true → both refer to the same object in the String pool

```
## .equals() method
```
Used to compare contents of objects**

The .equals() method is case-sensitive.** 
```
```java

String s1 = new String("Java");

String s2 = new String("Java");

String s3 = new String("JAVA");

System.out.println(s1.equals(s2));  // true  → same content (case matches)

System.out.println(s2.equals(s3));  // false → content is not the same (case difference - the uppercase and lowercase letters do not match.)

```

## What is hashCode() ?

```
Every object in Java has a hashCode() method (inherited from Object class, which is the parent of all classes in java).

It returns an integer value that represents the object’s hash .

>  For Strings: The String class OVERRIDES hashCode() to return a VALUE based on its CONTENT, NOT MEMORY LOCATION

```
```java

String s1 = "Athira";

String s2 = new String("Athira");

System.out.println(s1.equals(s2));    //  true → same content

System.out.println(s1.hashCode());    // e.g., 63365123

System.out.println(s2.hashCode());    // same as s1 → 63365123

Even though s1 and s2 are different objects in memory, their hashCodes match because their CONTENTS ARE EQUAL.

```
## Why is String Non-Primitive?

```

Unlike primitive types (int, char, etc.), String is a class. So we can create object from a class.

Even when declared like a primitive (String name = "java";). It internally creates a String object.

We can use methods on String (e.g., .length(), .toUpperCase()) — which primitive types don’t support.

```

## Memory Allocation: String Literal vs String Object

### String Literal

```java

String name = "Athira"; // String Literal

Stored in the String Intern Pool.

> If the same literal already exists, Java reuses the reference → memory efficient.
```


### String Object using new

```java

String name = new String("Athira");  //String Object 

A new object is created in Heap memory, even if the same literal exists in the pool > Not memory efficient.

```
## How It Looks Internally In Memory?

```
Heap Memory
-------------
| "Athira" |   ← created by new
-------------

String Intern Pool
----------------------
| "Athira" |  ← already created if not present
----------------------

Stack Memory
-----------------------------
| name ─────────┐
|               ▼
|     Reference to Heap
-----------------------------

```

## Why do we prefer String Literals over String Objects?
```
String Literals - We prefer String literals because they are stored in the String Pool,which helps Java reuse existing strings instead of creating new objects.

This improves memory efficiency and performance.

String Object - Using new String() creates unnecessary objects in Heap memory,so it is generally avoided unless we explicitly need a new instance.

```


## String Summary (Quick Revision)
```

(1) String is immutable → Once created, it cannot be changed.

(2) String literals are stored in the String Intern Pool.

(3) Using new String("abc") creates a new object in Heap memory.

(4) .equals() compares content.

(5) == behaves differently:

        > For primitives: compares actual values
        10 == 10 → true

        > For objects: compares memory/reference
        "abc" == new String("abc") → false

(6) .hashCode() returns an int based on content (overridden in String class)

(7) .hashCode() checks the content

(8) Different memory → == returns false

(9) Strings are thread-safe by nature due to immutability


```

## Brain Teasers !

```java

public class StringCheck {
    public static void main(String[] args) {
        String a = "Be Consistent";
        String b = new String("Be Consistent");

        System.out.println(a == b);          // ?
        System.out.println(a.equals(b));     // ?
        System.out.println(a.hashCode());    // ?
        System.out.println(b.hashCode());    // ?
    }
}


Questions:

(Q1) a == b → Does it compare references or values?

(Q2) a.equals(b) → Will it return true or false? Why?

(Q3) a.hashCode() and b.hashCode() → Will they match?

```
```java

public class EqualityCheck {
    public static void main(String[] args) {
        int a = 10; // primitive
        int b = 10;

        System.out.println(a == b);  // ?

        String s1 = "Value your time";
        String s2 = new String("Value your time");

        System.out.println(s1 == s2);  // String object      // ?
        System.out.println(s1.equals(s2));   // ?
    }
}

(Q1) What will be the output of a == b? Why?

(Q2) Are s1 and s2 referring to the same object in memory? Why or why not?

(Q3) What does s1 == s2 compare? Content or memory reference?

(Q4) Why does s1.equals(s2) return true even though s1 == s2 is false?

(Q5) How many objects are created in memory when we write new String("Value your time")?

(Q6) Why does == work differently for primitives and String objects?

```


