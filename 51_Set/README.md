# SET - Set is the only interface in the Collection framework that is idempotent by design ! 

```

                         Iterable (interface)
                               ▲
                               |
                       Collection (interface)
                               ▲
                               |
                          Set (interface)
                               ▲
        ┌──────────────────────┼────────────────────────┐
        │                      │                        │
   HashSet (class)     LinkedHashSet (class)      TreeSet (class)
                                                        ▲
                                                        |
                                      SortedSet & NavigableSet (interfaces)

```

```
Non Linear Data Structure which store only unique values.

Only unique values are stored - No duplicates allowed.

Idempotent** in nature → Adding the same element multiple times has no effect after the first addition.

Idempotent means - How many times the operation is performed, results remain the same.

Can have only one NULL value.

Order of the elements may or may not be maintained depending upon the implementation(whether we use Hashset or LinkedHashset).

Hashset -  Do not maintain order.

LinkedHashset - Maintain order.

List does not hav any implementation for retrieving elements in sorted order.

Can retrieve elements in sorted order if Treeset is used.

No get() Method in Set. In Set, elements are not stored by index, so we cannot use get(index) like we do with a List.

Set use Iterator or for-each loop to traverse the elements one by one.
```


## Hashset
```
Hashset is a class which implements Set Interface.

Hashset internally uses hashmap, so insertion order is not preserved. Elements appear in random order when iterated.

Single null value is allowed in hashset.

HashSet extends AbstractSet.

AbstractSet implements Set.
```

How to declare a Hashset?

```java

HashSet<String> hashset = new HashSet<String>();

```

## HashSet Methods

``` java
        hashset.add("India");
        hashset.add("Scotland");
        hashset.add("Netherlands");
        hashset.add("Kashmir");// Kasmir will be added once as set is idempotent
        hashset.add("Kashmir");
        hashset.add("Kashmir");
```

## How to maintain order in a set?

## By using Linked Hashset.

``` java
LinkedHashSet<String> Linkedhashset = new LinkedHashSet<>();
        Linkedhashset.add("India");
        Linkedhashset.add("Scotland");
        Linkedhashset.add("Netherlands");
        Linkedhashset.add("Kashmir");// Kashmir will be added once as set is idempotent
        Linkedhashset.add("Kashmir");
        Linkedhashset.add("Kashmir");
        System.out.println("LinkedHashset is" + Linkedhashset);
```


## Treeset
```java
TreeSet<String> treeSet = new TreeSet<>();
        treeSet.add("India");
        treeSet.add("Scotland");
        treeSet.add("Netherlands");
        treeSet.add("Kashmir");// Kasmir will be added once as set is idempotent
        treeSet.add("Kashmir");
        treeSet.add("Kashmir");
        System.out.println("Treeset is" + treeSet);
    
```

## How to retrieve elements from Set?
```

The Set interface does **not** provide a `get()` method — because Sets are **not index-based.

To access elements, we use Iterator (from the Iterator interface) or **enhanced for-each loops.

```
## For each for Iteration

```java
for (String data : treeSet){
            System.out.println(data);
        }
```


## Iterator for traversing through set

```java
Iterator<String> dataIterator = treeSet.iterator();
        while(dataIterator.hasNext()){
            System.out.println(dataIterator);
        }
```


Iterator<String>
➤ Declares a variable dataIterator of type Iterator (used to loop through String elements).

treeSet.iterator()
➤ Calls the iterator() method on treeSet.
➤ This method returns an Iterator object that knows how to go through the TreeSet.

Assignment (=)
➤ The returned Iterator object is stored in the dataIterator variable.

while (dataIterator.hasNext())
➤ Checks if there is a next element available in the set.
➤ Returns true if there is one, otherwise false.

dataIterator.next()
➤ Retrieves the next element in the set.
➤ Moves the pointer forward to the next item.

System.out.println(...)
➤ Prints the current element.


Iterator<String>	We are declaring a variable dataIterator of type Iterator Interface — used to loop through String values.
treeSet.iterator()	This calls the iterator() method on treeSet, which returns an Iterator object.

Iterator is an interface from java.util.

iterator() is a method inside the Iterable interface.

All collections like List, Set, etc., implement Iterable, so we can use .iterator() on them.


🔸 LinkedHashSet → ✅ Maintains insertion order

🔸 HashSet → ❌ No guaranteed order

🔸 TreeSet → ✅ Sorted order (not insertion order)



## Methods in set

```java

// isEmpty() - check whether a set is empty or not
                HashSet<String> set =  new HashSet<>();
                  set.isEmpty();
        System.out.println(set.isEmpty());

        //size() - total num of elements in set
        System.out.println(hashset.size());

        // contains() - check whether a particular obj is present or not in the set - returns boolean
        System.out.println(hashset.contains("India"));
        System.out.println(hashset.contains("Delhi"));


        // remove() - remove an obj from set
        System.out.println(hashset.remove("Kashmir"));
        System.out.println(hashset);
        }

```

## How to access elements in set through index?

Not possible as set doesn't have any index

# Is there a way where we can access set elemenst through index? 

Yes, convert it into set and then we can access elements using get().


``` java 

HashSet<String> hashset = new HashSet<String>();
        hashset.add("India");
        hashset.add("Scotland");
        hashset.add("Netherlands");
        hashset.add("Kashmir");// Kasmir will be added once as set is idempotent
        hashset.add("Kashmir");
        hashset.add("Kashmir");

        ArrayList<String> al = new ArrayList<>(hashset);
        System.out.println(al);
        System.out.println(al.get(0));
        ```

        
