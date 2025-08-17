# String Intern Method


 ## String Intern Pool Vs Heap


### String Literal - String Intern Pool

```java

String data = "Nothing is impossible"; // string literal
```
```
String Intern Pool stores String literals.

Before creating a new literal, Java checks if it already exists in the pool.

If yes, the same reference is reused (memory efficiency).

If not, a new literal is added to the pool.
```

```
|                  | String literal
|   Nothing        |
|  is impossible   | String intern Pool
|                  |
 -------------------
```


### String Object - Heap

```java
String data = new String ("Nothing is impossible");

```
```
Heap stores objects created with new String().

Even if the same string exists in the pool, new forces a new object in the heap.


```

```
|                  |
|   Nothing        | Object is created in heap memory
|  is impossible   | Heap
|                  |
 -------------------
```

## String .intern() in Java -  What it does ?
```

We can explicitly move a String object to the String Intern Pool by calling .intern().

intern() tells Java - Put this string in the String Intern Pool - and return the reference from the pool.

If the string already exists in the pool → Java won’t duplicate it, it will just return the existing reference.

If it doesn’t exist yet → Java adds it to the pool and return that reference.

```
```java
public class InternExample {
    public static void main(String[] args) {
        String s1 = "Nothing is impossible";                 // goes to intern pool
        String s2 = new String("Nothing is impossible");     // new object in heap
        String s3 = s2.intern();             // refers to "Nothing is impossible" from pool

        System.out.println(s1 == s2); // false → different references
        System.out.println(s1 == s3); // true → both point to pool "Nothing is impossible"
    }
}
```
## Excecution Flow
```

String s1 = "Nothing is impossible";

"Nothing is impossible" is stored in the intern pool.

s1 points to the string intern pool.

String s2 = new String("Nothing is impossible");

Creates a new heap object, even though "Nothing is impossible" is already in the pool.

So s2 points to a different object.

String s3 = s2.intern();

intern() checks the pool. "Nothing is impossible" already exists.

Instead of adding a duplicate, it returns the reference from the pool.

Now s3 points to the same object as s1.
```
## Why we always create String literal and not string object?

### string literals

```java

String s1 = "hello";
String s2 = "hello";

```

```
Stored in the String Intern Pool.

When a new literal is created, Java first checks if the same value already exists in the pool.

If it exists → Java reuses the reference instead of creating a new object.

Saves memory and improves performance.

```
### string objects

```java
String s1 = new String("hello");
String s2 = new String("hello");
```
```
Each new String call always creates a new object in heap memory, even if the same value already exists in the pool.

This leads to duplicate objects with the same content → more memory usage.

The object inside heap is separate, but Java still creates/uses a copy of the literal in the intern pool internally.

```

## Concept Check


### 1. What does the intern() method do in Java?

```
Moves a String object from the heap to the String Intern Pool.

If the string already exists in the pool, it returns the reference instead of creating a new one.
```

### 2. What is the return value of intern()?
```
Returns a reference to the string from the intern pool.

String s1 = new String("java");
String s2 = s1.intern();
String s3 = "java";
System.out.println(s2 == s3); // true

```

### 3. What is the difference between new String(abc) and abc.intern()?

```
new String(abc) → creates a new object in the heap (even if abc already exists in the pool).

abc.intern() → ensures the string is placed in the intern pool and returns the reference.

```

### 4. Does intern() always create a new object?
```
No. If the string already exists in the intern pool, it just returns the reference.

If not, it adds it to the pool and returns the new reference.

```