# 📘 Java Data Types 

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
- Non-Primitive = store **memory reference** 

---

## 🔹 Data Types Overview — Defaults, Sizes & Examples

| Data Type       | Default Value           | Size                    | Example Usage         |
|------------------|--------------------------|--------------------------|------------------------|
| `byte`           | `0`                      | 1 byte                   | `byte b = 10;`         |
| `short`          | `0`                      | 2 bytes                  | `short s = 1000;`      |
| `int`            | `0`                      | 4 bytes                  | `int a = 5;`           |
| `long`           | `0L`                     | 8 bytes                  | `long l = 123456L;`    |
| `float`          | `0.0f`                   | 4 bytes                  | `float f = 5.5f;`      |
| `double`         | `0.0d`                   | 8 bytes                  | `double d = 5.5;`      |
| `char`           | `'\u0000'` (null char)   | 2 bytes                  | `char c = 'A';`        |
| `boolean`        | `false`                  | JVM-dependent (~1 bit)   | `boolean b = true;`    |
| `String`/`Object`| `null`                   | Reference (4 or 8 bytes) | `String s = "Hi";`     |


---

## 🎯 Interview Questions

- What is a data type in Java?  
- Types of data types in Java?  
- Difference between primitive and non-primitive?  
- Default values of int, boolean, and char?  
- Why can’t primitives hold null?  
- Size in bytes of each primitive type?  
- Range of byte, short, int, long?  
- Can you use int in ArrayList?    
- What if null is assigned to a primitive?  
- What happens when you compare Integer with null?  


---



📬 _You can open an issue or fork the repo to suggest edits — I truly appreciate your input!_
