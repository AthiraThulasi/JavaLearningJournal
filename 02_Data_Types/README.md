# 📘 Java Data Types and Wrapper Classes

## 🔹 What is a Data Type?

A **data type** defines how much memory is required to store data.

- Memory refers to **RAM**, where program data is temporarily stored during execution.

Example:

```java
int x = 15;
```

Can `15` be directly stored inside memory? ❌ No.

- Numbers are stored in memory as **binary** (e.g., 00001111), since computers understand only 0s and 1s.

---

## 🔹 Why Can't Computers Store Decimal Numbers Directly?

- Computers work using **micro-transistors** which detect only **two states**: ON (1) and OFF (0).
- Each **binary state** of a transistor (ON or OFF) is represented as a **bit (binary digit)**.

---

## 🔹 Bit, Nibble, Byte, Integer

- `1 nibble = 4 bits`
- `2 nibbles = 8 bits = 1 byte`
- `Integer = 32 bits = 4 bytes`

| Binary | Decimal |
| ------ | ------- |
| 0000   | 0       |
| 1111   | 15      |

So, maximum value a nibble can store is **15** (decimal) = **1111** (binary).

- `1 byte = 8 bits = 2 nibbles`
- Can store from **0 to 255** (256 total values)

---

## 🔹 Types of Data Types

### 📦 1. Primitive Data Types (store actual values)

- Boolean → `true`, `false`
- Character → single character
- Number:
  - Integer types: `byte`, `short`, `int`, `long`
  - Floating-point types: `float`, `double`

### 🧱 2. Non-Primitive Data Types (store memory address)

- Reference types → `Class`, `Object`, `Array`, `Interface`, `Enum`
- Store memory **address** (pointers), not actual values

### ✅ Takeaway:

- Primitive = store **actual value**
- Non-Primitive = store **memory reference** to object in heap

---

## 🔹 Default Values

In Java:
- **Primitive types** are *not automatically assigned default values* in **local variables** (variables declared inside methods).
- But if they are **instance variables** (declared inside a class but outside any method), they are assigned defaults.
- **Non-primitive types** (objects) are assigned default value `null`.

| Data Type     | Default Value |
|---------------|----------------|
| byte          | 0              |
| short         | 0              |
| int           | 0              |
| long          | 0L             |
| float         | 0.0f           |
| double        | 0.0d           |
| char          | '\u0000' (null char) |
| boolean       | false          |
| Object/String | null           |

> ⚠️ Note: Local variables (inside methods) **must be initialized** before use. Instance and static variables get default values.

---

# 🏱 Wrapper Classes in Java

## 🔹 Why Wrapper Classes?

Imagine going on an **international trip** ✈️. You have **local currency** but want to shop, eat food, and explore. 

But — local currency won't work! You need to **convert to that country's currency**.

 Similarly:

- `int` is like **local primitive** currency
- But to use in collections or objects, you need to **wrap it in a Wrapper Class** to convert it into an **object type**

👉 A **Wrapper Class is an object representation of a primitive type**.

---

## 🔹 Primitive vs Wrapper Types

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

---

## 🔹 Wrapper Class Features

- Part of **java.lang** package
- **Immutable**, like Strings
- Allow primitive types to be used as **Objects**

Example:

```java
int num = 10;               // Primitive → num is a variable that stores the value 10 directly
Integer numObj = 10;        // Wrapper → numObj is a reference that stores the memory address of an object holding 10
```

- Primitive → stored in **stack**
- Wrapper → stored in **heap**

> ⚠️ Note: JVM optimizations may affect where objects are stored, but this is generally true.

---

## 🔹 Primitive vs Wrapper Comparison

| Feature               | Primitive Type | Wrapper Class        |
| --------------------- | -------------- | -------------------- |
| Stored in             | Stack Memory   | Heap Memory (Object) |
| Can be null?          | ❌ No           | ✅ Yes                |
| Supports methods?     | ❌ No           | ✅ Yes (`Integer.parseInt()`, `toString()`, etc.) |
| Works with instanceof | ❌ No (not an object) | ✅ Yes                |
| Used in Collections   | ❌ No           | ✅ Yes                |

---

## 🔹 Visual Comparison: `int` vs `Integer`

| `int num1 = 10;`                                     | `Integer num2 = 10;`                                               |
|------------------------------------------------------|---------------------------------------------------------------------|
| `10` is directly stored inside `num1`                | `10` is stored inside an `Integer` object                          |
| `num1` is like a box holding the value `10`          | `num2` holds a reference (address) to an object containing `10`    |
| Stored in **stack memory**                           | Stored in **heap memory**                                          |
| No object reference — just the value                 | Reference points to memory location where the object lives         |

---

## 🔹 Null Handling: `Integer x = null` ✅ vs `int y = null` ❌

| Wrapper Class                              | Primitive Data Type                                  |
|--------------------------------------------|------------------------------------------------------|
| `Integer x = null;`                        | `int y = null;`                                      |
| ✅ `Integer` is a reference type, can be null | ❌ `int` must hold a concrete value (e.g., 0, 1)     |
| Null means no object is referenced         | Null is not a value, it's a reference (not allowed)  |
| Works fine in Java                         | Throws compile-time error                            |

---

## 🔹 Why Do We Need Wrapper Classes?

1. **Collections** like `ArrayList<int>` ❌ don’t work, but `ArrayList<Integer>` ✅ does  

2. **Allow null values** → `Integer x = null` ✅, but `int y = null` ❌  

3. **Provide utility methods**
   ```java
   int num = Integer.parseInt("100");  // converts String to int
   ```
4. **Autoboxing support**  

   Java automatically converts between primitives and wrappers:
   ```java
   List<Integer> numbers = new ArrayList<>();
   numbers.add(5); // int is autoboxed to Integer
   ```

---

📌 `int` is faster as it stores values directly in memory.  
📌 `Integer` is more useful for **Collections**, nulls, and **object-oriented features**.

🎯 Interview Questions
=======================

✅ Basic Level
================
What is a data type in Java?

What are the different types of data types in Java?

What is the difference between primitive and non-primitive data types?

What is the default value of int, boolean, and char in Java?

Why can’t a primitive variable be assigned null?

What is the size (in bytes) of each primitive type in Java?

What is the range of a byte, short, int, and long?

⚙️ Intermediate Level
=======================
What is autoboxing and unboxing in Java?

What are wrapper classes and why do we need them?

What is the difference between int and Integer?

Can we use primitives in collections like ArrayList? Why not?

How are primitive types and wrapper objects stored in memory (stack vs heap)?

What is the default value of an object reference?

Explain how memory is allocated for a wrapper object vs primitive.

What happens if we try to assign null to a primitive variable?

🧠 Advanced
===============
What will happen if we compare an Integer object with null?

What’s the difference between == and .equals() when comparing wrapper objects?

Why is Integer a = 127; Integer b = 127; true for a == b, but false when the value is 128?

Are wrapper classes immutable? How?

Can a wrapper class be extended?

How does Java internally convert a String to int using Integer.parseInt()?

Explain the concept of value caching in wrapper classes.


