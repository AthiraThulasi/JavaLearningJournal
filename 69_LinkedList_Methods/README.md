## LinkedList Methods

### Let’s Revisit the Java Collections Hierarchy : How LinkedList fits into the Java Collections Framework?


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

 Need a quick refresher on Interface & Inheritance? Click here to revise !

## How we define and initialize a LinkedList in Java ?
```

Java creates a LinkedList object that can store String values, and assign it to the variable namesList.

LinkedList<String> namesList = new LinkedList<>();
↑                  ↑           ↑
│                  │           └───► 🟩 Object Creation (heap memory)
│                  └──────────────► 🟨 Reference Variable (stored in stack memory)
└────────────────────────────────► 🟦 Reference Type 


```

## How LinkedList is Connected to List and Deque Interfaces ?


### LinkedList is a class which implements both - (1)  List interface (2) Deque interface (double-ended queue).

 **> Deque extends Queue, so LinkedList indirectly supports Queue methods too, So LinkedList can behave like a List, Queue, and Deque.**

```

          ┌───────────────┐        ┌──────────────┐
          │   Queue (I)   │        │   List (I)   │
          └──────▲────────┘        └──────▲───────┘
                 │                          │
              extends                    implements
                 │                          │
          ┌──────┴───────┐                  ┴───────┐
          │  Deque (I)   │                          │
          └──────▲───────┘                          │
                 │     implements                   │
                 └───────────────────────────────┐  │
                                                   
                                       ┌────────────────────┐
                                       │ LinkedList (class) │
                                       └────────────────────┘

                                       
```
## Why do we say LinkedList implements List and Deque, and not Queue?

**Because in the Java Collections Framework - LinkedList directly implements: List & Deque.**

```java
public class LinkedList<E> implements List<E>, Deque<E>

> LinkedList is a class that follow the rules of both List and Deque interfaces.

> That means LinkedList must provide implementations for all the methods declared in both interfaces.

> Since Deque extends Queue, LinkedList also inherits all the behaviors of a Queue.

```

## How does Queue fit ?

 **LinkedList indirectly supports Queue behavior, But it doesn’t directly implements Queue — instead, it implements Deque, which extends Queue.**

```

Queue is a parent
Deque is a child of Queue
LinkedList implements the child (Deque), so it automatically gets the parent's behavior (Queue).

           ┌───────────────┐
           │  Queue (I)    │
           └──────▲────────┘
                  │
               extends
                  │
           ┌──────┴───────┐
           │  Deque (I)   │
           └──────▲───────┘
                  │
               implements
                  │
           ┌──────┴────────────┐
           │ LinkedList (class)│
           └───────────────────┘



```
## When & Why We Use List as the Reference Type ?


### In OOPs, we learnt that the reference type should be the parent, and the object should be the child — this is known as upcasting or runtime polymorphism.

```java

List<String> namesList = new LinkedList<>();       // polymorphism or upcasting
              ↑               ↑
         Parent              Child's Object
        (Reference Type)      

```
1. List is the parent interface, and LinkedList is the child class that implements it.

2. Because of polymorphism (upcasting), we can easily switch between different List implementations like ArrayList, Vector, LinkedList, etc., without rewriting our code.

3. This approach is great for flexibility.

4. Our code becomes more reusable and follows good design principles.

```java

    > List<String> namesList = new LinkedList<>();
    > List<String> namesList = new ArrayList<>();

```

## Limitations of Using List as the Reference Type When Accessing Both List & Deque Methods ?

**When we want to use methods that belong specifically to the LinkedList class and the Deque interface, if we use List as parent type**

**(1) We can only access methods defined in the List interface.**

**(2) We cannot access methods that are specific to LinkedList and Deque.**

**(3) Even though the object is a LinkedList, Java limits method access based on the reference type — in this case, the parent interface List.**



```java
LinkedList<String> namesList = new LinkedList<>();

This gives us full access to all methods of List, Deque, and LinkedList.
```

```java
List<String> namesList = new LinkedList<>();

This gives us access to only the methods defined in the List interface,as Java limits access based on the reference type (List, in this case — the parent interface).
```

## Adding Elements to LinkedList

> LinkedList is implemented as a Doubly Linked List, meaning each node holds references to both its previous and next nodes, allowing traversal in both forward and backward directions.

> LinkedList maintains order of insertion.

> LinkedList supports duplicates and allows null values.

```java

    LinkedList<String> namesList = new LinkedList<String>();

    namesList.add("python");

    namesList.add("java");

    namesList.add("postman");

    namesList.add("java");// Duplicates allowed

    namesList.add(null);// Null is allowed in LinkedList

    ArrayList<String> al = new ArrayList<>()

    al.add("JMeter");// ArrayList and LinkedList are using the SAME add() method from the List interface.

    al.add("cypress");
```
## How Elements Look in Memory (Doubly Linked List)

Not sure how a Doubly Linked List works?  [Click here to understand how it works]

```
       Address: 001
┌────────┬──────────┬────────┐
│ Prev   │  Data    │ Next   │ INDEX 0
│ null   │ python   │ 002    │
└────────┴──────────┴────────┘
     ▲                      │
     │                      ▼
Address: 002
┌────────┬──────────┬────────┐
│ Prev   │  Data    │ Next   │ INDEX 1
│ 001    │ java     │ 003    │
└────────┴──────────┴────────┘
     ▲                      │
     │                      ▼
Address: 003
┌────────┬──────────┬────────┐
│ Prev   │  Data    │ Next   │ INDEX 2
│ 002    │ postman  │ 004    │
└────────┴──────────┴────────┘
     ▲                      │
     │                      ▼
Address: 004
┌────────┬──────────┬────────┐
│ Prev   │  Data    │ Next   │ INDEX 3
│ 003    │ java     │ 111    │
└────────┴──────────┴────────┘

```




## Inserting Elements to a particular index in LinkedList

**> Insertion in a LinkedList is fast because elements are inserted by simply updating the links (pointers) between nodes, without shifting other elements as in an ArrayList.**


```java

namesList.add(1, "javascript"); //  Inserting the element at INDEX 1 

```

```

**The node that was previously at index 1 (address 002) moved to index 2, and all the following nodes were pushed forward.**

       Address: 001
┌────────┬────────────┬────────┐       INDEX 0
│ Prev   │   Data     │ Next   │
│ null   │  python    │ 005    │
└────────┴────────────┴────────┘
     ▲                          │
     │                          ▼
Address: 005
┌────────┬────────────┬────────┐       INDEX 1
│ Prev   │   Data     │ Next   │
│ 001    │ javascript │ 002    │
└────────┴────────────┴────────┘
     ▲                          │
     │                          ▼
Address: 002
┌────────┬──────────┬────────┐        INDEX 2
│ Prev   │  Data    │ Next   │
│ 005    │ java     │ 003    │
└────────┴──────────┴────────┘
     ▲                        │
     │                        ▼
Address: 003
┌────────┬──────────┬────────┐        INDEX 3
│ Prev   │  Data    │ Next   │
│ 002    │ postman  │ 004    │
└────────┴──────────┴────────┘
     ▲                        │
     │                        ▼
Address: 004
┌────────┬──────────┬────────┐        INDEX 4
│ Prev   │  Data    │ Next   │
│ 003    │  java    │ 111    │
└────────┴──────────┴────────┘

```
## Remove an Element From LinkedList

```
(1) remove()            ➤ Removes the head (first element) and returns it  
(2) remove(int index)   ➤ Removes the element at the specified index and returns it
(3) remove(object)      ➤ Removes the first occurence of the object.

```

```java

// (1) Removes the head (first element) and returns it
String data = namesList.remove();  
System.out.println(data);  // Output: python


// (2) Removes the element at index 1 and returns it
String data1 = namesList.remove(1);  
System.out.println(data1);  // Output: javascript


// (3) Removes the first occurrence of the object "java" - returns boolean - indicating whether the object was found and removed!
boolean data2 = namesList.remove("java");
System.out.println(data2);  // Output: true

```
### Note:

> Collections store objects, not primitive type.

> Java Collections use Generics, which only work with objects — not primitive types. So, we use wrapper classes like Integer, Double, Character, etc., instead of int, double, or char.

Revisit Wrapper Classes ➜](../19_Wrapper_Class/README.md)

> remove(Object o) returns a boolean, indicating whether the object was found and removed.


## get(), set() and contains() Methods!

```
(1) get(int index)       ➤ Retrieves the element at the specified index  
(2) set(int index, val)  ➤ Updates the element at the specified index with a new value  
(3) contains(object)     ➤ Returns true (boolean), if the specified element exists in the list

```

```java

(1) get() - Retrieve element
System.out.println(namesList.get(0));  // Output: postman


(2) set() - Update an element at a specific index
namesList.set(0, "Playwright");        // Replaces "postman" with "Playwright"
System.out.println(namesList);         // Output: [Playwright, null]


(3) contains() - Check if an element exists in the list
boolean data4 = namesList.contains("Playwright");
System.out.println(data4);             // Output: true

```

### Add Elements from ArrayList to LinkedList !

```
addAll(Collection c) ➤ Appends all elements from the specified collection to the list
```

```java
boolean result = namesList.addAll(al);              // nameList has [Playwright, null]
                                                   // adding [JMeter, cypress] from ArrayList al we have created at the beginning.
System.out.println(namesList);
                                                 // Output: [Playwright, null, JMeter, cypress]
```

## Common Methods

```
(1) size()               ➤ Returns the number of elements in the LinkedList  
(2) clear()              ➤ Removes all elements from the LinkedList, making it empty
```

```java

(1) size()

System.out.println(namesList.size());  // Returns the number of elements in the LinkedList

(2) clear()

namesList.clear();  // Removes all elements from the LinkedList
System.out.println(namesList);  // Output: [] ➤ List is now empty

```


## Return Types of LinkedList Methods We Have Seen So Far

###  Methods That Return `boolean`

| Method                        | Return Type | Description                                             |
|-------------------------------|-------------|---------------------------------------------------------|
| `remove(Object o)`            | `boolean`   | Removes the first occurrence of the specified element   |
| `contains(Object o)`          | `boolean`   | Checks if the list contains the specified element       |
| `addAll(Collection c)`        | `boolean`   | Adds all elements from another collection to the list   |

---

###  Methods That Return an Element (Object)

| Method                        | Return Type | Description                                             |
|-------------------------------|-------------|---------------------------------------------------------|
| `get(int index)`              | `Element`   | Retrieves the element at the given index                |
| `set(int index, val)`         | `Element`   | Updates and returns the previous value at that index    |
| `remove()`                    | `Element`   | Removes and returns the first element (head)            |
| `remove(int index)`           | `Element`   | Removes and returns the element at the specified index  |

---

###  Methods That Return Other Types

| Method              | Return Type | Description                                  |
|---------------------|-------------|----------------------------------------------|
| `size()`            | `int`       | Returns the number of elements in the list   |
| `clear()`           | `void`      | Clears all elements (returns nothing)        |



## Array Traversal Using For Loop !
``` java

for(int index = 0;index < namesList.size();index++){
            System.out.println(namesList.get(index));

```
## Enhanced For Loop

```java
for(String names : namesList){
            System.out.println(names);
        }
```

## Loop Using Iterator

Wanna revise Iterator >> 

``` java

Iterator<String> iteratorList = namesList.iterator();  

// namesList.iterator() calls the iterator() method from the Iterable interface
// and returns an Iterator object for the namesList.
// 'iteratorList' is a reference variable pointing to that Iterator object.

while (iteratorList.hasNext()) { 

// Checks if there is a next element in the list

String currentName = iteratorList.next();         
// Retrieves the next element and stores it in 'currentName'

    System.out.println(currentName);
}
```

## For Each using lambda & Method Reference

```java

//For each using lambda

namesList.forEach(x-> System.out.println(x)); // Lambda expression — for each element x, print it

namesList.forEach(System.out::println); // :: > Method reference — shorthand for the above lambda expression
```

##  What is Deque?

> Deque stands for Double Ended Queue.
 
> Double Ended Queue means - we can insert and remove elements from both ends — front and back.

> Deque allows BI-DIRECTIONAL traversal — from front to back and back to front !


```java

// Creating a LinkedList and using add() to add elements

LinkedList<String> namesList = new LinkedList<String>();

            namesList.add("java");
            namesList.add("python");
            namesList.add("selenium");
            namesList.add("java");
            namesList.add("postman");
            namesList.add(0,"cypress");         // Inserts "cypress" at index 0, shifting others to the right
            namesList.add(null);               // o/p - [ cypress, java, python, selenium, java, postman, null]
       
```

## Methods in Deque

```
addFirst(e)       ➤ Adds the element at the front of the list  
addLast(e)        ➤ Adds the element at the end of the list  
get(index)        ➤ Retrieves the element at the specified index (from List)  
getFirst()        ➤ Retrieves the first element in the list  
getLast()         ➤ Retrieves the last element in the list  
offerFirst(e)     ➤ Adds element at the front and returns true if successful  
offerLast(e)      ➤ Adds element at the end and returns true if successful  
pollFirst()       ➤ Removes and returns the first element, or null if list is empty  
pollLast()        ➤ Removes and returns the last element, or null if list is empty  
peekFirst()       ➤ Returns the first element without removing it  
peekLast()        ➤ Returns the last element without removing it  
push(e)           ➤ Adds element at the front (stack-style)  
pop()             ➤ Removes and returns the first element (stack-style)  

```

## Deque Method Examples

```java

 nameList.addFirst("docker")    // return void       
 namesList.addLast("Rest Assured");   // return void
 System.out.println(namesList.get(0));      // from List Interface
 System.out.println(namesList.getFirst()); //From Deque
 System.out.println(namesList.get(namesList.size() - 1)); // From List Interface
 System.out.println(namesList.getLast());  //From Deque
 System.out.println(namesList.offerFirst("python"));// returns boolean
 System.out.println(namesList.offerLast("java")); 
 String pollFirstResult = namesList.pollFirst();
 String pollLastResult =namesList.pollLast(); 
 String peekFirstResult =namesList.peekFirst();
 String peekLastResult = namesList.peekLast();
 namesList.push("javascript");
 namesList.pop();// Removes and returns the first item → which is "javascript"
 ```

 ## Return Types Of Deque Methods


> boolean ➤ offerFirst(), offerLast()

> E (element) ➤ get, getFirst, getLast, pop

> void ➤ addFirst(), addLast(), push()

> E or null ➤ poll() and peek() methods (they safely return null if list is empty)


## Brain Teasers 

### 🔹 Q1: What’s the difference between addFirst() and offerFirst()?

Both add an element to the front (head), but for:

addFirst() - return type is void

offerFirst() returns type is boolean

### 🔹 Q2: What is the return type of pollFirst() and when would it return null?

Return type: E (element type)

It returns null if the deque is empty (safe version of removeFirst())

### 🔹 Q3: If you use push("java") and then pop(), what happens?

push() adds to the front

pop() removes from the front

So we’ll get "java" removed — it behaves like a stack

### 🔹 Q4: Can a LinkedList be used as a Queue, Stack, and Deque?

Yes! LinkedList implements List, Deque, and Queue, so it can function as:

A Queue (FIFO) → using add(), poll()

A Stack (LIFO) → using push(), pop()

A Deque → using addFirst(), removeLast(), etc.

### 🔹 Q5: What happens if you call pop() on an empty LinkedList?

It throws a NoSuchElementException. Unlike poll(), which returns null.

### 🔹 Q6: How can you iterate backward in a Deque?

By using descendingIterator():

```java

Iterator<String> revItr = deque.descendingIterator();
while (revItr.hasNext()) {
    System.out.println(revItr.next());
}
```

### 🔹 Q7: Can you store null in a LinkedList used as a Deque?

Yes! LinkedList allows null elements.

### 🔹 Q8 :Difference Between Polling and Peeking in Deque ?

| Method        | Action                                           | Removes Element? | Return Value                     | When to Use                                       |
| ------------- | ------------------------------------------------ | ---------------- | -------------------------------- | ------------------------------------------------- |
| `pollFirst()` | Retrieves **and removes** the first element      | ✅ Yes            | First element or `null` if empty | When you want to use and remove the element       |
| `peekFirst()` | Retrieves **without removing** the first element | ❌ No             | First element or `null` if empty | When you only want to *check* what's at the front |
