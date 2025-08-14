# Collection

## Java Collection Framework (JCF) - Introduced in java 1.2 
```
> Java Collection Framework (JCF) is a UNIFIED ARCHITECTURE that provides a set of classes and interfaces to store, retrieve, manipulate, and communicate aggregate data efficiently.

> It was designed to bring all commonly used data structures under one standardized structure, making them easier to use, manage, and extend.
```
```

                   ┌────────────────────┐
                   | Iterable (interface)
                   └────────▲───────────┘
                            │
                         extends
                            │
                ┌────────────────────────┐
                | Collection (interface) |
                └───────▲────▲────▲──────┘
                        │    │    │
                    extends │  extends
                            │
     ┌──────────────── ┐ ┌───────────────┐  ┌────────────────────────┐
     | List (interface)| | Set (interface)| | Queue (interface)      |
     └──────▲──────────┘ └──────▲─────────┘ └────────▲────────────── ┘
            │                   │                      │
        implements          implements         implements
            │                   │                      │
 ┌────────────────────┐ ┌────────────────────┐ ┌────────────────────────────┐
 | ArrayList (class)  | | HashSet (class)    | | PriorityQueue (class)      |
 |LinkedList (class)  | | LinkedHashSet      | | ArrayDeque (class)         |
 | Vector (class)     | | TreeSet (class)    | |                            |
 | Stack (class)      | └────────────────────┘ | LinkedList (class)         |
 └────────────────────┘                        | (also implements Deque)    |
                                                ────────────────────────────┘

LinkedList implements List & Deque (double-ended queue)

```
 ## Why was JCF Introduced?  

Before JCF, Java had multiple unrelated classes (like Vector, Hashtable, etc.) for handling collections. 

Java unified these under one architecture in JCF.

       > Provides standard interfaces (List, Set, Queue, Map).

       > Includes utility methods for sorting, searching, and manipulation.

       > Supports type safety through generics.



## What Is Iterable?

```
Iterable <E> is the root interface in the collection hierarchy. It allows an object to be traversed (iterated) through a collection, enabling sequential access to its elements.

Enables traversal of elements using:

     (1) iterator() method - To iterate through elements

     (2) forEach() > Enhanced loop using lambda

     (3) spliterator() – For parallel iteration

     
```

## Interfaces in JCF

## 1. Collection
```
Extends Iterable

Common methods: add(), remove(), contains(), size(), isEmpty(), clear()
```
## 2. List
```
order of insertion is maintained.

Allows duplicates and nulls.

Access via index.

Implementations: ArrayList, LinkedList, Vector, Stack.
```
## 3. Set
```
No duplicates

No guaranteed order (depends on implementation)

Implementations: HashSet, LinkedHashSet, TreeSet
```

## 4. Queue
```
FIFO structure

Used for task scheduling, buffers

Implementations: PriorityQueue, ArrayDeque, LinkedList
```

## 5. Map (not part of Collection hierarchy)
```
Key-value pair storage

Implementations: HashMap, LinkedHashMap, TreeMap, Hashtable
```

## Why Use Generics in Collections?

Generics ensures type safety - only allows elements of the specified type.

```java

List<String> list = new ArrayList<>();

list.add("Java");    // Allowed

list.add(123);       // Compile-time error

```

## What If There Is No Generics?
```
Without generics, collections return Object, meaning we’ll need to manually type cast each element.

This increases chances of runtime errors like ClassCastException.

Generics provide type safety and eliminate the need for casting.
```
```java

List list = new ArrayList();  //  Raw type (No generics)

list.add(100);

int num = (int) list.get(0); // Manual casting needed
```
## Why Collections Can’t Store Primitives ?

```
Collections store OBJECTS, not primitive types(int,double).

Collections use wrapper classes (Integer, Double, Character, etc.)  because collections work with objects and they require reference types.

Java provides wrapper classes for each primitive type, like:

•	Integer for int

•	Character for char

•	Double for double
```
```java
List<int> list = new ArrayList<>(); //  Error - primitives not supported

List<Integer> list = new ArrayList<>(); // Wrapper class

```
 ## How do classes in Java Collection Framework implement methods from interfaces?

 ```
Java uses interfaces (like List, Set, Queue) to define what a class must do, and concrete classes (like ArrayList, HashSet, LinkedList) to actually do it.

Interfaces declare abstract methods (method signatures only, no logic).

Concrete classes implement these interfaces and provide the actual logic for those methods.

This promotes loose coupling and flexibility in how we work with collections.
```

## Role of Polymorphism:
This is runtime polymorphism in action — where a parent reference (interface) points to a child object (class) and calls overridden methods.

```java

List<String> list = new ArrayList<>();

list.add("Hello"); // List defines it, ArrayList implements it

Though list is of type List, the add() method that gets executed is from ArrayList.
```
