# Internal Working Of Hashset

### We are focusing on understanding the following 2 points 

**(1) How set maintains uniqueness ?** 

**(2) why hashset does not maintain order?**

To understand how Set maintains uniqueness, it's helpful to learn how Map works internally. Read about Map here.

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

> store items in a hash table 

> retrieve quickly using hashing 

> So instead of writing all that logic again, HashSet just reuses HashMap.

```
## Creating Hashset

```java

HashSet<Integer> set = new HashSet<>(); // Creating a Hashset

HashMap<Integer, Object> map = new HashMap<>(); // java internally creates a HashMap

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

## How map store elements? 
```
Map is an associative array which stores elements as key - value pairs.

+------------------+
| Map (Key, Value) |
+------------------+

```

## What happens when we add elements to hashset?

``` java

HashSet<Integer> set = new HashSet<>();

add.set(1)

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
  ```

## What is PRESENT?
```java
private static final Object PRESENT = new Object();
```

> PRESENT is a constant placeholder object used as the value in the internal HashMap.

> It’s a dummy object to complete the key–value pair — we only care about the keys, which are the actual set elements.

> If the KEY is NEW, map.put() returns NULL

> If the KEY already EXISTS, map.put() returns the previous value (i.e., PRESENT)

> Then HashSet.add() does this:

 > (1) If map.put( ) == null → returns true → element was added

 > (2) If map.put( ) != null → returns false → element was a duplicate



##  What Happens After map.put()? — How putVal() works?

```java

public V put(K key, V value) {

    return putVal(hash(key), key, value, false, true);

}

The put() method of HashMap doesn’t directly insert elements. 

Instead, It calls an internal method putVal( ) which performs the actual insertion into the appropriate bucket.  

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

      (1)  A HashSet does not maintain indexes like a list or array.

      (2) It stores elements based on their hashcode, not the order in which they were added.

      (3) Internally, it uses a HashMap, which organizes elements into buckets (based on hash) rather than positions.

> So when we iterate over a HashSet, the order may appear random or shuffled — and it can change depending on the hash distribution.
             
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

            System.out.println(dataSet);
```

## HashSet Class Declaration

``` java
public class HashSet<E>

    extends AbstractSet<E>

    implements Set<E>, Cloneable, java.io.Serializable


 The parent class of HashSet is AbstractSet.

 HashSet also implements 3 interfaces:

        - Set – to follow the set contract (no duplicates, unordered)

        - Cloneable – so that it can be cloned (copied)

        - Serializable – so that it can be serialized (saved/transferred)

 extends → means it inherits behavior from a class.

 implements → means it agrees to provide code for the methods defined in those interfaces.
```

## Why is map marked as transient in HashSet?

```java

private transient HashMap<E,Object> map; // The map is the field being marked as transient.

What does transient mean?

In Java, the transient keyword tells the JVM:

Do not serialize the map when converting the object to a byte stream (e.g., during file save or network transfer).
```
 ## Why skip serialization of the internal map?

```
Because, HashSet is backed by a HashMap internally.

We don’t want to serialize the entire internal structure — like buckets, hashcodes, load factors, etc.

Instead, Java uses custom serialization logic to write only the actual set elements, not the full map.

```
## Benefits of Marking map as transient

```
 Encapsulation**: Keeps internal map structure hidden from external systems during serialization.

 Smaller File Size: Avoids writing unnecessary internal data to file or stream.

 Backward Compatibility: Makes it easier to read data even if internal implementation changes in future versions. 

```
# How Hashmap of string Type works ?

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

# Can We Add null to a HashSet? Where is it stored?

Yes, null can be added to a HashSet.

Behind the scenes, HashSet uses a HashMap — and HashMap allows one null key.

When we add null, the key is treated specially, It directly goes to bucket 0 (i.e., index 0 of the internal table).

No hashCode is calculated for null — because it would throw a NullPointerException.

Java internally handles this with:

``` java

return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);

So null → returns 0 → goes to index 0.

 Only one null is allowed in a Set, because Set doesn’t allow duplicates.
```

## How Does set.contains() Work?

```java

set.contains(1); // Internally, this calls: map.containsKey(1);

Because a HashSet uses a HashMap to store its elements, the contains() method in HashSet checks whether the element exists as a key in the internal map.



##  Why Is It So Fast?

The method HashMap.containsKey() uses hashing, so: Average time complexity = O(1) (constant time)

This means: Lookup is extremely fast, even with large data sets.

The speed is one of the main reasons HashSet is preferred when checking for existence.

```
## Hashing Mechanism -  How HashSet Handles Duplicates ?

### Default capacity of a hashset 

By default, when we create a HashSet without specifying the capacity, it internally creates a HashMap with 16 buckets — indexed from 0 to 15.

```
+------+       +----------+----------+----------+----------+
|  0   | ────► | hashCode |   key    |  value   |  next    |    > This is how elements are stored in hashset.
+------+       +----------+----------+----------+----------+    > Each bucket is an index in memory 
|  1   |                                                        > — Elements are stored in linked lists when there are collisions.
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
|  8   |
+------+
|  9   |
+------+
| 10   |
+------+
| 11   |
+------+
| 12   |
+------+
| 13   |
+------+
| 14   |
+------+
| 15   |
+------+
```
## What’s Inside Each Bucket?

**Each bucket in this array can hold a linked list of nodes in case of collisions.**

**Each Node contains the following:**

```java

class Node<K, V> {

    final int hashCode; // hashCode → Numeric representation of the key (used to find the bucket index)

    final K key;        // key → The element added to the HashSet

    V value;            // value → A dummy constant object called PRESENT (used to complete the key–value pair)

    Node<K, V> next;    // next → A pointer to the next node in the same bucket (used during collisions)
}
```

### What happens when we add elements?

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

When we add an element to a HashSet, Java internally calculates the bucket index using:

```java

bucketIndex = hashCode(key) % capacity; // remainder determines the bucket index

```
This remainder determines the bucket index where the element will be stored.

Since the default capacity is 16, the available bucket indexes range from 0 to 15.


## How to calculate hashcode for 16?

```
bucketIndex = hashCode(key) % capacity. 

 hashCode(16) % 16 = 0 // we already have an element at bucket 0 ( collision)

When two different objects return the same hashcode. This is called a hash collision.

Elements 0 and 16 goes to the same bucket, called COLLISION. 
```
## How HashSet Handles Collisions?

When two elements map to the same bucket, Java stores them as nodes in a linked list inside that bucket.

Here’s how it looks internally:

```
+------+                 +----------+----------+----------+----------+
|  0   | ──────────────► | hashCode |   key    |  value   |  next    |.        C = dummy constant (PRESENT)
+------+                 +----------+----------+----------+----------+          
                         |   0      |    0     |    C     |   888    |         next = pointer to the next node in the bucket
                         +----------+----------+----------+----------+
                                                           ↓
                         +----------+----------+----------+----------+
                         |   0      |   16     |    C     |  null    |
                         +----------+----------+----------+----------+
                                                           ↑
                                                    (888 = memory address of next node)

```

## What if number of entries in a single bucket exceeds a threshold (usually 8)?

> If the number of entries in a single bucket exceeds a threshold, the linked list is automatically converted into a balanced tree .

> Java 8 Enhancement -  Tree Conversion.(specifically, a Red-Black Tree) to improve performance.

> This transformation helps in:

       Faster lookup (O(log n) instead of O(n))

       Maintaining performance in collision-heavy scenarios.

```

A HashSet in Java uses hashing to determine where to store elements and equality checks to avoid duplicates. This is done using two important methods:

 (1) hashcode() (2) equals()

hashCode() - Converts an object into an integer hash

This hash is used to determine the bucket/index where the element should go in memory

equals() - equals() checks if two objects are logically equal, even if they land in the same bucket due to matching or colliding hashCode() values.

In a HashSet, two objects with the same hashCode() might still be different.

hashCode() is just a number used for bucket placement — and it’s possible for two different objects to return the same hashcode. This is called a hash collision.

That’s why Java calls equals() to confirm whether the objects are truly duplicates before rejecting the second one.

for proper functioning -  hashCode() and equals() must work together to ensure uniqueness in a HashSet. - That’s how HashSet avoids storing duplicate elements.

```
## Load Factor and Resizing

The load factor determines when the HashSet should resize.

Default load factor = 0.75

When 75% of the HashMap's capacity is filled, it resizes (usually doubling the capacity).

Resizing involves rehashing all elements and placing them into new buckets, ensuring continued performance.

 Example:
If initial capacity = 16 →
16 × 0.75 = 12 → Resizing occurs after the 12th element is added.


## Comparison with Other Set Implementations

 LinkedHashSet: Extends HashSet

Maintains insertion order using a doubly-linked list

Ideal when maintaining order is needed

TreeSet: Implements NavigableSet & SortedSet

Uses a Red-Black Tree internally

Maintains sorted order (natural or using a custom comparator)

Provides O(log n) time for add, remove, and contains operations


## Summary
```
> HashSet uses HashMap to maintain uniqueness.

> All logic for hashing and collision resolution is handled by HashMap.

> add() method in HashSet calls put() in HashMap.

> Collisions are handled using linked list inside buckets.

> Only one null key is allowed.

> Internals (like the backing map) are marked transient to avoid serialization issues.

```




