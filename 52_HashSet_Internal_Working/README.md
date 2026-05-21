# Internal Working Of Hashset

## We are focusing on understanding the following 2 points :

### (1) How set maintains uniqueness ?** 

### (2) why hashset does not maintain order?**

To understand how Set maintains uniqueness, it's helpful to learn how Map works internally. So, Good to have a read about Map first.

## How set maintains uniqueness ?

```
> Set maintains uniqueness by using a HashMap internally.

> When we create a HashSet object, Java secretly uses a HashMap in the background to store the elements.
 
> Since HashSet internally uses a HashMap, it relies on the Map’s unique key property to ensure that the elements in the Set remain unique.

```
##  Why Does HashSet Use HashMap Internally?
```
 Because HashMap already has the logic to: 

> avoid duplicates

> store items using hashing and buckets

> retrieve items quickly

> So instead of writing all that logic again, HashSet reuses HashMap internally.
```

```
##  What happens when we create a Hashset ?

**When we create a HashSet, Java internally creates a HashMap to store its elements**.

```java

Set<Integer> set = new HashSet<>(); // Creating a Hashset

Map<Integer, Object> map = new HashMap<>(); // java internally creates a HashMap

```
## HashSet() Constructor

```java

public HashSet() {
    
    map = new HashMap<>();  // Hashset Constructor
}


> When we create HashSet, the default constructor of the HashSet class is called.

> Internally, the HashSet() constructor creates a HashMap to store its elements.

> This map stores the set elements as keys, which ensures uniqueness - because Map does not allow duplicate keys.

> Internally, HashSet instantiates a HashMap to manage its elements.

```

## What is a Map? How map store elements? 

```

Map is an interface that represents an associative array — a data structure that stores data in key–value pairs.

We can access a VALUE in a Map by using its KEY — this process is called a lookup.

+------------------+
| Map (Key, Value) |
+------------------+

```

## What happens when we add elements to a hashset?

``` java

Set<Integer> set = new HashSet<>();

set.add (1).   // Adding 1 to Hashset

```

## Internal Flow Overview

``` java

set.add(1)  // Adding an element to set
      ↓
map.put(1, PRESENT)  // Hashset internally calls put() method of a HashMap which put elements inside the map.
      ↓
putVal(hash(1), 1, PRESENT, false, true) // hash(key) calculates a hashcode for the element.
                                
                                        // Hashcode >> is the numeric representation of an object and hashcode of a number is number itself.

                                        // The element (1) added to the HashSet becomes the KEY in the internal HashMap

                                        // PRESENT is a dummy object used as the VALUE, It is a constant (static FINAL object)




+----------------+       +-------------------+       +-----------------------+
|   Set.add(1)   | ----► |   map.put(K, V)   | ----► |   map.put(1, PRESENT) |
+----------------+       +-------------------+       +-----------------------+
                                                                  ▲
                                                                  |
                                                                  |
                                                                  |
                                                      
                                                           PRESENT is a constant(static final Object)  

```


## Wanna see - How map.put() works internally? 

```java

public boolean add(E e) { // e becomes the key (element added in set)

    return map.put(e, PRESENT) == null;   // add () method of hashset internally calls put() method of map.
                                         //  PRESENT is the constant dummy value ((static final Object))
                                        // == null >> Checks if map.put() return null — meaning it’s a new entry (i.e., not a duplicate)

}

// Logic:

> If the key is NEW:

      → map.put() returns NULL

      → add() returns TRUE

      → element was added

If the key ALREADY EXISTS:

     → map.put() returns the OLD value (which is always PRESENT in HashSet)

     → add() returns FALSE

     → element was a duplicate

  ```

## What is PRESENT?
```java
private static final Object PRESENT = new Object(); // PRESENT (all caps) → by Java convention, constants are named in uppercase
```

> PRESENT is a constant placeholder object used as the value in the internal HashMap.

> It’s a dummy object to complete the key–value pair — we only care about the keys, which are the actual set elements.




##  What Happens After map.put()? — How putVal() works?

```java

public V put(K key, V value) {. // put() is a public method in HashMap

    return putVal(hash(key), key, value, false, true); // putVal() is an internal method inside the HashMap class — not in Set or HashSet.

}

The put() method of HashMap doesn’t directly insert elements. 

Since HashSet uses a HashMap internally, calling set.add(e) ends up calling map.put(e, PRESENT), which in turn calls putVal().

putVal( )  performs the actual insertion into the appropriate bucket.  

```


 ## What putVal() Does?

> (1) Calculates the hash
 ```
 HashCode is a numeric representation of an object.

 For numbers, the hashcode is the number itself
```
>(2) Finds the right bucket
```
 Using the formulae - hashCode % capacity 
 ```

> (3) Handles collisions
```
 If another key already exists at the same bucket
```

> (4) Checks for duplicates
```
 Compares using equals() to see if the key already exists
```
> (5) Inserts or updates
```
 Adds a new entry or replaces the existing one if the key matches
```


## Do Elements in a HashSet Maintain Order?

```
> No — the elements in a HashSet do not maintain insertion order.

> That’s because:

```
  (1) A HashSet does not support index-based storage like a List or Array.

  (2) It stores elements based on their hashcode, not the order in which they were added.

  (3) Internally, it uses a HashMap, which organizes elements into buckets based on hashing rather than positions.


> So when we iterate over a HashSet, the order may appear random or shuffled, and it can vary depending on the hash distribution.

             
```

``` java
Set<Integer> dataSet = new HashSet<Integer>();
            // Element retrieval order will not be maintained

            dataSet.add(0);
            dataSet.add(1);
            dataSet.add(16);
            dataSet.add(2);
            dataSet.add(32);
            dataSet.add(17);

            System.out.println(dataSet); O/P - order not maintained - [0, 16, 32, 1, 17, 2]
```

## HashSet Class 

``` java
public class HashSet<E>

    extends AbstractSet<E>

    implements Set<E>, Cloneable, java.io.Serializable


 > The parent class of HashSet is AbstractSet.

 > HashSet also implements 3 interfaces:

        - Set – to follow the set contract (no duplicates, unordered)

        - Cloneable – so that it can be cloned (copied)

        - Serializable – so that it can be serialized (saved/transferred)


 NOTE:

extends → means HashSet inherits functionality from the AbstractSet class

implements → means HashSet promises to provide implementations for the methods defined in those interfaces

```

## Why is map marked as transient in HashSet?

```java

private transient HashMap<E,Object> map; // The map is the field being marked as transient.

What does transient mean?

In Java, the transient keyword tells the JVM:

Do not serialize the map when converting the object to a byte stream (e.g., during file save or network transfer).

NOTE: 

Serialization is the process of converting an object into a byte stream, so it can be: (1) Saved to a file (2) Transferred over a network

```
 ## Why skip serialization of the internal map?

```
Because, HashSet is backed by a HashMap internally.

We don’t want to serialize the entire internal structure — like buckets, hashcodes, load factors, etc.

Instead, Java uses custom serialization logic to write only the actual set elements, not the full map.

```
## Benefits of Marking map as transient

```
 Encapsulation: Keeps internal map structure hidden from external systems during serialization.

 Smaller File Size: Avoids writing unnecessary internal data to file or stream.

 Backward Compatibility: Makes it easier to read data even if internal implementation changes in future versions. 

```
## How Hashmap of string Type works ?

```java

static final int hash(Object key) { //  Step 1: Get the key's hashCode()
    
    int h;  // Declares a temporary variable to hold the hashCode

    // If key is null → hash is 0 → goes to bucket 0

        return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);

        // Otherwise → 
        // 1. Calculate hashCode and store in 'h'
        // 2. Right shift h by 16 bits
        // 3. XOR the original and shifted values for better distribution
}



 key.hashCode() → gives the original hash (can be a large int).

 h >>> 16 → shifts bits 16 places right, dropping lower precision.

 ^ (XOR) → combines both to reduce collisions and spread keys evenly.

 If key is null, it avoids error and returns 0.

```

## Can We Add null to a HashSet? Where is it stored?
```

Yes, null can be added to a HashSet.

Behind the scenes, HashSet uses a HashMap — and HashMap allows ONE NULL KEY.

When we add null, the key is treated specially, It directly goes to bucket 0 - INDEX 0 of the internal table.

No hashCode is calculated for null — because it would throw a NullPointerException.

Java internally handles this with:

return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);

So null → returns 0 → goes to index 0.

Only one null is allowed in a Set, because Set doesn’t allow duplicates.

```

## How Does set.contains() Work?

```java

set.contains(1); // Internally, this calls: map.containsKey(1);

Because a HashSet uses a HashMap to store its elements, the contains() method in HashSet checks whether the element exists as a key in the internal map.

```

##  Why Is contains() So Fast?

```
The method HashMap.containsKey() uses hashing. So, Average time complexity = O(1) (constant time)

This means: Lookup is extremely fast, even with large data sets.

The speed is one of the main reasons HashSet is preferred when checking for existence.

```
## Hashing Mechanism -  How HashSet Handles Duplicates ?

**Default capacity of a hashset : By default, when we create a HashSet without specifying the capacity, it internally creates a HashMap with 16 buckets — indexed from 0 to 15.**

```

Index (Bucket)    NODE - The actual object stored inside a bucket

+------+       +----------+----------+----------+----------+
|  0   | ---->  | hashCode |   key    |  value   |  next    |   <-- Elements in a NODE.
+------+       +----------+----------+----------+----------+    
|  1   |                                                       
+------+
|  2   |           Hashcode >> is the numeric representation of an object and hashcode of a number is number itself.
+------+           
|  3   |           Key → The element added to the HashSet
+------+
|  4   |           value → A dummy constant object called PRESENT (used to complete the key–value pair)
+------+.       
|  5   |           next → A pointer (reference) to the next node in the bucket in case of a collision 
+------+        
|  6   |
+------+
|  7   |
+------+
|  8   |   ← Bucket 8
+------+
|  9   |
+------+
| 10   |   Each index in the array is called a BUCKET.
+------+
| 11   |
+------+
| 12   |  ← Bucket 12
+------+
| 13   |
+------+
| 14   |
+------+
| 15   |.  ← Bucket 15
+------+
```
## What’s Inside Each Bucket?

**Each bucket can hold one or more nodes, depending on how many elements map to the same index.**

**Each Node contains the following:**

```java

class Node<K, V> {

    final int hashCode; // hashCode → Numeric representation of the key (used to find the bucket index)

    final K key;        // key → The element added to the HashSet

    V value;            // value → A dummy constant object called PRESENT (used to complete the key–value pair)

    Node<K, V> next;    // next → A pointer to the next node in the same bucket (used during collisions)
}
```

## What happens when we add elements?

``` java

set.add(0);
set.add(1);
set.add(2);

When these elements are added to the HashSet, they are stored internally as shown below (assuming default capacity = 16):

+------+          +-----------------------+   // hashCode = 0   
|  0   | ───────► | [0][0][C][null]       |   // key = 0
+------+          +-----------------------+   // value = C (constant)
                                              // next = null (no collision)

+------+          +-----------------------+
|  1   | ───────► | [1][1][C][null]       |     ← hashCode 1, key 1
+------+          +-----------------------+

+------+          +-----------------------+
|  2   | ───────► | [2][2][C][null]       |    ← hashCode 2, key 2
+------+          +-----------------------+


```

## How is the Bucket Index Calculated?

```java

When we add an element to a HashSet, Java internally calculates the bucket index using:

bucketIndex = hashCode(key) % capacity; // remainder determines the bucket index

This remainder determines the bucket index where the element will be stored.

Since the default capacity is 16, the available bucket indexes range from 0 to 15.

```
## How to calculate hashcode for 16?

```
bucketIndex = hashCode(key) % capacity. 

hashCode(16) % 16 = 0 // Remainder is 0, we already have an element at bucket 0 ( collision)

A hash collision occurs when two different keys produce the same hash index, meaning they are assigned to the same bucket in the hash table.

Elements 0 and 16 are stored in the same bucket, called COLLISION. 
```

## How HashSet Handles Collisions?


```
When two elements map to the same bucket, Java stores them as nodes in a linked list inside that bucket.

Here’s how it looks internally:

+------+                 +----------+----------+----------+----------+
|  0   | ──────────────► | hashCode |   key    |  value   |  next    |.        C = dummy constant (PRESENT)
+------+                 +----------+----------+----------+----------+          
                         |   0      |    0     |    C     |   888    |         next = pointer to the next node in the bucket
                         +----------+----------+----------+----------+
                                                           ↓
                         +----------+----------+----------+----------+  Each bucket can store one or more entries (as nodes), especially  
                         |   0      |   16     |    C     |  null    |  in case of collisions.
                         +----------+----------+----------+----------+
                                                           ↑
                                                    (888 = memory address of next node)

```

## What if number of entries in a single bucket exceeds a threshold (usually 8)?

```
> If the number of entries in a single bucket exceeds a threshold, the linked list is automatically converted into a balanced tree .

> Java 8 Enhancement -  Tree Conversion.(specifically, a Red-Black Tree) to improve performance.

> This transformation helps in:

       Faster lookup (O(log n) instead of O(n))

       Maintaining performance in collision-heavy scenarios.

```
## How HashSet Uses hashCode() and equals() to Ensure Uniqueness?

```

A HashSet in Java uses HASHING to determine where to store elements and equality checks to avoid duplicates. 

This is done using two important methods: (1) hashcode() (2) equals()


(1) hashCode() - Converts an object into an integer hash

This hash is used to determine the bucket/index where the element should go in memory


(2) equals() - equals() checks if two objects are logically equal, even if they land in the same bucket due to matching or colliding hashCode() values.


hashCode() is just a number used for bucket placement — and it’s possible for two different objects to return the same hashcode. This is called a hash collision.

That’s why Java calls equals() to confirm whether the objects are truly duplicates before rejecting the second one.

For proper functioning -  hashCode() and equals() must work together to ensure uniqueness in a HashSet. - That’s how HashSet avoids storing duplicate elements.

```
## Load Factor and Resizing

```
The load factor defines how full the HashSet can get before it resizes.

Default load factor: 0.75

This means: when the number of elements exceeds 75% of the capacity, the HashSet will resize (usually by doubling the capacity).

```
## What Happens During Resizing?
```
When resizing is triggered:

All existing elements are rehashed (i.e., their bucket positions are recalculated).

They are placed into new buckets based on the new capacity.

This helps maintain constant-time performance for operations like add(), contains(), and remove().

This process is automatic and internal — developers don't need to manually resize the set.

Example:

If initial capacity = 16

Then 16 × 0.75 = 12

The 13th element will trigger resizing.

```
##  Comparison: HashSet vs LinkedHashSet vs TreeSet
```

| Feature              | HashSet                            | LinkedHashSet                                  |  TreeSet                                  
|----------------------|----------------------------------- |------------------------------------------------|--------------------
 Order Maintained?     |  No                                |  Yes (insertion order)                         | Yes (sorted order)                        
 
Internal Structure     | HashMap                            | HashMap + Doubly Linked List                  | Red-Black Tree                              

Time Complexity        | O(1) average                       | O(1) average                                   | O(log n)                                     

|Null Allowed?         |  Yes (only one null allowed)       |  Yes                                           |   No (throws `NullPointerException`)       

 Use Case              | Fast lookups with no ordering      | Maintain insertion order + fast access        | Maintain sorted order                       
```

## Summary

```
🔹HashSet and HashMap are classes in Java that implement the Set and Map interfaces respectively.

🔹 HashSet uses a HashMap internally to store elements and ensure uniqueness.

🔹 All elements added to a HashSet become the KEYS of the internal HashMap.

🔹 A constant dummy object called PRESENT is used as the value in the map.

🔹 HashSet.add(e) internally calls map.put(e, PRESENT).

🔹 If map.put() returns null → element is new → added successfully.
   If map.put() returns PRESENT → duplicate → not added.

🔹 The internal map is marked transient to avoid being serialized with all internal structure.

🔹 Serialization only includes actual elements — not buckets, hashcodes, etc.

🔹 Each bucket (0 to 15 by default) holds nodes (key, value, next) for entries.

🔹 Collisions are handled using a linked list inside buckets.
   If bucket entries exceed a threshold (usually 8), they are converted into a balanced tree (Java 8+).

🔹 HashSet relies on two methods to avoid duplicates:
    - `hashCode()` to determine bucket placement.
    - `equals()` to check actual object equality inside same bucket.

🔹 Only one null value is allowed in HashSet (stored at index 0).

🔹 HashSet does not maintain insertion order because elements are stored based on hash, not position.

🔹 Load Factor : HashSet uses a HashMap internally, so it inherits its resizing mechanism.

     Default Load Factor = 0.75
     This means: when 75% of the internal capacity is filled, resizing is triggered.

🔹 Time Complexity for operations like add(), remove(), contains() = **O(1)** (on average)

🔹 Compared to:
    - LinkedHashSet → maintains insertion order
    - TreeSet → maintains sorted order, slower operations (O(log n))

🔹 Use a HashSet when : We need fast search, insertion, and deletion (average time complexity: O(1))

    - We want to store unique items
    - Don’t care about order
    - Need fast access and lookups


```




