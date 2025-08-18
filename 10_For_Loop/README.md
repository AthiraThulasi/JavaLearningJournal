#  For Loop

```
A FOR LOOP is used when the number of iterations is known in advance.
```
```
It has 3 parts: 

INITIALIZATION – where the loop starts.

CONDITION – until when the loop should run.

INCREMENT/DECREMENT – how the loop variable updates.

```
## Syntax of a For Loop:

```java
for (initialization; condition; updation) {
    
    // Code to be executed in each iteration
}
```
## How to define a for loop?

```java

for (int i = 1; i <= 2; i++) {
    
    System.out.println("Java");
}
```
```
OUTPUT:

i <= 2. > so output is printed twice!

java

java
```

## Breakdown of Syntax:
```
int i = 1; → Initialization (loop starts from 1)

i <= 5; → Condition (loop runs while this is true)

i++ → Updation (i is incremented by 1 after every loop)
```
## What is i++?
```
i++ means increment i by 1 after each loop cycle.

It’s the same as writing: i = i + 1;

Example: i++ gives 1, 2, 3, 4, 5

Example: i-- gives 5, 4, 3, 2, 1
```

## Looping Variable
```
"i" is called the LOOPING VARIABLE or CONTROL VARIABLE.

We can name it anything (e.g., j, count, etc.)
```
### Scope Reminder:
```
The VARIABLE i is accessible only inside the loop.

If we try to use i outside the loop, it results in a COMPILE TIME ERROR.

ERROR: cannot resolve symbol 'i'.
```

## For Loop Essentials
```
| Step               | Purpose                                   | Example         |
|------------------- |-------------------------------------------|-----------------|
| INITIALIZATION     | Start the loop with a variable            | int i = 1       |
| CONDITION          | Loop continues **while this is true**     | i <= 5          |
| UPDATE             | Update the variable after each iteration  | i++ or i--      |

> If the update is missing, the loop can become INFINITE!
```
## Post vs Pre Increment & Decrement

```
| Expression | Step 1                   | Step 2                        | Final x | Final i     |
| ---------- | ------------------------ | ----------------------------- | --------- | --------- |
| x = i++;  | Assign x = i → x = 5      | Then i = i + 1 → i = 6        | 5         | 6         |
| x = ++i;  | i = i + 1 → i = 6         | Then assign  x = i → x = 6    | 5         | 6         |
| x = i--;  | Assign x = i → x = 5      | Then i = i - 1 → i = 4        | 5         | 4         |
| x = --i;  | i = i - 1 → i = 4         | Then assign x = i → x = 4     | 4         | 4         |
```

##  Summary
```
 Post-Increment (i++): Use the value first, then increment.

 Pre-Increment (++i): Increment first, then use the updated value.

 Post-Decrement (i--): Use the value first, then decrement.

 Pre-Decrement (--i): Decrement first, then use the updated value.

```
##  Reverse For Loop
```
When we want to loop backwards, such as printing values from 5 to 1, use reverse for loop.

```
```java
for (int i = 5; i >= 1; i--) {
                                   // Here, i-- decreases the value of i in each iteration until the condition i >= 1 becomes false.
    System.out.println(i);
}
```

## For Loop Without Condition
```
Gives an INFINITE LOOP as an EXIT CRITERIA is not mentioned.

If we don’t use break, this loop will run forever!

```

```java
for (int i = 1; ; i++) 

```

## For Loop With Multiple Variables

```
We can declare and update multiple variables in a for loop.
```
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
```
Used when we just want to read elements of an array/collections one by one, without using an index.
```
```java
int[] numbers = {1, 2, 3, 4, 5}; // numbers is an array which holds 5 integer values: 1, 2, 3, 4, 5.

for (int num : numbers) {. // num is a loop variable or Element variable — it temporarily holds each element of the array **numbers** during every iteration.

    System.out.println(num);
}
```

## When to Use For Loop?
```
When NUM OF ITERATIONS is KNOWN.

Great for counting, printing patterns, or accessing array indexes.

```

## Concept Check:

### How many times is the condition checked in a for loop that runs 5 times?

```java
for (int i = 1; i <= 5; i++) {
    System.out.println("i = " + i);
}
```


###  Step-by-Step Execution:
```

| Iteration   | `i` Value | Condition `i <= 5` | Executes?         |
|-------------|-----------|--------------------|--------------------|
| Before 1st  | 1         | true               |  Prints `i = 1`  |
| 2nd         | 2         | true               |  Prints `i = 2`  |
| 3rd         | 3         | true               |  Prints `i = 3`  |
| 4th         | 4         | true               |  Prints `i = 4`  |
| 5th         | 5         | true               |  Prints `i = 5`  |
| After 5th   | 6         | false              |  Loop ends       |

```
```
Total Executions - 5  

Condition checked - 6 times (n + 1)

In a for loop, if it runs n times, the condition is checked n + 1 times.
```
### Key Points:

```

Before the loop starts:
Java first checks the condition to decide if the loop should even begin.

During the loop:
After each iteration finishes, Java checks the condition again to see if another round should run.

When the loop ends:
Finally, Java checks the condition one more time, sees it’s false, and then stops the loop.

So, for n loop runs, the condition is checked n + 1 times.

```




