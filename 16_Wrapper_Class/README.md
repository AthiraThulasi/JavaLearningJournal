# Wrapper Class in Java

## What is a Wrapper Class? Why Do We Need It?
```
Think of this: You're on an international trip to Amsterdam .

You carry local currency, but to shop or dine abroad, you need Euros (€) — the local currency there.
So, you convert your local currency to Euros to be able to function smoothly during your trip.

In Java, it's similar - Java is an object-oriented language, and while primitive types like int, char, and boolean are simple and fast (like local currency), they cannot be used in places where objects (Euros) are required.

Since **Java Collections (like ArrayList, HashMap) and many utility classes and APIs** are designed to work with **objects**, primitives like int, char, and boolean cannot be used directly in those contexts. 

That’s where **Wrapper Classes** come in — they act like a currency converter , WRAPPING THE PRIMITIVE into an OBJECT form so it can be used where only objects are allowed.
```

###  Analogy Summary:
```
| Concept        | Example   | Analogy                                  |
| -------------- | --------- | ---------------------------------------- |
| Primitive Type | `int`     | Local currency (limited use)             |
| Wrapper Class  | `Integer` | International currency (widely accepted) |

```

###  How Can We Define a Wrapper Class?
```
A Wrapper Class is an object representation of a primitive type.

```

##  Primitive vs Wrapper Types

```
| Primitive Type | Wrapper Class |
| -------------- | ------------- |
| `byte`         | `Byte`        |
| `short`        | `Short`       |
| `int`          | `Integer`     |
| `long`         | `Long`        |
| `float`        | `Float`       |
| `double`       | `Double`      |
| `char`         | `Character`   |
| `boolean`      | `Boolean`     |

```

##  Wrapper Class Features

```java
int num = 10;           // Primitive
Integer numObj = 10;    // Wrapper class
```
```
* Part of java.lang package

* Immutable, like Strings

* Allow primitive types to be used as Objects.

* Wrapper → stored in heap

```

##  Primitive vs Wrapper Comparison
```
| Feature               | Primitive Type | Wrapper Class        |
| --------------------- | -------------- | -------------------- |
| Stored in             | Stack Memory   | Heap Memory (Object) |
| Can be null?          | ❌ No           | ✅ Yes                |
| Supports methods?     | ❌ No           | ✅ Yes                |
| Works with instanceof | ❌ No           | ✅ Yes                |
| Used in Collections   | ❌ No           | ✅ Yes                |
```

##  Visual Comparison
```

| primitive | `int num1 = 10;`        Wrapper  | `Integer num2 = 10;`                      |
| -------------------------------- | ----------------------------------------- |
| Stores `10` directly in variable | Stores a reference to object holding `10` |
| Stored in stack                  | Stored in heap                            |
| No methods available             | Many methods (parseInt, toString, etc.)   |
```


##  Null Handling

### `Integer x = null`  vs `int y = null` 

| Wrapper Class                      | Primitive Data Type                 |
| ---------------------------------- | ----------------------------------- |
| ✅ `Integer x = null;`              | ❌ `int y = null;`                   |
| Reference type (can be null)       | Must hold a concrete value like `0` |
| Null means no object is referenced | Null is not allowed in primitives   |
| Works fine in Java                 | Compile-time error                  |

>  `Integer` is an object and can store `null`.

>  `int` must have a real number like `0`, `1`, etc.

---

##  Why Do We Need Wrapper Classes?
```
1. Collections like `ArrayList<int>`  won’t work with primitives → use `ArrayList<Integer>` 

2. Allow `null` values

3. Provide utility methods like `parseInt()`

4. For object-oriented features like **autoboxing**, **null handling**, and **generics**

> `int` is faster but  `Integer` is flexible for OOP and Collection use

Don’t worry if Collections are new to you — you'll understand this even better in the **Collections** section of the journal.

```

##  Use of Wrapper in Collections

Generics (type) in Java require objects — they don’t accept primitive types. That’s why we use wrapper classes:

```java
// List
List<Integer> integerList = new ArrayList<>();  // Here Generics is Integer

// Set
Set<Double> doubleSet = new HashSet<>();        // Here Generics is Double

// Map
Map<Integer, String> studentMap = new HashMap<>();  

// Queue
Queue<Character> charQueue = new LinkedList<>();  // Here Generics is Character

// Stack
Stack<Float> floatStack = new Stack<>();    // Here Generics is Float

// PriorityQueue
PriorityQueue<Long> longQueue = new PriorityQueue<>();

// Deque
Deque<Short> shortDeque = new LinkedList<>();
```

These are examples of using wrapper classes with various generic data structures in Java.



##  Concept cHECK


* What is a Wrapper Class in Java?
* Why do we need Wrapper Classes when we already have primitive types?
* List all primitive types in Java and their corresponding wrapper classes?
* Can you assign null to a wrapper class?
* What is autoboxing and unboxing in Java? Give examples.
* How are primitives and wrappers stored?
* What’s the default value of Object?
* Are wrapper classes immutable?
* Can you extend a wrapper class?
* How is memory handled differently for primitive types and wrapper classes?
* What are the default values of wrapper class objects vs primitive types?
* What is the difference between == and .equals() when comparing wrapper objects?
* What are the performance implications of using wrapper classes instead of primitives?
* Can you override methods on wrapper classes like Integer or Boolean?
* Can wrapper classes be used in switch-case statements?




