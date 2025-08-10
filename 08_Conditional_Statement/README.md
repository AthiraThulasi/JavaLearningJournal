#  Conditional Statements

```
Java executes code sequentially, line by line.

But if, we want to control the flow based on certain conditions — that’s where conditional statements help.

```
### Conditional statements in Java:

```
if

if-else

if-else-if

switch

```

# 1. if Statement


```java

// Syntax

if (condition) {

    block of code to execute **if condition is true**
}
```
## How it works ?
```

 If the condition is true, Java executes the immediate next statement or code block.

If the condition is false, Java skips the next statement/block.
```
## Example 1: Single Statement

```java
int c = 100;

if (c > 50)

    System.out.println("C is greater than 50");
```

## Example 2: Code Block with Multiple Lines
```java

if (c > 5) {

    System.out.println("Hello");

    System.out.println("How are you");

    System.out.println("Are you learning java");

}
```
## Example 3: False condition  without braces
```java

int c = 10 + 5;

if (c > 10)  // False

System.out.println("C is lesser than 10"); // skipped

System.out.println("C is greater than 10"); //  This is outside the if - always executed
```
## Java's Rule for if Without Braces {}
```
When we write an if statement without {}, only the immediate next line (the first one) is treated as part of the if.
```

## Example 4: Using & (bitwise AND) with two conditions

```java
int a = 100;
int b = 20;

if (a > b && b > a) {

    System.out.println("a is greater than b");    // Code block will only be excecuted, if both conditions are true!

    System.out.println("b is greater than a");

}
```


## Condition Analysis:
```
a > b → 100 > 20 →  true

b > a → 20 > 100 → false

true && false →  false
```
## Notes
------------
```
Always use curly braces {} if the if block has more than one line.

If the block isn’t executed (condition is false), it becomes a dead code block.
```
## if Block Execution


```java
if (c > 10)
     |
   True
     ↓
Execute next statement(s)
```

```plaintext
if (c > 10)
     |
   False
     ↓
Skip the next statement(s)
```

# 2. if else
--------------
```
The if-else statement lets you choose between two blocks of code based on whether the condition is true or false**
```
```java
        condition
            |
         +--+--+
     true|     |false
        ↓       ↓
   Execute     Execute
     if         else
   block        block
```

 Syntax:
```java
if (condition) {

    // executes if condition is true

} else {

    // executes if condition is false
}
```
### Example:

```java

int a = 10;

int b = 20;

if (a > b) {

    System.out.println("a is greater");

} else {

    System.out.println("b is greater");

}

Output:

Since a > b is false, the output will be: b is greater
```
### Key Concept:
```
The if block runs if the condition is true

The else block runs if the condition is false

Only one of the two blocks will execute
```
### Tip
```
Used when you have exactly two outcomes.

Avoid using else without if — they always work as a pair
```

# 3. if-else-if Ladder
-------------------------

```plaintext
         condition1
             |
         +---+---+
     true|       |false
         ↓       condition2
      Block1        |
                 +--+--+
             true|     |false
                ↓       condition3
             Block2        |
                        +--+--+
                    true|     |false
                       ↓       ↓
                    Block3   Else block
```
```
The if-else-if ladder is used when you need to check multiple conditions (sequential checks), one after another.

It allows you to choose one block out of many based on which condition is true first.
```
 ## Syntax:
```java
if (condition1) {

    // runs if condition1 is true

} else if (condition2) {

    // runs if condition2 is true

} else if (condition3) {

    // runs if condition3 is true

} else {

    // runs if none of the above are true
}
```
## Example
```java

int percentage = 75;  


if (percentage > 100 || percentage < 0) {    //  Boundary Condition Check

    System.out.println("Invalid Percentage");  // >100 or <0 is invalid

    return;  //  Stops execution if value is invalid
}


if (percentage > 90) {           //  Grade Assignment Based on Valid Percentage

    grade = 'A';

} else if (percentage >= 80 && percentage < 90) {

    grade = 'B';

} else if (percentage >= 70 && percentage < 80) {

    grade = 'C';

} else if (percentage < 70) {

    grade = 'F';  // Handles rest of values <70

} else {

    grade = '-';  //  Missing value case (if percentage is 0 for example)
}

System.out.println("Grade: " + grade);

```
## 4.Switch Statement
----------------------
```
A switch statement is used when we have multiple fixed values to compare against one variable.**
```
```java

switch (expression) {

    case value1:

        // code block

        break;

    case value2:

        // code block

        break;

    // ... more cases

    default:
        // default block (optional)
}
```
### Key Points
```

switch	    Starts the block that checks different values

case	    Each possible value to match

break	    Exits the switch after a match is found

default 	(Optional) Runs if no case matches

```
## Example: Switch Based on Grade
```java

char grade = 'B';

switch (grade) {

    case 'A':

        System.out.println("Excellent!");
        break;

    case 'B':
        System.out.println("Very Good!");
        break;

    case 'C':
        System.out.println("Good");
        break;

    case 'D':
        System.out.println("You passed");
        break;

    case 'F':
        System.out.println("Better luck next time");
        break;

    default:
        System.out.println("Invalid grade");
}
```
## How It Works?
```java

If grade = 'B'?

Java checks: 

(1) Is it 'A'?  No

(2) Is it 'B'? Yes → prints "Very Good!" and exits

```
### Note
---------------------
```
Works with byte, short, int, char, String, and enums (not float, double).

Without break, all below cases will execute ("fall-through").
```








