
# Map 

```
> Map is part of the Java Collections Framework, but it DOES NOT EXTEND the COLLECTION INTERFACE.  

> This is because Map stores KEY - VALUE Pairs, unlike other collections like `List` or `Set`, which store individual elements.

``` 


## Map Hierarchy 
```
             +----------------------+
             |      Map (interface) |                           Map (specifically HashMap) = Array (buckets) + LinkedList 
             +----------+-----------+
                        ↑
implements+-----------------------------------+implements
         ^             ^                       ^
No order |             | implements            |
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

 > Whenever we want to retrieve the value, we use the KEY that is associated with that VALUE. This is called LOOK UP OPERATION (Retrieval).

 > LOOK UP happens at super speed.

 > Perfomance of get() or the LOOK UP opearation is O(1) > Time Complexity. 

 > Example use: Counting frequencies, lookups (dictionary).

```

## What is Timecomplexity O(1) means?
```
> No matter how many key-value pairs are stored in the map, whether it's 10, 100, 1000, or even 1 million.

> Retrieving a value using a KEY will take the same amount of time > So TimeComplexity is Constant - O(1)

```

## What is Hashing ? How Hashing Works in HashMap ?
```
Hashing is the process of converting a LARGE OBJECT into a FIXED LENGTH INTEGER VALUE — called hashCode.

This integer value is the  bucket index where the NODE will be stored ( KEY & VALUE)

Reduces collisions and enables fast retrieval.

bucketIndex = hashCode % capacity;
```
```java

Example: Hashcode of an Integer Object

Integer i = 10; 

// or Integer i = new Integer(10); // // Both lines create Integer objects in different ways

System.out.println(i.hashCode()); // Output: 10 // Hashcode of any integer obj is number itself.

```
```
+-------------------------+
|  Integer is a Wrapper   |                                      //  Integer is a wrapper class.                    
|  class for int          |
+-----------+-------------+                                     //  Parent of integer is Object.
            |
            |                                                  // Object class provides a method called hashCode(), which generates hashcode using hashing to convert 
     +------+------+
     |   Object    |  ← Parent of Integer                       large objs into fixed len integer
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

31 (base multiplier) is a prime number used to reduce collisions.

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

So here LARGE STRING is converted to FIXED LENGTH INTEGER.

```
## What is the CONTRACT BETWEEN hashCode() and equals()?

```
When we create a custom class (like Student or Employee) and plan to store its objects in collections like HashMap, HashSet, or Hashtable,

we MUST OVERRIDE BOTH equals() and hashCode() — this is known as the contract between them.

These methods should be based on our class's instance variables, so that logically equal objects behave correctly in hash-based collections.

```
```
Two objects are considered equal when:

(1) Their hashCode() is the same.

(2) Their instance variable values match.

```

## Java's Contract Rule !

```
==========================================================================================================
If two objects are equal according to .equals() → they must return the same hashCode()

But if two objects have the same hashCode() → they may or may not be equal (because of hash collisions)

==========================================================================================================
```

## Code showing Java's Contract Rule !
```java


public class Test {
    public static void main(String[] args) {
        String s1 = "Java";
        String s2 = "Java";

        System.out.println(s1.equals(s2));       // true → content is same
        System.out.println(s1.hashCode());       // e.g., 2008614266
        System.out.println(s2.hashCode());       // 2008614266


    
    }
}
```
##  Why this proves the CONTRACT ?

```
Both s1 and s2 have the same content

So .equals() returns true

And their hashCode() is also the same

This proves:If two objects are equal using .equals() -> they must have the same hashCode().

```

## Why Should We Override Both in Custom Classes?
```
Whenever we create a custom class (like Student, Employee, etc.) and plan to use it in hash-based collections like HashMap or HashSet,
we must override both equals() and hashCode().

.equals() → defines logical equality (based on instance variables)

.hashCode() → ensures equal objects go to the same bucket

   > Overriding equals() and hashCode() ensures:

       >>Objects with same values are treated as equal

       >>Hash-based collections work as expected

```
##  What Happens If We Don’t Override?

``` java
// Even if two objects have same data:

Student s1 = new Student(1, "Athira");

Student s2 = new Student(1, "Athira");

// Without overriding equals() and hashCode()

System.out.println(s1.equals(s2)); // false 

System.out.println(s1.hashCode() == s2.hashCode()); // maybe false 

HashMap will treat s1 and s2 as different keys,even though they "look" the same! 

Overriding both makes sure our object behaves correctly in collections.
```
## Object.hashCode() vs Objects.hash() – What’s The Difference?

```
When overriding the hashCode() method in our custom class, we typically choose between two approaches:

1. Use the default hashCode() method inherited from the Object class.

2. Use the utility method Objects.hash() introduced in Java 7

```

## What is Object.hashCode() - The Default Method !

```
Object.hashCode() – from java.lang.Object

Object is the parent of all classes in Java.

Default method inherited by every class in Java.

Returns a hash based on the memory address (if not overridden).

Can lead to more collisions unless overridden properly.

Not null-safe.

Usually not used directly in custom hash logic.
```
```java

Object obj = new Object();
System.out.println(obj.hashCode());  // Prints the default hashCode based on memory address

```

## What is Objects.hash() – The Utility Method for Custom Classes !

```
Objects.hash() – from java.util.Objects

A utility method (static) introduced in Java 7

Used to generate a hash code by combining multiple fields

Internally calls Arrays.hashCode() → which is null-safe

Great for use in custom class implementations of hashCode()
```
```java

public int hashCode() {
    return Objects.hash(id, name); // Combines both fields
}

```

## Object.hash ( ) OR Objects.hash( ) - Which one to prefer?

```
When overriding the hashCode() method in our custom class, we have two options:

(1) Use the default hashCode() from the Object class. 
           
           OR

(2) Use the utility method Objects.hash() introduced in Java 7.

But which one should we use?

```
```
Always Prefer: Objects.hash() >> LESS COLLISIONS

Because it:

   > Combines multiple fields into one hash

   > is null-safe

   > Reduces hash collisions

   > Makes our code cleaner and readable

```
```
 Object.hashCode() (Default)

   > Comes from java.lang.Object

   > Based on memory address (if not overridden)

   > Not null-safe

   > Not useful for checking equality of two objects with same data

   > Always choose the one with less collision

```

##  How to Properly Override hashCode() and equals() in a Custom Class !



```java
import java.util.Objects;

class Employee { // Custom class to show equals() and hashCode()
    int id;
    String name;

    Employee(int id, String name) {
        this.id = id;
        this.name = name;
    }

    // Preferred way to override hashCode()
    // Uses Objects.hash() to combine multiple fields and reduce collision

    @Override
    public int hashCode() {
        return Objects.hash(id, name);
    }

    // Override equals() to define logical equality
    // Two Employee objects are equal if their id and name are the same


   // To generate the following - Right-click inside the class > Select Generate → equals() and hashCode()
    @Override                                   
    public boolean equals(Object o) {
        if (this == o) return true;  // If both references point to same object
        if (!(o instanceof Employee)) return false; // If not same class, return false
        Employee e = (Employee) o;
        return this.id == e.id && this.name.equals(e.name);
    }
}

-------------------------------------------------------------------------------------------------------------------

public class EmployeeRunner {

    public static void main(String[] args) {

         //  Same data → equals() returns true
        Employee e1 = new Employee(1, "Athira");
        Employee e2 = new Employee(1, "Athira");

          // hashCode() based on data, so both are equal
        System.out.println(e1.hashCode());     // Same as e2
        System.out.println(e2.hashCode());     // Same as e1
        System.out.println(e1.equals(e2));     // true 
    }
}
```
## Internal Working Of Map !

```
> Map consists of an array/table which has a size of 16, with index from 0 to 15. 

> Each index is called BUCKET.

> When we create a hashmap -  HashMap <Integer,String> hmap = new HashMap(), the follwing table will be created internally!

```
## HashMap Memory Layout !

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
```
**Each bucket can hold one or more NODES, depending on how many elements map to the same index.**

**Each node is going to be LinkedList**.
```
```
----------------------------
| Map = Array + LinkedList |
----------------------------
```

## NODE !

```java

NODE is the the actual object stored inside a bucket.

Each NODE contains the following:

class Node <K, V> {

    final int hashCode; // hashCode → Numeric representation of the key (used to find the bucket index)

    final K key;        // key → The element added to the HashSet

    V value;            // value → A dummy constant object called PRESENT (used to complete the key–value pair)

    Node <K, V> next;    // next → A pointer to the next node in the same bucket (used during collisions)
}
```

## How to Insert an Element Inside a HashMap?

 
```java

Syntax:

hmap.put(10, "java");

Internally, this calls:

public V put(K key, V value)

When we call hmap.put(10, "java"), it triggers the put(K key, V value) method defined in the Map interface and implemented by the HashMap class.

The HashMap then calculates the hash code for the key, finds the correct bucket, and stores the key-value pair as a Node in that location.

```
## Step-by-Step Internal Process:

**Step 1: Calculate the hash of the key**

```
hash(10) = 10  // In Java, Integer's hashCode() returns the number itself

```

**Step 2: Create a Node at bucket index 10.**

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

```
Array size is 16. So we calculate: 32 % 16 = 0 > Remainder is 0, So Bucket index = 0.

BUCKET
+------+                 +----------+----------+----------+----------+
|  0   | ──────────────► | hashCode |   key    |  value   |  next    |        
+------+                 |   0      |   32     | python   |  null    |
                         +----------+----------+----------+----------+
```
## Why Modulus (or Bitwise AND)?

```
We often explain HashMap index calculation using %, because it's easy to understand.

Internally (in real HashMap source code): Java actually uses bitwise AND (&) instead of % to keep the index within range (0 to 15)

hash & (n - 1) Where n = array length (e.g., 16) // instead of hash % size

32 & (16 - 1) = 32 & 15 = 0

Why Java Uses & Instead of %?  Because & is much faster than %

HashMap always maintains its array size as a power of 2 (16, 32, etc.), so hash % size and hash & (size - 1) will always give the same result.

```
## Collision Example

```java

hmap.put(64, "RestAssured");

hash(64) = 64

64 % 16 = 0

Bucket index = 0, but index 0 already has key 32.

Both 32 and 64 are stored in the same bucket as a linked list chain >>  Collision Occurs!

```

## What is a Collision?
```
A collision happens when two different KEYS map to the same bucket index after hashing.

In this case: Keys: 32 and 64

Same bucket: 0
```

## What happens when collision occurs?

```
Collision will results in creating a linkedlist .

When multiple keys generate the same bucket index (after applying hash function), Java handles this by creating a LINKEDLIST at that index.

Each new (key, value) pair is added as a NODE in the LinkedList.

```
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

## How to retrieve value from Linkedlist ?

```
hmap.get(64) // get the value of key 64

hash(64)= 64

64% 16 = 0

java goes to bucket 0, and check whether key 64 is present and return the value " restAssured".
```


## Is too many collisions good or bad?

```
Not good!

Collisions reduce the performance of HashMap by increasing the time to search, insert, or delete entries.
```

## What Happens When Collisions Increase and How Java Handles It ?

```
> When multiple keys hash to the same bucket, they are stored in a LINKEDLIST.

> If the number of nodes in a bucket exceeds  8, Java (since version 8) converts the list into a **Red-Black Tree** to improve performance.

  - Tree lookup: O(log n)  
  - LinkedList lookup: O(n)

- DEFAULT LOAD FACTOR: 0.75 > This means when the number of entries exceeds 75% of the current capacity, the map will RESIZE (usually doubles the capacity).

> What happens during RESIZING ?

      > A new, larger array is created.

      > All existing entries are rehashed and rearranged to new buckets.

      > This is called REHASHING, and it’s an EXPENSIVE operation in terms of performance.

      > Frequent resizing can lead to performance issues. That’s why choosing a good initial capacity is important for large datasets.
```

## How many null KEYS hashmap can have?
```
Only one 
```
## How many null VALUES hashmap can have?
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
    >It should not be used in multithreaded environments without external synchronization (e.g., Collections.synchronizedMap() or ConcurrentHashMap).

> Hashtable is thread-safe and synchronized.
   > Every method is synchronized, which makes it safe for concurrent access — but slower in performance.

> HashMap allows one null key and multiple null values.

> Hashtable does not allow any null key or null values.

```

## What if two keys have the same hashCode()?
```

If two keys have the same hashCode(), HashMap uses .equals() to further check if they are logically equal:

 If .equals() returns false →
   > Both keys are stored in the same bucket (collision is handled using a linked list or tree)

 If .equals() returns true →
   > The existing value is replaced with the new one (duplicate key)

```

## Commonly Used Methods in Java Map 

```java

public static void main(String[] args) {

        // Create a HashMap with Integer as key and String as value
        Map<Integer, String> employeeMap = new HashMap<>();

        // put(key, value) → Adds entries to the map
        employeeMap.put(101, "A");
        employeeMap.put(102, "R");
        employeeMap.put(103, "S");

        // Adding a duplicate key replaces the old value
        employeeMap.put(102, "C"); // replaces "R"

        // Print entire map
        System.out.println("Employee Map: " + employeeMap); 
        // Output: {101=A, 102=C, 103=S}

        // get(key) → Retrieves the value associated with the key
        System.out.println("Get key 101: " + employeeMap.get(101)); // A
        System.out.println("Get key 999: " + employeeMap.get(999)); // null (key doesn't exist)

        // ---------------------------------------
        //  Internal hashing and bucket indexing
        // ---------------------------------------

        // Hash code calculation of keys (used internally to find bucket index)
        // hashCode() returns a number used by Java to decide where to store the entry
         System.out.println("Hash of key 101: " + Integer.valueOf(101).hashCode()); 

        // To find the bucket index → Java does: hash % arraySize (usually 16 initially)
        System.out.println("101 % 16 (bucket index): " + (101 % 16));
        System.out.println("102 % 16 (bucket index): " + (102 % 16));
        System.out.println("103 % 16 (bucket index): " + (103 % 16));

        // So keys 101, 102, and 103 are stored at different buckets based on the result

        // keySet() → returns all keys in the map
        Set<Integer> keySet = employeeMap.keySet();
        System.out.println("All keys in employeeMap: " + keySet);

        // entrySet() → for traversing all key-value pairs
        System.out.println("Traversing employeeMap:");
        for (Map.Entry<Integer, String> entry : employeeMap.entrySet()) {
            System.out.println(entry.getKey() + " -----> " + entry.getValue());
        }

        // ---------------------------------------
        //  Case Sensitivity in Map keys
        // ---------------------------------------

        Map<String, String> studentMap = new HashMap<>();
        studentMap.put("John", "Present");

        // Case mismatch: returns null
        System.out.println("studentMap.get("john"): " + studentMap.get("john")); // null

        // Correct key (case matched): returns value
        System.out.println("studentMap.get("John"): " + studentMap.get("John")); // Present 

        //  Map keys are case-sensitive!
        // "John" and "john" are considered two different keys
    }
}
```

## Summary

```
| Method            | Purpose                                  |
| ----------------- | -----------------------------------------|
| put(key, value)   | Adds or replaces a key-value pair        |
| get(key)          | Retrieves the value for a given key      |
| keySet()          | Returns a Set of all keys                |
| entrySet()        | Returns a Set of all key-value entries   |

```









