
## Maps

## Map Hierarchy 
```
             +----------------------+
             |      Map (interface) |                           Map (specifically HashMap) = Array (buckets) + LinkedList 
             +----------+-----------+
                        ↑
implements+---------------------------+implements
         |             |                      |
No order |             |implements            |
 +-------------+  +-------------+  +------------------+                                Hashmap implements Map
 | HashMap     |  | TreeMap     |  | LinkedHashMap    |                                LinkedHashMap implements Map
 | (class)     |  | (class)     |  | (class)          |  java.utilpackage              TreeMap implements Map
 +-------------+  +-------------+  +------------------+
                                Maintain Insertion order
``` 

  ## NOTE :
 ```
   Hashmap (class) implements Map (interface)

   LinkedHashMap (class) implements Map (interface)

   TreeMap (class) implements Map (interface)

   Class Implements Interface means >> 
   
         (1) The class gets access to all the method signatures in the interface.

         (2) The class must write the actual logic (method bodies) for them.

```

##  What is a Map ?

```
 > Map is an interface that represents an associative array. Association is between KEY & VALUE.

    +------------------+
    | Map (Key, Value)  |
    +------------------+

 > Whenever we want to retrieve the VALUE, use the KEY associated with it. This is called LOOK UP OPERATION (Retrieval).

 > LOOK UP happens at super speed.

 > Perfomance of get() or the LOOK UP opearation is O(1) > Time Complexity. 

 > Example use: Counting frequencies, lookups (dictionary-style).

```

## What is Timecomplexity O(1) means?
```
> No matter how many key-value pairs are stored in the map, whether it's 10, 100, 1,000, or even 1 million.

> Retrieving a value using a KEY will take the same amount of time > So TimeComplexity is Constant - O(1)

```

## What is Hashing ? How Hashing Works in HashMap ?
```
Hashing is the process of converting a large object (like a string) into a fixed-length integer value — called hashCode.

This integer value is the  bucket index where the NODE will be stored ( KEY & VALUE)

Reduces collisions  and enables fast retrieval.


bucketIndex = hashCode % capacity;
```
```java

Example: Hashcode of an Integer Object

Integer i = 10; // or Integer i = new Integer(10);

System.out.println(i.hashCode()); // Output: 10 // Hashcode of any integer obj is number itself.

```
```
+-------------------------+
|  Integer is a Wrapper   |                                      //   Integer is a wrapper class.                    
|  class for int          |
+-----------+-------------+                                    //  Parent of integer is Object.
            |
            |                                                // Object class provides a method called hashCode(), which generates hashcode using hashing to convert large objs into fixed len integer
     +------+------+
     |   Object    |  ← Parent of Integer
     +------+------+
            |
     +------+------+
     | hashCode()  |  ← Method in Object class
     +-------------+
            | Generates hashcode using hashing which converts larger object into fixed length integer value
            v
  For Integer: hashCode() = value itself // Example: new Integer(10).hashCode() = 10
  
```

## How is hashCode() calculated for a String?

Java uses a specific formula to calculate the hashcode of a String:

```java

hashCode = s[0]*31^(n-1) + s[1]*31^(n-2) + ... + s[n-1]

s[i] is the ith character of the string

^ means exponentiation (power)

31 is a prime number used to reduce collisions
```
```
+------------------------------+
|         String s = "abc"     | ----> String is converted to character array [a,b,c]
+------------------------------+

hashCode formula:

|--------------------------------------------------|
|s[0]*31^(n-1) + s[1]*31^(n-2) + ... + s[n-1]*31^0 |  31 is base multipier ( primenumber ) -> Less collisons
|--------------------------------------------------|

= 'a'*31^2 + 'b'*31^1 + 'c'*31^0
= 97*961  + 98*31   + 99*1
= 96354 > fixed length integer

So here large string get converted to fixed length integer
```




We say 2 objects are equal, when they have same hashcode + check the value of instance variables.
Hashcode and Hashing are used in maps to decide where keys and values are stored!


Map consists of an array/table which has a size of 16, with index from 0 to 15. Each index is called BUCKET.

When we create a hashmap > HashMap <Integer,String> hmap = new HashMap(), the follwing table will be created.

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
| 10   |   Each index in the array is called a BUCKET > BUCKET holds a NODE
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

**Each bucket can hold one or more NODES, depending on how many elements map to the same index.**

**Each node is going to be LinkedList**.

```
----------------------------
| Map = Array + LinkedList |
----------------------------
```

**Each Node contains the following:**

```java

class Node<K, V> {

    final int hashCode; // hashCode → Numeric representation of the key (used to find the bucket index)

    final K key;        // key → The element added to the HashSet

    V value;            // value → A dummy constant object called PRESENT (used to complete the key–value pair)

    Node<K, V> next;    // next → A pointer to the next node in the same bucket (used during collisions)
}
```
===============================================================================================================================================================


## How to Insert an Element Inside a HashMap?

 
```java

Syntax:

hmap.put(10, "java");

```
Internally, this calls:

```java

public V put(K key, V value)

```
## Step-by-Step Internal Process:

Step 1: Calculate the hash of the key

```
hash(10) = 10

Step 2: Create a Node at bucket index 10

```
```
BUCKET
+------+                 +----------+----------+----------+----------+
|  10  | ──────────────► | hashCode |   key    |  value   |  next    |        
+------+                 |   10     |   10     |  java    |  null    |
                         +----------+----------+----------+----------

```       

## Inserting Another Key:

```java

hmap.put(32, "python");

hash(32) = 32
```
But array size is 16. So we calculate:

32 % 16 = 0

Bucket index = 0
```
BUCKET
+------+                 +----------+----------+----------+----------+
|  0   | ──────────────► | hashCode |   key    |  value   |  next    |        
+------+                 |   0      |   32     | python   |  null    |
                         +----------+----------+----------+----------+

```
## Why modulus?

```
To keep the index within range (0 to 15), Java uses:

hash & (n - 1) // instead of hash % size

Where n = array length (e.g., 16)

32 & (16 - 1) = 32 & 15 = 0
```
## Collision Example:

```java

hmap.put(64, "RestAssured");

hash(64) = 64

64 % 16 = 0

Bucket index = 0 again, but index 0 already has key 32.

Both 32 and 64 are stored in the same bucket as a linked list chain >>  Collision Occurs!

```

## What is a Collision?

A collision happens when two different keys map to the same bucket index after hashing.

In this case: Keys: 32 and 64

Same bucket: 0


# What happens when collision occurs?

Collision will results in creating a linkedlist .

When multiple keys generate the same bucket index (after applying hash function), Java handles this by creating a **LinkedList** at that index.

Each new (key, value) pair is added as a **node** in the LinkedList.


```
BUCKET
+------+                 +----------+----------+----------+----------+
|  0   | ──────────────► | hashCode |   key    |  value   |  next    |        
+------+                 |   0      |   32     | python   |   ──┐    |
                         +----------+----------+----------+     │
                                                                ▼
                         +----------+----------+-------------+----------+
                         | hashCode |   key    |  value      |  next    |        
                         |   0      |   64     | RestAssured | null     |
                         +----------+----------+----------+--------------+

```   

## How to retrieve value from Linkedlist

hmap.get(64) // get the value of key 64

hash(64)= 64

64% 16 = 0

java goes to bucket 0, and check whether key 64 is present and return the value " restAssured".



## Is too many collissions good or bad?

```
Not good!

Collisions reduce the performance of HashMap by increasing the time to search, insert, or delete entries.
```

##  What happens when collisions increase?

> When multiple keys hash to the same bucket, they are stored in a **LinkedList**.

> If the number of nodes in a bucket exceeds **8**, Java (since version 8) converts the list into a **Red-Black Tree** to improve performance.

  - Tree lookup: O(log n)  
  - LinkedList lookup: O(n)

- **Default load factor**: 0.75 > This means when the number of entries exceeds **75% of the current capacity**, the map will **resize** (usually doubles the capacity).

##  What happens during resizing?

      > A new, larger array is created.

      > All existing entries are rehashed and rearranged to new buckets.

      > This is called rehashing, and it’s an expensive operation in terms of performance.

      > Frequent resizing can lead to performance issues. That’s why choosing a good initial capacity is important for large datasets.


## How many NULL KEYS hashmap can have?
```
Only one 
```
## How many NULL VALUES hashmap can have?
```
Multiple
```
## Who is the child of Hashmap?

```

Hashmap<String, String> name = new LinkedHashMap<String,String>()


LinkedHashMap extends HashMap > ie. LinkedHashmap is the child of hashmap

It inherits all behavior from HashMap but also maintains insertion order

We can use a LinkedHashMap object wherever a HashMap is expected — because of  inheritance and polymorphism.

```
 ## What is the Contract Between hashCode() and equals()?

 ```
 In Java, the hashCode() and equals() methods are tightly linked when using objects as keys in collections like HashMap, HashSet, and Hashtable.

 Contract Rule:
If two objects are equal (according to .equals()),
→ they must have the same hashCode.

But if two objects have the same hashCode,
→ they may or may not be equal (due to collisions).
```

## Why Override Both in Custom Classes?
```
Whenever you create a custom class that will be used as a key in HashMap, you must override both:

.equals() → to define when two objects are logically equal

.hashCode() → to ensure they go to the same bucket in the map

If you don't override them:

Two objects with same instance variable values will be treated as different keys

HashMap will treat them as different entries, even if they "look" the same
```

## Map Implementations Comparison

```

| Feature        | HashMap     | LinkedHashMap              | TreeMap        | Hashtable     |
|----------------|-------------|----------------------------|----------------|---------------|
| Ordering       | ❌ No       | ✅ Maintain Insertion order | ✅ Sorted keys | ❌ No         |
| Thread-safe    | ❌ No       | ❌ No                       | ❌ No          | ✅ Yes        |
| Null Key       | ✅ 1 key    | ✅ 1 key                    | ❌ No          | ❌ No         |
| Null Values    | ✅ Yes      | ✅ Yes                      | ✅ Yes         | ❌ No         |
| Speed          | ✅ Fast     | ✅ Fast                     | ❌ Slower      | ❌ Slower     |

```

## What is the difference between HashMap and Hashtable?

 ```
> HashMap is not thread-safe and non-synchronized.

> It should not be used in multithreaded environments without external synchronization (e.g., Collections.synchronizedMap() or ConcurrentHashMap).

> Hashtable is thread-safe and synchronized.

> Every method is synchronized, which makes it safe for concurrent access — but slower in performance.

> HashMap allows null key and values; Hashtable doesn’t

```

## What if two keys have the same hashCode()?
```

 HashMap uses .equals() to check for equality

> If different: added to the same bucket (collision handled by chaining)

> If equal: value is replaced

```