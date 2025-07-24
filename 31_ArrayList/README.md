# ArrayList

## Features of ArrayList !
```

- Belongs to: java.util package.

- Dynamic array → Resizable (unlike regular arrays).

- Allows duplicate values.

- Allows null elements.

- Maintains insertion order.

- Not synchronized (not thread-safe).

- Faster than Vector in single-threaded environments.

- Time complexity for accessing an element: O(1) → Constant Time  

```

## Why Do We Need ArrayList When We Already Have Arrays?

Arrays are one of the oldest and simplest data structures in Java.

They help us store data in a contiguous memory block with index-based access — fast and efficient!

But they come with a major limitation:

Once the size of an array is defined, it cannot be changed.

Imagine We're building a contact list or a shopping cart — and we don’t know how many items will be added. Arrays will fall short here. This is where ArrayList comes in.
 
## ArrayList – A Resizable Array!

ArrayList is a class in Java from the java.util package. 

It offers a dynamic way to store and manage data.

We don't have to worry about size — it can grow as needed.

## Syntax of ArrayList

```java

ArrayList<Integer> al = new ArrayList<Integer>();

```

```

>	ArrayList <Integer> : This defines a list that will store Integer objects — not primitive int, but its object form, which is called a wrapper class.

>	al: This is the reference variable

>	new ArrayList<>() - This creates the object in heap memory

>	When this object is created:

        > The ArrayList class is loaded into memory.

        > Instance variables are created inside heap.

        > The constructor is called.

 ```

## How Memory Works with ArrayList?

```java

ArrayList<Integer> al = new ArrayList<Integer>();

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
 
## What Is the Time Complexity of ArrayList?

Time complexity describes how the performance of an operation scales with the size of the input.

When we perform CRUD operations (Create, Read, Update, Delete), understanding time complexity helps us compare data structures like ArrayList vs. LinkedList.

Accessing by index → Time Complexity: O(1) → Constant Time
 
## Why Is ArrayList Fast?

	> ArrayList offers fast random access, meaning it can access elements directly by index.

	> It does not require sequential traversal, so even with a large list, accessing any element is very fast. 

	> Time Complexity: O(1) → Constant Time.


##  How to Make an ArrayList Thread-Safe (Synchronized)?

### (1) By Using Collections.synchronizedList()

By using collections utility method synchronizedList and pass the arraylist

```java

List<String> syncList = Collections.synchronizedList(new ArrayList<>();

```
This ensures thread-safe access, but manual synchronization is still needed when iterating.
 
### 2. Using CopyOnWriteArrayList (Expensive Solution)

```java

CopyOnWriteArrayList<String> safeList = new CopyOnWriteArrayList<>();

```
This is a thread-safe variant of ArrayList. It creates a fresh copy of the array list on every write (add/remove/update), ensuring safe iteration during concurrent modifications.

Expensive Solution – as it creates new copy everytime.


✅  Interview Questions on Internal Working of ArrayList
What is the default capacity of an ArrayList in Java?
→ 10
How does an ArrayList grow when the capacity is full?
→ It increases by 50% of its current capacity (new capacity = old + old/2).
What is the difference between size() and capacity in an ArrayList?
→ size() = number of elements added. 
capacity = number of elements the internal array can hold.
Can an ArrayList hold primitive types like int?
→ No. It can only hold objects. For int, we must use the wrapper class Integer.
Where is an ArrayList stored in memory?
→ The reference (al) is stored in the stack. The actual objects (data) are stored in the heap.
What happens when an ArrayList is full and a new element is added?
→ A new larger internal array is created, old elements are copied, and the new element is added.
Is ArrayList thread-safe?
→ No. It's not synchronized. Use Collections.synchronizedList() or CopyOnWriteArrayList for thread safety.
How does ArrayList differ from an array in memory management?
→ Arrays have fixed size and can't grow. ArrayList grows dynamically and internally manages memory.
Can we manually set the capacity of an ArrayList?
→ Yes, using new ArrayList<>(initialCapacity).
How is resizing handled in ArrayList? Is it costly?
→ Yes, resizing can be costly. It involves creating a new array and copying elements, which takes time.




