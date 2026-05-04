# ArrayList

```
Imagine we are building a Contact App with 100s of contacts.
 
Can we use an Array?

No — because:

      Arrays have a fixed size, which must be declared at the time of creation.

      In a contact app, we’ll frequently add or remove contacts, and we don’t know the total number in advance.

      So, arrays are not suitable for such dynamic operations.
 

 Why use ArrayList?

•	ArrayList is a resizable array (dynamic), meaning it can grow or shrink in size.

•	It stores elements in a contiguous memory structure, allowing fast access.
```

## Features of ArrayList !
```

- Belongs to: java.util package.

- Dynamic array → Resizable (unlike regular arrays).

- Allows duplicate values.

- Allows null elements.

- Maintains insertion order.

- Not synchronized (not thread-safe), but fast for single-threaded applications.

- Faster than Vector in single-threaded environments.

- Time complexity for accessing an element: O(1) → Constant Time  

```

## Why Do We Need ArrayList When We Already Have Arrays?

> Arrays are one of the oldest and simplest data structures in Java.

> They help us store data in a contiguous memory block with index-based access — fast and efficient!

> But they come with a major limitation: Once the size of an array is defined, it cannot be changed.

> Imagine We're building a contact list or a shopping cart — and we don’t know how many items will be added. Arrays will fall short here. This is where ArrayList comes in.
 
## ArrayList – A Resizable Array!

ArrayList  offers a dynamic way to store and manage data.

We don't have to worry about size — it can grow as needed.

## Syntax of ArrayList

```java

List<Integer> al = new ArrayList<Integer>();

```

```

>	List <Integer> : This defines a list that will store Integer objects — not primitive int, but its object form, which is called a wrapper class.

>	al: This is the reference variable

>	new ArrayList<>() - This creates the object in heap memory

>	When this object is created:

        > The ArrayList class is loaded into memory.

        > Instance variables are created inside heap.

        > The constructor is called.

 ```

## How Memory Works with ArrayList?

```java

List<Integer> al = new ArrayList<Integer>();

```

## What happens Internally ?

```
	> al is created in the stack.

	> It points to the memory allocated inside the heap.

	> By default, ArrayList creates 10 memory slots (capacity) in the heap to store objects.

	> Each slot can hold one Integer object.

	> When we start adding elements - 

	         > Elements are stored at sequential indexes, starting from index 0.

	         > With each addition, the size of the ArrayList increases.

	         > The internal capacity is fixed at 10 by default.

	         > Capacity remains unchanged until the ArrayList is full.

```
## Adding Elements in ArrayList — How Capacity and Size Work Internally ?
```
al.add(1); // Index 0 → Size = 1 → Capacity remaining = 9  
al.add(2); // Index 1 → Size = 2 → Capacity remaining = 8  
al.add(3); // Index 2 → Size = 3 → Capacity remaining = 7  
al.add(4); // Index 3 → Size = 4 → Capacity remaining = 6  
 ```

## What Happens When ArrayList Gets Full?

### Once all 10 slots are filled, ArrayList automatically increases its capacity.

``` java

To calculate new capacity :

newCapacity = oldCapacity + (oldCapacity / 2).

newCapacity = 10 + (10 / 2) = 15

```
```
> A new internal array with capacity 15 is created.

> All 10 existing elements are copied into this new array.

> The reference variable al now points to the new memory.

> The old array is removed by the Garbage Collector.

> This resizing happens behind the scenes — giving you the power of a flexible array without the manual effort!

```
 
## Why Is ArrayList Fast?  What is the Time Complexity ?
```

Time complexity describes how the performance of an operation scales with the size of the input.

ArrayList works like a normal array — all elements are stored next to each other in memory.

So when we say get(3), Java knows exactly where the 3rd element is.

It jumps directly to that spot — no searching, no looping.

This direct access makes retrieval very fast, even for large lists — and this happens in CONSTANT TIME, i.e., O(1).

Time Complexity of ArrayList is O(1).

```


## How to Make an ArrayList Thread-Safe (Synchronized)?

### 2 ways  - (1) By Using Collections.synchronizedList() &  (2) Using CopyOnWriteArrayList 

### (1) By Using Collections.synchronizedList()

By using collections utility method synchronizedList and pass the arraylist

```java

List<String> syncList = Collections.synchronizedList(new ArrayList<>());

// This ensures thread-safe access.

```

 
### 2. Using CopyOnWriteArrayList (Expensive Solution)

```java

CopyOnWriteArrayList<String> safeList = new CopyOnWriteArrayList<>());

```
This is a thread-safe variant of ArrayList. It creates a fresh copy of the array list on every write (add/remove/update), ensuring safe iteration during concurrent modifications.

Expensive Solution – as it creates new copy everytime.







