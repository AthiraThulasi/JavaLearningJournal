
## Maps

## Map Hierarchy 
```
             +----------------------+
             |      Map (interface) |
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

Used to compute bucket index in HashMap

This hash is used to calculate the bucket index.

Enables fast retrieval
• Reduces collisions (ideally)

bucketIndex = hashCode % capacity;
```
```java

Example: Hashcode of an Integer Object

Integer i = 10; // or Integer i = new Integer(10);

System.out.println(i.hashCode()); // Output: 10

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
|         String s = "abc"     |
+------------------------------+

hashCode formula:
s[0]*31^(n-1) + s[1]*31^(n-2) + ... + s[n-1]*31^0

= 'a'*31^2 + 'b'*31^1 + 'c'*31^0
= 97*961  + 98*31   + 99*1
= 93217

✔️ String hashCode() depends on characters and order.
✔️ Same characters in different order → different hashCode.

Used in:
+-----------------+
| HashMap         |
| HashSet         |
| Hashtable       |
+-----------------+

Note:
- Once created, String is immutable
- So hashCode stays the same → fast lookups




```
## 