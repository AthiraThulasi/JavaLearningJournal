#  While 

```
 The while loop is used to execute a block of code repeatedly as long as the condition is true.
```
## Syntax:
```java
while (condition) {

    // code block to be executed
}
```
## Flow
```
Condition is checked first

If true → executes the body

If false → exits the loop immediately
```

## Example 1: Print numbers from 1 to 5

```java
int number = 1;

while (number <= 5) {

    System.out.println(number);

    number = number + 1;
}
```

## While Excecution:
```
| Step | number Value | Condition number <= 5 | Action          |
|------|-----------|--------------------|------------------     |
| 1    | 1         | true               | Prints 1, number → 2  |
| 2    | 2         | true               | Prints 2, number → 3  |
| 3    | 3         | true               | Prints 3, number → 4  |
| 4    | 4         | true               | Prints 4, number → 5  |
| 5    | 5         | true               | Prints 5, number → 6  |
| 6    | 6         | false              | Loop exits            |   
```

## Note:
```
The loop runs as long as the condition is true.

If the condition is false at the start, the loop block won’t run even once.
```
## Infinite loop 

```java
int number = 1;

while (number <= 5) {
    System.out.println(number);
                                    // number = number + 1; ← This is missing!
}
```

## What Happens?

```
number stays 1.

number <= 5 is always true, So the loop never exits.

It keeps printing 1 again and again keeping the loop infinite.

```

## Defining Variable Inside a Loop !
```
 Never define a variable inside a loop
```
```java

for (int i = 1; i <= 5; i++) {
    int x = 10; ❌  // x is redefined on every iteration
    System.out.println(x + i);
}
```
```
 Always define the variable outside the loop:
```
```java

int x = 10; ✅ // Defined once, 
for (int i = 1; i <= 5; i++) {
    System.out.println(x + i); // reusing the same x
}
```

## While with break statement
```

Normally, a loop ends when its condition becomes false.

But sometimes, we may want to exit early — for example, if a certain value is found or a condition is met.

In such cases, break gives a manual control to terminate the loop before its natural end.
```
```java
int i = 1;

while (true) { 
    if (i == 5) {
        break; // Exit loop when i = 5
    } else {
        System.out.println("We are going to be good in Java :-)"); // Prints message
        i++; // Update i
    }
}


```
