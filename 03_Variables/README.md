#  Variables

## What is a Variable?
```
A variable is a name given to a memory location. It is used to store data that can be changed during the execution of a program.

Syntax >> datatype variableName = value;

```

```java
int a = 10;

+-------------+
|   a = 10    |
+-------------+

| Code          | Meaning                                                                 |
| ------------- | ----------------------------------------------------------------------- |
| int a;        | Declaration – Reserves memory for an integer variable named `a`.        |
| a = 10;       | Assignment – Assigns the value `10` to the variable `a`.                |
| int a = 10;   | Initialization – Declaration + Assignment in a single step.             |


int → Data type

a → Variable name

10 → Value assigned

 Memory is allocated based on the data type (int gets 4 bytes)

```
## Points to Remember

```
Variables focus on memory allocation.

The data type determines how much memory is required and what type of value the variable can store.

Variables allow us to access and manipulate stored data by referring to the variable name, not the memory address.
```
## Key TakeAways:

### What happens when you declare a variable?

**The compiler reserves memory in RAM to hold a value of the specified data type.**

**The variable name acts like a label pointing to that memory location.**

```java

int age = 25;  // Declaration


   Variable             Memory (4 bytes)
+-----------+         
|   age  = 25   
+-----------+        


int tells Java to reserve 4 bytes in RAM.

The value 25 will be stored in that 4-byte memory block.

The variable name age acts as a pointer to the reserved memory where the data (like 25) is kept.
```