# Loops - Brain Teasers


### Q1. What is a Loop?
```
A loop is used to execute a block of code repeatedly until a specified condition is met.
```

### Q2. Types of Loops in Java ?

```
| Loop Type     | Condition Check   | Executes At Least Once? | When to Use                             |
|---------------|------------------|---------------------------|-----------------------------------------|
| `for`         | Before loop body |  Only if condition is true | When number of iterations is known     |
| `while`       | Before loop body |  Only if condition is true | When number of iterations is unknown   |
| `do-while`    | After loop body  |  Always executes once      | When block must run **at least once**  |
```

### Q3. What is the difference between for, while, and do-while loops in Java?

```
| Feature              | `for` loop                          | `while` loop                          | `do-while` loop                        |
|----------------------|-------------------------------------|----------------------------------------|----------------------------------------|
| Condition Check      | Before executing the block          | Before executing the block             | After executing the block              |
| Guaranteed Execution | No                                  |   No                                   |  Yes (executes at least once)        |
| Use Case             | Known number of iterations          | Unknown number of iterations           | Run block once, then check condition   |
```

### Q4. Can we have infinite loops? How do you break them?
```
Yes, We can create infinite loops with any of the 3 loop types. Use break to exit the loop.
```
```java

while (true) {

    if (Condition)
    
     break;
}
```

### Q5. What happens if the condition is false in a do-while loop?
```
The loop executes once, even if the condition is false.
```
### Q6. Can we use break and continue in loops? What’s the difference?
```
break: Terminates the loop entirely.
```

```java

for (int i = 1; i <= 5; i++) {      // break example
    if (i == 3)
     break;
    System.out.println(i);
}
```

continue: Skips the current iteration and jumps to the next.


```java

for (int i = 1; i <= 5; i++) {   // continue example
    if (i == 3) 
    continue;
    System.out.println(i);
}
```

### Q7. Find the o/p ?

```java

for (int i = 1; i <= 5; i++) {
    if (i == 3) continue;
    System.out.print(i + " ");
}
```

### Q8. Can we nest loops inside loops?
```
Yes, nested loops are common in multi-dimensional structures like 2D arrays.
```
### Q9.  Find the o/p ?

```java

for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 2; j++) {
        System.out.print("* ");
    }
    System.out.println();
}
```

### Q10. What’s the output of the following code? 

```java

int i = 1;
while (i <= 3) {
    System.out.print(i + " ");
    i++;
}
```

### Q11.  Find the o/p ?

```java
int i = 10;
do {
    System.out.print(i + " ");
    i++;
} while (i < 5);

```

### Q12.  Find the o/p ?

```java

for (int i = 1; i <= 5; i++) {
    if (i == 4) break;
    System.out.print(i + " ");
}

```

### Q13.  Find the o/p ?

```java

int i = 1;
while (true) {
    if (i == 3) break;
    System.out.print(i + " ");
    i++;
}
```

### Q14.  Find the o/p ?

```java
for (int i = 1; i <= 2; i++) {
    for (int j = 1; j <= 3; j++) {
        System.out.print(i + "," + j + " ");
    }
    System.out.println();
}

```

### Q15. When would you use a do-while loop over a while loop?
```
Use do-while when the block must run at least once, like menu-based programs or input validations.
```
### Q16. How can you create an infinite loop using while?

```java

while (true) {
    System.out.println("This will never stop unless we break");
}
```

### Q17. How do you safely exit an infinite while loop?

Use the break statement inside a condition.

```java

int i = 1;
while (true) {
    if (i == 5) 
    break;
    System.out.println(i);
    i++;
}
```
### Q18. What happens if you forget to update the loop variable?
```
It causes an infinite loop because the condition never becomes false.
```
```java

int i = 1;
while (i <= 5) {
    System.out.println(i); // Infinite loop, i never changes
    // i++; //  Missing update!
}

```

### Q19. Why is it not advisable to declare variables inside a loop?
```
A new variable is created in every iteration, wasting memory.
```
``` java

for (int i = 1; i <= 5; i++) {
    int x = 10; //  Created again and again
    System.out.println(x + i);
}
```
  Create variable outside:

``` java

int x = 10;
for (int i = 1; i <= 5; i++) {
    System.out.println(x + i);
}
```

### Q20. Can you use break inside a while or do-while loop?
```
Yes. break helps exit the loop before the condition becomes false.
```
```java

int i = 1;
while (i <= 10) {
    if (i == 5) 
    break;
    System.out.println(i);
    i++;
}
```

### Q21. Write a do-while loop that prints numbers from 10 to 1 in reverse

``` java

int i = 10;
do {
    System.out.println(i);
    i--;
} while (i >= 1);

```
### Q22. Find the output of the following code?

``` java

int x = 5;
while (x > 0) {
    System.out.println(x);
    x--;
}
```

### Q23. Find the output of the following code

```java

int i = 10;
do {
    System.out.println(i);
    i++;
} while (i < 5);

```

### Q24. What will be the output?

``` java

int i = 1;
while (true) {
    if (i == 4)
        break;
    System.out.println("Value is: " + i);
    i++;
}
```

### Q25. What will be printed?
```java


int i = 0;
while (i < 3) {
    i++;
    if (i == 2)
        continue; // Skips printing when i = 2
    System.out.println("i = " + i);
}


```

### Mistakes to avoid in Loops
```
| Mistake                                   | Example                                     | Fix                                         |
|-------------------------------------------|------------------------------------------   |---------------------------------------------|
| Not updating the loop variable            | while(i < 10) { ... } (but i++ missing)     | Always update the condition                 |
| Semicolon after FOR or WHILE block        | for(i=0;i<5;i++);                           |  Adds an empty loop body                    |
| Forgetting braces for multiple statements | Only one line runs if `{}` are omitted      | Always use `{}` for clarity                 |
```


### When To Use Which Loop
```
| Loop       | When to Use                              | Common Use Case           |
| ---------- | ---------------------------------------- | ------------------------- |
| FOR        | When the number of iterations is known   | Iterating arrays          |
| WHILE      | When the number of iterations is unknown | User input until valid    |
| D0-WHILE   | When the loop must run at least once     | User menus or retry input |
```
