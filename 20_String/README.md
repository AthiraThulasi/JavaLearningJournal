# String

### A String is a sequence of characters.  Eg: "java". ( String should be enclosed in double quotes)

### String is a class from the java.lang package. It is a non-primitive data type .

## How to declare a String?

### 2 ways to declare a String - (1) Using String Literal and (2) Using new Keyword (String Object)

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
│   s2       │──────────────►│  "Java"(object)     │
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

**String literal is stored in a special memory called String Intern pool.**

**String Internpool lets us store only unique value (No duplicates) - Efficient memory usage.**

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



## String is an Immutable Class - What Does That Mean? How String Immutability Works?

String is an immutable class, which means that once a String object is created, its value cannot be changed. 

Any modification of a String results in the creation of a new String object, leaving the original one unchanged.

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

### Java compares objects in two ways:

### (1) Using the reference comparison operator  ==

### (2) Using the .equals() method


## How Reference Comparison Operator ( == )  Compare Primitives ?

>**For primitive types (like int, char, boolean, etc.), == compares the actual values stored in the variables, not memory addresses.**

```java 


int a = 10; // a is primitive type

int b = 10; // b is primitive type

System.out.println(a == b); // == compares values for primitives // true because both values are same. [ 10 == 10]

For Primitive types (like int, char, boolean)

Reference Comparison Operator ( == )compares actual values stored in the variable.

```

## How Reference Comparison Operator ( == ) Compares Non - Primitives ?

>**For non-primitive types, == compares the memory address (i.e., whether two reference variables point to the same object in memory)**

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

>**Used to compare contents of objects**

```java

String s1 = new String("Java");

String s2 = new String("Java");

String s3 = new String("JAVA");

System.out.println(s1.equals(s2));  // true  → same content (case matches)

System.out.println(s2.equals(s3));  // false → content is not the same (case difference - the uppercase and lowercase letters do not match.)

```
>**The .equals() method is case-sensitive.** 


```
System.out.println(s1.equals(s2)); // ✅ true → compares actual text inside // case sensitive
Why is String Non-Primitive?

Unlike primitive types (int, char, etc.), String is a class. So we can create object from a class.

Even when declared like a primitive (String name = "Athira";). It internally creates a String object.

We can use methods on String (e.g., .length(), .toUpperCase()) — which primitive types don’t support.

### Memory Allocation: String Literal vs Object

 ### String Literal

```java

String name = "Athira"; // String Literal
Stored in the String Intern Pool.
```

> If the same literal already exists, Java reuses the reference → memory efficient.

### String Object using new

```java

String name = new String("Athira");  //String Object
```
> A new object is created in Heap memory, even if the same literal exists in the pool.

Not memory efficient.

🧠 Purpose of String Pool
To save memory by reusing immutable string literals.

```
String name = new String("Athira")

Heap Memory
-------------
| "Athira" |    
-------------
```
String Constant Pool
----------------------
| "Athira" |    ← Created via: String name = "Athira";
----------------------

Stack Memory
-----------------------------
| name ─────────┐
|               ▼
|     Ref to String Intern Pool/Heap
-----------------------------

💡 Important Points
String is immutable (cannot be changed once created).

It stores references (not actual content) in the stack.

Java reuses existing literals via the String pool.

❓ Interview Tip
Q: What’s the difference between String name = "Athira"; and String name = new String("Athira");?

A:

The first reuses the literal from the pool (SCP).

The second creates a new object in heap memory, even if the same string exists.

String is an Immutable Class in Java
Java String objects are immutable, meaning their value cannot be changed once created.

🛡️ Why are Strings Immutable?
✅ Security (used in classloaders, URLs, file paths)

✅ Performance (due to String Pool reuse)

✅ Thread Safety (no accidental changes in multi-threaded programs)

✅ Hashcode Caching (for fast access in HashMap)

🔄 Example: String Immutability + Pool Reuse
java
Copy
Edit
class Demo {
    public static void main(String[] args) {
        int x = 10;
        int[] a = new int[3];
        a[0] = 10;
        a[1] = 20;
        a[2] = 30;

        String name1 = "Jatin";
        String name2 = "Jatin"; // ✅ Same value, reused from pool
        String name3 = name1 + "123"; // 🔄 Creates new String
    }
}
name1 and name2 point to the same object in the String Constant Pool

name3 is created fresh in heap because of concatenation (+)

🧠 Memory Diagram
vbnet
Copy
Edit
Stack Memory                       Heap Memory                      String Constant Pool
┌────────────┐                 ┌────────────┐                     ┌──────────────┐
| name1 ─────┼────────┐        |   [0] 10    |                    |  "Jatin"     |
| name2 ─────┤        │        |   [1] 20    |                    └────┬─────────┘
| name3 ─────┘        │        |   [2] 30    |                         │
                      ▼        └────────────┘                         │
                   "Jatin"  ◄─────────────────────────────────────────┘
                      ↑
           (Shared between name1 & name2)
           
          name3 → "Jatin123" (New Object in Heap)
✅ String Pool (Intern Pool)
Java maintains a pool of strings to save memory.

If the same literal is reused, Java assigns the same reference.

🔍 Even if two variables use the same value, only one copy is created in the pool.

💥 Strings are Immutable
❌ Can't modify after creation.

Operations like concatenation, replace, etc., return new objects.

🔁 Mutable Alternatives
Class	Mutable	Thread-Safe
String	❌	✅
StringBuilder	✅	❌
StringBuffer	✅	✅

🔍 String Comparison
Use .equals() to compare content.

Use == to compare references.

java
Copy
Edit
String a = "hello";
String b = new String("hello");

System.out.println(a == b);        // false → different objects
System.out.println(a.equals(b));   // true  → same content


== vs .equals() in Java
Operator	Compares	Used With
==	References / memory address (for objects)
Value (for primitives)	Objects & Primitives
.equals()	Actual content/value	Objects only (like String)

📌 Example: Comparing Strings with ==
java
Copy
Edit
public class StringDemo {
    public static void main(String[] args) {
        int x = 10;
        int y = 10;

        System.out.println(x == y);  // ✅ True → primitive comparison → 10 == 10

        String name1 = "Athira";     // 🔁 Stored in String pool
        String name2 = "Athira";     // 🔁 Reuses same pool reference
        String name3 = "athira";     // 🔁 Different string, different reference

        System.out.println(name1 == name2);  // ✅ True → same reference in pool
        System.out.println(name1 == name3);  // ❌ False → different reference
    }
}
🧠 Explanation:
✅ For Primitives:
java
Copy
Edit
x == y  → compares values directly → 10 == 10 → ✅ true
❌ For Objects:
java
Copy
Edit
name1 == name2 → compares **memory address**
→ both refer to same pool location → ✅ true

name1 == name3 → different string literal → different address → ❌ false
🔎 Case Sensitivity with .equals()
java
Copy
Edit
System.out.println(name1.equals(name3)); // ❌ false → "Athira" ≠ "athira"
equals() is case-sensitive.

Even though name1 and name3 have similar letters, Java treats "Athira" and "athira" as different values.