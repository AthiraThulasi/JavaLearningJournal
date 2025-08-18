# What is Type Casting ?
```
Type casting is the process of converting a variable from one data type to another.  

In Java, this can happen automatically (widening) or manually (narrowing).
```

##  1. Implicit Type Casting (Widening Conversion)
```
Implicit Type Casting happens **automatically**.

Java converts a **smaller data type to a larger data type** without any data loss . It is also called **Widening Casting**

```
##  Implicit Conversion Order:

```java

byte → short → int → long → float → double
```

## Wondering how does implicit conversion happens automatically ? And how is a smaller type automatically assigned to a larger one?

## Real-Life Use of Implicit Conversion

 ### Calculating Average
```
we want a decimal result, even though the number starts as an integer.
```
``` java

int totalMarks = 450;       // int
int subjects = 6;          //  int

double average = totalMarks / subjects;  // double

System.out.println(average); // Output: 75.0 in double

```

### How this works?
```
totalMarks and subjects are both int, so: Java performs integer division: 450 / 6 → 75 (int).

We're assigning the result to a double: double average = 75;
```
### Java checks:
```
Can I safely store an int (like 75) inside a double? Why Java Allows This (Implicit Widening).

double has more storage (8 bytes) than int (4 bytes).

double can represent both whole numbers and decimal numbers (e.g., 75.0). There's no risk of data loss. So Java automatically converts int to double.
```

## What is Explicit Conversion? And when is it needed?
```
Explicit casting is when we manually convert one data type to another using (type) syntax — especially when automatic conversion doesn't happen or we want more control.

We tell Java exactly what type to convert to by writing the type in parentheses.

When we explicitly cast totalMarks from int to double, this forces Java to treat totalMarks as a double (455.0) before doing the division.
```

```java

int totalMarks = 455;
int subjects = 6;

// Implicit Conversion
double average1 = totalMarks / subjects;   // Here, Java performs integer division: 455 / 6 → 75 (decimal .833 is lost)

// Explicit Casting
double average2 = (double) totalMarks / subjects;// Explicit Casting - Here, we are telling java, please treat totalMarks as a double before doing the math.

System.out.println("Implicit: " + average1); // Output: 75.0
System.out.println("Explicit: " + average2); // Output: 75.833333...

```

## What happens Internally ?
```
double average2 = (double) totalMarks / subjects

Here, (double) totalMarks is a double operand. One operand is double, so Java promotes the other (subjects = 6) to double automatically.

So the final division becomes: 455.0 / 6.0 → 75.833333...

The result is stored in average2, which is a double.

```