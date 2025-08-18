## Collection  - Brain Teasers!

### Q1: What’s the difference between Collection and Collections? 

```
| Collection                                               | Collections                                            |
| -------------------------------------------------------- | ------------------------------------------------------ |
| Interface from java.util                                 | Utility class from java.util                           |
| Extends Iterable                                         | Final class with only static helper methods            |
| Base for List, Set, Queue                                | Offers methods like sort(), reverse(), shuffle()       |
| Used to define collection types                          | Used to perform operations on collections              |
| Example: Collection<String> names = new ArrayList<>();   | Example: Collections.sort(myList);                     |

```

### Q2: How is Uniqueness Maintained in HashSet and HashMap?

```
Where did we study hashCode() + equals()?

We studied this in the context of both HashSet and HashMap, because:

Both use HASHING to store data

Both rely on hashCode() and equals() to check for uniqueness

>  HashSet:

     - Internally uses a HashMap where each element is added as a key.

     - set.add("apple") → becomes → map.put("apple", PRESENT)

> Before inserting:

    - First checks the element’s hashCode() to find the bucket

    - Then uses equals() to ensure it’s not a duplicate

> HashMap:
 
    - Keys are unique.

If two keys have the same hashCode(), it uses equals() to resolve collisions.

Duplicate keys overwrite the old value.
```

### Q3: How does HashMap handle collisions?

``` java

WWhen two keys have the same hash index, Java creates a LinkedList inside that bucket to store both entries.

Each new node is added to that list — this is how HashMap handles collisions.

map.put(16, "Java");

map.put(32, "Python"); // if both map to index 0 (16%16 = 0, 32%16 = 0)
```


### Q4: What is the default initial capacity of a HashMap?

```
16 buckets (0 to 15)

And the load factor is 0.75 → so it resizes when it's 75% full.

```

### Q5. What is the default initial capacity of an ArrayList?
```
10 elements

When full, it increases capacity by 50%

new capacity = old capacity + (old capacity / 2)
```

### Q5. Which data structure maintains insertion order? Which doesn’t?
```
|  Maintains Insertion Order  |  Does NOT Maintain Order  |
| --------------------------- | ------------------------- |
| LinkedHashSet               | HashSet                   |
| LinkedHashMap               | HashMap                   |
```
### Q6. Difference between HashMap, TreeMap, and LinkedHashMap ?
```
| Feature     | HashMap         | TreeMap                  | LinkedHashMap              |
| ----------- | --------------- | -------------------------| ------------------------   |
| Order       |  No order       |  Sorted (by key)          | Insertion order           |
| Null Keys   | 1 allowed       | Not allowed               |  1 allowed                |
| Performance |  Fastest        |  Slower (due to sorting)  |  Medium                   |
| Use Case    | General storage | Need sorted keys            Access in inserted order  |
```

### Q7. What happens if you store the same key twice in a Map?

```java

The value is overwritten.

map.put(1, "Java");
map.put(1, "Python"); // replaces previous value
Now map.get(1) will return "Python".
```

### Q8. Is ArrayList thread-safe? What about Vector?

| Class       | Thread-Safe? | Synchronized? |
| ----------- | ------------ | ------------- |
| ArrayList   |  No          |  No           |
| Vector      |  Yes         |  Yes          |


### Q9. What is ConcurrentModificationException?
```
ConcurrentModificationException occurs when a collection is modified while being iterated using something like a for-each loop.

Use Iterator with .remove() or CopyOnWriteArrayList to avoid this.
```

### Q10. What is the difference between List and ArrayList?
```
List is an interface.

ArrayList is a class that implements List.
```

## Q11. Difference between ArrayList and LinkedList?
```
| Feature            | ArrayList                | LinkedList                |
| ------------------ | ------------------------ | ------------------------- |
| Data Structure     | Dynamic Array            | Doubly Linked List        |
| Access             | Fast (index-based)       |  Slow (needs traversal)   |
| Insertion/Deletion | Slow (shifting needed)   |  Fast (no shifting)       |
| Use Case           | Read-heavy               | Insert/delete-heavy       |
```

### 12. Which is faster – ArrayList or LinkedList?
```
For searching, ArrayList is faster.

For inserting/deleting, LinkedList is better.
```

### Q13. Can we store null in ArrayList or LinkedList?
```
 Yes, both allow multiple null values.
```

### Q14. How to convert List to ArrayList?
```java

List<String> list = new ArrayList<>();

ArrayList<String> arrayList = new ArrayList<>(list);
```
### Q15. Can we convert Array to List?

```java

String[] arr = {"a", "b"};

List<String> list = Arrays.asList(arr);

```

### Q16: What is the difference between HashSet and LinkedHashSet?
```
| Feature     | HashSet     | LinkedHashSet  |
| ----------- | ----------- | ------------------ |
| Order       |  Unordered  | Insertion order  |
| Performance | Faster      |  Slightly slower |
```

### Q17: Does Set allow duplicates?
```
 No. Set maintains uniqueness using hashCode() and equals().
```

### Q18. Can Set contain null?
```
HashSet allows one null value.

 ```

### Q19. How do different Set and Map types handle null?

| Type            | Allows NULL Key / Value?  |             Notes                                          |
| --------------- | --------------------------| ---------------------------------------------------------- |
| HashSet         |  Yes (1 null value)       | Internally uses HashMap, stores NULL in bucket 0           |
| LinkedHashSet   |  Yes (1 null value)       | Maintains insertion order, still uses HashMap internally   |
| TreeSet         |  No                       | Throws NullPointerException — uses compareTo() to sort     |
| HashMap         |  Yes (1 null key)         | Stored in bucket 0                                         |
| LinkedHashMap   |  Yes (1 null key)         | Preserves insertion order                                  |
| TreeMap         |  No                       | No NULL keys — throws exception due to key comparison     |


### Q20 How many null keys and values can a HashMap have?

```
| Element Type | Allowed in `HashMap`? | How Many?                |
| ------------ | --------------------- | ------------------------ |
| null key     |  Yes                  | Only 1 null key.         |
| null value   |  Yes                  | Multiple null values.    |

```

### Q21: Difference between HashMap and LinkedHashMap?

 ```
 | Feature     | `HashMap`   | `LinkedHashMap`   |
| ----------- | -----------  | ----------------- |
| Order       | Unordered    |  Insertion order  |
| Null Keys   | 1 allowed.   |  1 allowed        |
| Thread-Safe | No           |  No               |

```

### Q22. What happens if you insert a duplicate key into a HashMap?
```
The new value replaces the old one associated with that key.

```
### Q23.  Difference between keySet() and entrySet()?

```
keySet() returns only keys.

entrySet() returns key-value pairs.
```

### Q24. Convert Set to List?

```java

Set<String> set = new HashSet<>();

List<String> list = new ArrayList<>(set);
```
### Q25. Convert Map keys to List?
```java

List<String> keys = new ArrayList<>(map.keySet());

```
### Q26. Convert Map values to List?

```java

List<String> values = new ArrayList<>(map.values());

```
### Q27. What is Iterable in Java?

```
It’s the root interface for all collection classes that can be looped using for-each.

It provides the method: Iterator<T> iterator();

All classes like List, Set, Queue implement Iterable.
```

### Q28. What is the difference between Iterable and Iterator?

```
| Feature       | Iterable                           | Iterator                            |
| ------------- | ---------------------------------- | ----------------------------------- |
| Type          | Interface with iterator() method   | OBJECT returned by iterator()       |
| Purpose       | Used to get an Iterator            | Used to TRAVERSE the collection     |
| Scope         | One per collection class           | One per iteration                   |
| Introduced in | Java 5                             | Used since Java 1.2                 |

```

### Q29. How to use Iterator to loop through a List?

```java

List<String> names = new ArrayList<>();

Iterator<String> it = names.iterator();

while (it.hasNext()) {
    System.out.println(it.next());
}

```
### Q30. What happens if you modify a List while iterating? why?

```
 ConcurrentModificationException is thrown.

Java’s iterators are fail-fast. That means: If the structure of the list changes while we're iterating over it, the iterator detects it and fails 
immediately to prevent unpredictable behavior.

 ```

### Q31. How to safely remove elements during iteration ?

```java

Iterator<String> it = list.iterator();
while (it.hasNext()) {
    String val = it.next();
    if (val.equals("apple")) { // "apple" is the target value to delete
        it.remove(); //  Safe removal
    }
}

```
### Q32. Does Iterator work on Arrays?

```
No. Arrays do not implement Iterable.

Use traditional for loop or Arrays.asList(array) to convert and iterate.
```

### Q33. Is there a difference between iterate() and iterator() in Java?

```
| Method       | Is it Exist? | Belongs To               | Purpose                                            |
| ------------ | -----------  | ------------------------ | -------------------------------------------------- |
| iterator()   | Yes          | Iterable                 | Returns an `Iterator` to loop through a collection |
| iterate()    | Yes          | Stream (static method)   | Used to generate streams, not used for collections |


Every class that implements Iterable (like List, Set) must override iterator().

 iterate() – Not a valid method in core Java Collections.

 Stream.iterate() - exists in Java 8 - used to generate a stream of elements.

```
### Q.34. What are the key methods in the Iterator interface?
```
| Method      | Purpose                                                           |
| ----------- | ----------------------------------------------------------------- |
| hasNext()   |  Checks if more elements are available to iterate                 |
| next()      |  Returns the next element in the collection                       |
| remove()    |  Removes the current element from the collection (safe removal)   |
```

### Q35. What are the methods of the Iterable interface?
```
| Method              | Since  | Purpose                                      |
| ------------------- | ------ | -------------------------------------------- |
| iterator()          | Java 5 | Returns an `Iterator` to traverse elements   |
| forEach             | Java 8 | Performs action for each element (lambda)    |
| spliterator()       | Java 8 | Returns a `Spliterator` for advanced looping |
```

### Q36. What is the relationship between Iterable and Iterator interfaces?

```
| Interface  | Package     | Role / Level                                  | Purpose                                                |
| ---------- | ----------- | --------------------------------------------- | ------------------------------------------------------ |
| Iterable   | java.lang   | Root interface of Collection Framework        | Represents a collection that can be iterated           |
| Iterator   | java.util   | Helper interface                              | Provides methods to iterate over elements one by one |


For better understanding: 

| Interface  | Role                                                                                |
| ---------- | ----------------------------------------------------------------------------------- |
| Iterable   | Just says: “Hey, I SUPPORT iteration — call my iterator() method!”                |
| Iterator   | The actual object that PERFORMS the iteration (has hasNext(), next(), etc.)     |


Iterable enables iteration
Iterator does the iteration


```

