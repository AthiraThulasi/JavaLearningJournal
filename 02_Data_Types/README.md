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

| Data Type     | Default Value       | Size                    |
|---------------|----------------------|--------------------------|
| byte          | 0                    | 1 byte                  |
| short         | 0                    | 2 bytes                 |
| int           | 0                    | 4 bytes                 |
| long          | 0L                   | 8 bytes                 |
| float         | 0.0f                 | 4 bytes                 |
| double        | 0.0d                 | 8 bytes                 |
| char          | '\u0000' (null char) | 2 bytes                 |
| boolean       | false                | 1 bit*                  |
| Object/String | null                 | reference (4 or 8 bytes)|

> ⚠️ Note: Local variables (inside methods) **must be initialized** before use. Instance and static variables get default values.

---

# 🏑 Wrapper Classes in Java

## 🔹 Why Wrapper Classes?

Imagine going on an **international trip** ✈️. You have **local currency** but want to shop, eat food, and explore.  
But — local currency won't work! You need to **convert to that country's currency**.

Similarly:
- `int` is like **local primitive** currency
- To use in Collections or Objects, you must **wrap it in a Wrapper Class**

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

```java
int num = 10;               // Primitive
Integer numObj = 10;        // Wrapper class
```

> Primitive → stored in **stack**  
> Wrapper → stored in **heap**

---

## 🔹 Primitive vs Wrapper Comparison

| Feature               | Primitive Type | Wrapper Class        |
| --------------------- | -------------- | -------------------- |
| Stored in             | Stack Memory   | Heap Memory (Object) |
| Can be null?          | ❌ No           | ✅ Yes                |
| Supports methods?     | ❌ No           | ✅ Yes                |
| Works with instanceof | ❌ No           | ✅ Yes                |
| Used in Collections   | ❌ No           | ✅ Yes                |

---

## 🔹 Visual Comparison

| int num1 = 10;                          | Integer num2 = 10;                           |
|----------------------------------------|---------------------------------------------|
| Stores `10` directly in variable        | Stores a reference to object holding `10`   |
| Stored in stack                         | Stored in heap                              |
| No methods available                    | Many methods (parseInt, toString, etc.)     |

---


## 🔹 Null Handling: `Integer x = null` ✅ vs `int y = null` ❌

| Wrapper Class                      | Primitive Data Type                                      |
|-----------------------------------|-----------------------------------------------------------|
| ✅ `Integer x = null;`             | ❌`int y = null;`                                           |
| ✅ `Integer` is a reference type, can be null | ❌ `int` must hold a concrete value (e.g., 0, 1)           |
| Null means no object is referenced| Null is not a value, it's a reference (not allowed)       |
| Works fine in Java                | Throws compile-time error                                |

✅  Integer is an object (wrapper class) and can store null > Storing null means it doesn't point to any actual object.

❌ int is a primitive data type and cannot be assigned null — it must have a real number like 0, 1, -5, etc.


---

## 🔹 Why Do We Need Wrapper Classes?

1. Collections like `ArrayList<int>` ❌ won’t work → use `ArrayList<Integer>` ✅  
2. Allow `null` values  
3. Provide utility methods like `parseInt()`  
4. Java supports **Autoboxing**:

```java
List<Integer> list = new ArrayList<>();
list.add(10); // int auto-converted to Integer
```

---

📌 `int` is faster  
📌 `Integer` is flexible for OOP and Collection use  


---

## 🎯 Interview Questions

### ✅ Basic
- What is a data type in Java?  
- Types of data types in Java?  
- Difference between primitive and non-primitive?  
- Default values of int, boolean, and char?  
- Why can’t primitives hold null?  
- Size in bytes of each primitive type?  
- Range of byte, short, int, long?  

### ⚙️ Intermediate
- What is autoboxing/unboxing?  
- Why are wrapper classes needed?  
- Difference between int and Integer?  
- Can you use int in ArrayList?  
- How are primitives and wrappers stored?  
- What’s the default value of Object?  
- What if null is assigned to a primitive?  

### 🧠 Advanced
- What happens when you compare Integer with null?  
- Difference between == and `.equals()` for wrappers?  
- Why does `Integer a = 127`, `b = 127` → `a == b` true, but false when `a = 128`?  
- Are wrapper classes immutable?  
- Can you extend a wrapper class?  
- How does `Integer.parseInt()` work internally?  
- What is value caching in wrapper classes?

---

📬 _You can open an issue or fork the repo to suggest edits — I truly appreciate your input!_
