#  For Loop

**A for loop is used when the number of iterations is known in advance.**

It has **3** parts:

### Initialization – where the loop starts.

### Condition – until when the loop should run.

### Increment/Decrement – how the loop variable updates.

## Syntax of a For Loop:

```java
for (initialization; condition; updation) {
    // Code to be executed in each iteration
}
```
## How to define a for loop?

```java
for (int i = 1; i <= 2; i++) {
    System.out.println("Athira");
}
```

**Output**
---

i <= 2. > so output is printed twice!

Athira

Athira


## Breakdown of Syntax:

int i = 1; → **Initialization** (loop starts from 1)

i <= 5; → **Condition** (loop runs while this is true)

i++ → **Updation** (i is incremented by 1 after every loop)

## What is i++?

i++ means increment i by 1 after each loop cycle.

It’s the same as writing: i = i + 1;

Example: i++ gives 1, 2, 3, 4, 5

Example: i-- gives 5, 4, 3, 2, 1


## Looping Variable

**i** is called the **looping variable** or control variable.

We can name it anything (e.g., j, count, etc.)

### Scope Reminder:

The **variable i** is accessible only inside the loop.

If we try to use i outside the loop, it results in a **compile-time error**.

**Error: cannot resolve symbol 'i'.**


## For Loop Essentials

| Step         | Purpose                                   | Example         |
|--------------|-------------------------------------------|-----------------|
| **Initialization** | Start the loop with a variable          | `int i = 1`     |
| **Condition**     | Loop continues **while this is true**     | `i <= 5`        |
| **Update**        | Update the variable after each iteration | `i++` or `i--`  |

> **If the update is missing, the loop can become **infinite**!

## Post vs Pre Increment & Decrement


| Expression | Step 1                   | Step 2                        | Final `x` | Final `i` |
| ---------- | ------------------------ | ----------------------------- | --------- | --------- |
| `x = i++;` | Assign `x = i` → `x = 5` | Then `i = i + 1` → `i = 6`    | `5`       | `6`       |
| `x = ++i;` | `i = i + 1` → `i = 6`    | Then assign `x = i` → `x = 6` | `6`       | `6`       |
| `x = i--;` | Assign `x = i` → `x = 5` | Then `i = i - 1` → `i = 4`    | `5`       | `4`       |
| `x = --i;` | `i = i - 1` → `i = 4`    | Then assign `x = i` → `x = 4` | `4`       | `4`       |


## ✅ Summary

✅ Post-Increment (i++): Use the value first, then increment.

✅ Pre-Increment (++i): Increment first, then use the updated value.

✅ Post-Decrement (i--): Use the value first, then decrement.

✅ Pre-Decrement (--i): Decrement first, then use the updated value.



##  Reverse For Loop

When we want to loop backwards, such as printing values from 5 to 1, use reverse for loop.
```java
for (int i = 5; i >= 1; i--) {
    System.out.println(i);
}
```

**Here, i-- decreases the value of i in each iteration until the condition i >= 1 becomes false.**


## For Loop Without Condition

**Gives an **infinite loop** as as **EXIT CRITERIA** is not mentioned.


```java
for (int i = 1; ; i++) {
    System.out.println(i);
    if (i == 5)
        break; // Stop after printing 5
}
```

If we don’t use break, this loop will run forever!


## For Loop With Multiple Variables

We can declare and update multiple variables in a for loop.

```java

for (int i = 1, j = 5; i <= 5; i++, j--) {
    System.out.println("i = " + i + ", j = " + j);
}
```


i = 1, j = 5  
i = 2, j = 4  
i = 3, j = 3  
i = 4, j = 2  
i = 5, j = 1  


## Enhanced For Loop (For-Each)

"Used when we just want to read elements of an array/collections one by one, without using an index."

```java
int[] numbers = {1, 2, 3, 4, 5};

for (int num : numbers) {
    System.out.println(num);
}
```

✅ Here, num takes each element from the array numbers.

✅ Best for read-only iteration when we don’t need to change the elements.



## When to Use For Loop?

**When number of iterations is known**.

Great for counting, printing patterns, or accessing array indexes.


## Interview Question:

### How many times is the condition checked in a for loop that runs 5 times?

```java
for (int i = 1; i <= 5; i++) {
    System.out.println("i = " + i);
}
```


###  Step-by-Step Execution:


| Iteration   | `i` Value | Condition `i <= 5` | Executes?         |
|-------------|-----------|--------------------|--------------------|
| Before 1st  | 1         | true               | ✅ Prints `i = 1`  |
| 2nd         | 2         | true               | ✅ Prints `i = 2`  |
| 3rd         | 3         | true               | ✅ Prints `i = 3`  |
| 4th         | 4         | true               | ✅ Prints `i = 4`  |
| 5th         | 5         | true               | ✅ Prints `i = 5`  |
| After 5th   | 6         | false              | ❌ Loop ends       |



**Total Executions:** 5  

**Condition checked:** 6 times (`n + 1`)

### Key Points:

The condition is evaluated:

✅ **Before the first execution**

✅  **After every iteration.**

**So, for n loop runs, the condition is checked n + 1 times**





