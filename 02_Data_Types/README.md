# 📘 Data Types

---

## 🔹 What is a Data Type?

A **data type** defines how much memory is required to store data and what kind of data a variable can hold — such as numbers, characters, or logical values.

 Data is stored in **binary (0s and 1s)** because computers operate using electrical states:
- ON → `1`
- OFF → `0`

---

##  How Computers Store Data

- Values like `15` are **converted into binary** before being stored in memory.
- Computers use **transistors** that detect binary signals.
- Each change in signal is called a **bit** (binary digit).

---

## 🔢 Bit, Nibble, Byte Breakdown

| Term              | Value                                 |
|-------------------|----------------------------------------|
| 1 nibble          | 4 bits                                |
| 2 nibbles = 1 byte| 8 bits                                |
| Integer           | 32 bits → 4 bytes                     |
| Max value in nibble | `1111` in binary = `15` in decimal   |
| 1 byte range      | 0 to 255 (`00000000` to `11111111`)   |

---

##  Types of Data Types in Java

Java has **two categories** of data types:

| Type           | Details                                                             |
|----------------|---------------------------------------------------------------------|
| **Primitive**   | Stores actual values in memory (like `int`, `char`, `boolean`)     |
| **Non-Primitive** | Stores **references** to memory locations (like `String`, `Array`) |

---

##  Java Primitive Data Types

Java provides **8 primitive types**. These are **not objects** and store actual data directly in memory.

| Data Type | Default Value | Size in Bits | Range                           |
|-----------|----------------|--------------|----------------------------------|
| `byte`    | 0              | 8 bits       | -128 to 127                      |
| `short`   | 0              | 16 bits      | -32,768 to 32,767                |
| `int`     | 0              | 32 bits      | -2³¹ to 2³¹-1                    |
| `long`    | 0L             | 64 bits      | -2⁶³ to 2⁶³-1                    |
| `float`   | 0.0f           | 32 bits      | ±3.4e38 (6–7 digits precision)   |
| `double`  | 0.0d           | 64 bits      | ±1.8e308 (15 digits precision)   |
| `char`    | '\u0000'       | 16 bits      | Unicode characters               |
| `boolean` | false          | 1 bit (logical)| true or false                  |

---

##  Non-Primitive Data Types

These include:

- Classes
- Arrays
- Interfaces
- Strings
- Enums

 **Key Point:**  
Non-primitive types **store memory addresses** (references), not actual values. They point to objects stored in the heap memory.

---

## ✅ Takeaways

| Feature                  | Primitive Type           | Non-Primitive Type           |
|--------------------------|---------------------------|-------------------------------|
| Stores actual value      | ✅ Yes                   | ❌ No (stores reference)      |
| Includes                 | `int`, `char`, `float`   | `String`, `Array`, `Class`   |
| Memory location          | Stack                    | Heap                         |
| Default value            | 0, false, etc.           | `null`                       | |
| Mutable                  | ❌ No (immutable)         | Depends on the class         |

---

##  Example


int age = 30;

float pi = 3.14f;

char grade = 'A';

boolean isPassed = true;

## Notes

- Use `int` by default for whole numbers and `double` for decimal numbers.
- Use `float` only when memory is a concern and precision is less important.
- `char` is used to store **a single character** (in Unicode).
- `boolean` is not numeric — it stores logical values (`true` or `false`).

---

## Interview Questions on Java Data Types

1. **What are the 8 primitive data types in Java?**
   - `byte`, `short`, `int`, `long`, `float`, `double`, `char`, `boolean`

2. **Why does Java use fixed sizes for its data types?**
   - To maintain platform independence and consistency across different machines (WORA: Write Once, Run Anywhere).

3. **What is the default value of `char` and `boolean`?**
   - `char`: `'\u0000'` (null character), `boolean`: `false`

4. **What is the size of `boolean` in Java?**
   - Java doesn't define a specific bit size for `boolean`, but logically it's 1 bit. Actual memory used depends on JVM.

5. **Can we store a `char` in an `int` variable?**
   - Yes, because `char` is internally stored as a Unicode integer value (2 bytes). Implicit casting is allowed.

6. **What is the difference between `float` and `double`?**
   - `float` is 32-bit and less precise (6–7 decimal digits), `double` is 64-bit and more precise (15 digits). Use `float` when memory is a constraint.

7. **What happens if you assign a float to an int?**
   - Compilation error: “possible lossy conversion”. You must explicitly cast it: `int x = (int) 3.14;`

9. **What is type casting?**
   - Changing one data type to another. Implicit (widening) and explicit (narrowing) casting.

10. **Why is `char` 2 bytes in Java?**
    - To support Unicode characters, which need more than 1 byte.

11. **What is the range of `int` in Java?**
    - `-2,147,483,648` to `2,147,483,647` (`-2^31 to 2^31 - 1`). Exceeding it causes overflow.

12. **What is the difference between `null`, `0`, and `false`?**
    - `null`: reference to nothing (objects), `0`: numeric zero (int/float), `false`: boolean value




---

