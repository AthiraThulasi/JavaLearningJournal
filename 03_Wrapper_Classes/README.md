
# 🏑 What is a Wrapper Class? Why do we need it?

Think of this: you're on an **international trip** 
✈️. You carry **local currency**, but to shop or dine abroad, you need to **convert it to the local currency of that country**.  

In Java, it's similar.  
Primitive types like `int`, `char`, and `boolean` are like **local currency** — simple and fast, but not accepted everywhere.

Java’s Collections and many APIs are designed to work with **objects**, not primitives.  
That’s where **Wrapper Classes** come in — they “wrap” primitives into object form, making them compatible with Java's object-oriented features.

---

### 🔁 Analogy Summary:

| Concept         | Example     | Analogy                      |
|------------------|-------------|-------------------------------|
| Primitive Type   | `int`       | Local currency (limited use) |
| Wrapper Class    | `Integer`   | International currency (widely accepted) |

---

### How can you define a Wrapper Class?
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
| Null means no object is referenced| Null is not a value, it's a reference (not allowed in primitives)       |
| Works fine in Java                | Throws compile-time error                                |

✅  Integer is an object (wrapper class) and can store null > Storing null means it doesn't point to any actual object.

❌ int is a primitive data type and cannot be assigned null — it must have a real number like 0, 1, -5, etc.


---

## 🔹 Why Do We Need Wrapper Classes?

1. Collections like `ArrayList<int>` ❌ won’t work → use `ArrayList<Integer>` ✅  
2. Allow `null` values  
3. Provide utility methods like `parseInt()`  
4. For object-oriented features like **autoboxing**, **null handling**, and **generics**

---

📌 `int` is faster  
📌 `Integer` is flexible for OOP and Collection use  

---

## Interview Questions

### ✅ Basic Level

- What is a Wrapper Class in Java?

- Why do we need Wrapper Classes when we already have primitive types?

- List all primitive types in Java and their corresponding wrapper classes?

- Can you assign null to a primitive type? What about a wrapper class?

- What is autoboxing and unboxing in Java? Give examples.

### ⚙️ Intermediate Level

- What happens behind the scenes when autoboxing or unboxing occurs?

- How is memory handled differently for primitive types and wrapper classes?

- What are the default values of wrapper class objects vs primitive types?

- What is the difference between == and .equals() when comparing wrapper objects?

- What are the performance implications of using wrapper classes instead of primitives?

### 🧠 Advanced Level

- Can you override methods on wrapper classes like Integer or Boolean?

- Can wrapper classes be used in switch-case statements?

- What will the following code print? Why?
     
     Integer a = 1000;
     Integer b = 1000;
     System.out.println(a == b);

