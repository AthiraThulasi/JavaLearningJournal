# String

A String is a sequence of characters, like "java".

String is a non-primitive data type and a class from the java.lang package.


# Why is String a Non-Primitive?

Unlike primitive types (int, char, etc.), String is a class.

Even when declared like a primitive (String name = "Athira";), it internally creates a String object.

We can use methods on it (e.g., .length(), .toUpperCase()) — which primitive types don’t support.

Memory Allocation: String Literal vs Object
✅ String Literal
java
Copy
Edit
String name = "Athira";
Stored in the String Constant Pool (SCP) or String Intern Pool.

If the same literal already exists, Java reuses the reference → memory efficient.

✅ String Object using new
java
Copy
Edit
String name = new String("Athira");
A new object is created in Heap memory, even if the same literal exists in the pool.

Not memory efficient.

🧠 Purpose of String Pool
To save memory by reusing immutable string literals.

🧵 Text-Based Memory Diagram
markdown
Copy
Edit
Heap Memory
-------------
| "Athira" |    ← Created via: new String("Athira")
-------------

String Constant Pool
----------------------
| "Athira" |    ← Created via: String name = "Athira";
----------------------

Stack Memory
-----------------------------
| name ─────────┐
|               ▼
|     Ref to SCP/Heap
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