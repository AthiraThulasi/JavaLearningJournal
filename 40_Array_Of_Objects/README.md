# Array of Objects

```
Let’s revisit Array!
```
###  Array

```
Array is a linear data structure, which store similar kind of data!

It stores multiple values of the same data type in contiguous memory locations.

It allows data access efficiently using an index.

Arrays are non-primitive. They are type safe.

```
```java
int[] a = new int[3];
```
```
int is a primitive type.

Java creates an array of 3 int slots in heap memory.

The reference variable a is stored in the stack.

a[0] = 100; // adding values to array
a[1] = 101;
a[2] = 103;
```
```
   Stack                        Heap
 ---------       --------------------------------
|   a     | ---> |  [100]    [101]    [103]      |
 ---------       --------------------------------
```

## What is Array of Objects ?
```
An array of objects is an array that stores references to many objects of the same class.

Instead of creating each object one by one, we can group them in a single array and manage them together.

Array of objects is ideal for:

Students in a school → Student[]

Products in a cart → Product[]

Movies in a library → Movie[]

We can scale from 1 object to hundreds — all with the same logic.

```

## How to Create Array Of Objects?

## Step 1: Declare array of references

```java

Person[] p = new Person[3];    // p = reference variable (lives in stack).
                              // Person = user-defined class (type of object the array can hold).
                             // new Person[3] → allocates an array of 3 references in the heap, each slot is initialized to null.
                            // Here each memory location is going to act as reference variable
                           // 3 memory locations created in heap act as reference variable
```
```
   Stack                        Heap
 ---------       -----------------------------------------
|   p     | ---> | [null]   [null]   [null]               |
 ---------       -----------------------------------------

```

```
Person is a user-defined class (non-primitive type).

Java creates an array of 3 null references in the heap.

The reference variable p is stored in the stack.

```

## Step 2: Create and assign objects

```java
p[0] = new Person("Joe", "S101", "A");
p[1] = new Person("Jack", "S102", "B");
p[2] = new Person("Jen", "S103", "C");

```

### What Does This Mean?

```
Each element in the array p is a reference to a Person object:

p[0] → Person("Joe", "S101", "A")

p[1] → Person("Jack", "S102", "B")

p[2] → Person("Jen", "S103", "C")

Each one is a separate object in memory, but all are of type Person.

```
```
   Stack                        Heap
 ---------       -----------------------------------------
|   p     | ---> | [ref0]   [ref1]   [ref2]               |.      Now, each reference in the array points to an actual Person object in the heap.
 ---------       -----------------------------------------
                   |        |         |
                   v        v         v
                 Joe      Jack      Jen
               (p[0])    (p[1])    (p[2])
```
## Using for-each Loop in Array of Objects
```
Here, Person is the class type used for each element.

```
```java
for (Person per : p) {
    System.out.println(per);
}
```


## Revisit: for-each with Primitive Array !

```java
int[] arr = new int[3];
for (int a : arr) {
    System.out.print(a);
}
```

## Summary Table: Array vs Array of Objects:
```
| Concept         | Array                       | Array of Objects               |
| --------------- | --------------------------- | ------------------------------ |
| Data Type Used  | Primitive (`int`, `double`) | Class/Object (`Person`)        |
| Memory (Heap)   | Stores actual values        | Stores references to objects   |
| Default Values  | `0`, `0.0`, `false`, etc.   | `null`                         |
| Object Creation | Direct via index            | Must use `new` for each object |
```
## CONCEPT CHECK


## 1. What is an array of objects in Java?
``` 
An array of objects is an array that stores references to many objects of the same class.

Instead of creating each object one by one, we can group them in a single array and manage them together.

```


## 2. How does memory allocation work in an array of objects?

``` 

- The array of references is created in heap memory.

- Each object must be created separately using `new`.  

- Until initialized, the references are `null`.

```

## 3. If you declare Person[] p = new Person[3]; but don’t initialize with new - what happens when you try to access p[0]?

```
We’ll get a NULL POINTER EXCEPTION because the array only holds NULL references until objects are assigned.

```

## 4. How do you iterate over an array of objects?

Using for or for-each loop:  

```java
for (Person person : p) {
    System.out.println(person.getName());
}
```
## 5. Can you sort an array of objects?
```
Yes - Using Arrays.sort() along with: Comparable (natural ordering) or Comparator (custom ordering)
```
## 6. Can an array of objects hold different types?
```
No,  All elements must be of the declared type or its subclasses.
Example: Animal[] can hold Dog and Cat objects (since both extend Animal).
```
## 7. What's the difference between Person[] and ArrayList<Person>?
```
Array → Fixed size, cannot grow dynamically.

ArrayList → Resizable, provides more flexibility with dynamic data management.

```

