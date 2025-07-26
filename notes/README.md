#Notes

## Quick recap on keywords extends and implements

### > An interface  extends another interface
```
An interface extends another interface means interface inherits all the abstract and default methods from another interface .

Example: List extends Collection

> Both List and Collection are interfaces.                              ┌──────────────────────────┐
                                                                        │  Collection (interface)  │
> Collection is the parent, and List is the child.                      └──────────────────────────┘
                                                                                         ▲
 
> So, List inherits all methods from the Collection interface.                           │  extends
                   │
                                                                             ┌────────────────────┐
>This includes:                                                              │  List (interface)  │

   > All abstract methods                                                    └────────────────────┘

   > All default methods (since Java 8)
  
   > List does not inherit static methods in collection                                                                                                                                                   
                                                                    
```
### > A Class implements an interface
```
Class implements an interface means a class agrees to provide concrete definitions for all the methods declared in the interface.

Example: ArrayList implements List.     

        ┌────────────────────┐
        │   List (interface) │
        └────────────────────┘
                  ▲
                  │  implements
                  │
        ┌────────────────────┐
        │  ArrayList (class) │
        └────────────────────┘

```
### A Class extends another class
```
Class extends another class  means a class can **inherit** from another class.

Example: Stack extends Vector
```

(Note: Map is a separate top-level interface, not part of the Collection hierarchy)
```


Yes, absolutely\! It makes the diagram even clearer to specify "implements".

Here's the revised diagram with "implements" added to the relevant arrows:

```
                  Queue (interface)
                        ▲
                        |  extends
                        |
                       Deque (interface)
                        ▲       ▲
                        |       |
                        |       | implements
                       List (interface)
                        ▲       |
                        |       |
                        |       | implements
                      LinkedList (class)
```



✅ We use Iterator to traverse through collections in Java.
Here’s the breakdown:

Iterator is an interface in java.util.

It is used to loop through elements one by one from collections like List, Set, etc.

It works with any class that implements the Iterable interface (like ArrayList, HashSet, etc.).

Common Methods of Iterator:
Method	Description
hasNext()	Checks if there's another element
next()	Returns the next element

remove()	Removes the current element (optional)

Summary:
Concept	Package	Role
Iterable	java.lang	The base interface implemented by all collections
iterator()	method in Iterable	Returns an Iterator
Iterator	java.util	Interface used to traverse elements one by one


TIP
Breakdown:
✅ Iterator is an interface in java.util.

✅ iterator() is a method defined in the Iterable interface.

✅ When you call iterator() on any collection (like ArrayList, HashSet, etc.), it returns an object that implements the Iterator interface.

Iterator is not part of the main Collection interface hierarchy (like Iterable → Collection → List/Set/Queue).

Instead, Iterator is a helper interface in the java.util package used for traversal.

             java.lang.Iterable (interface)
                      ↑
         All collection interfaces like:
     Collection, List, Set, Queue, Deque, etc.
                      |
              +----------------+
              |  iterator()    |
              |  (abstract)    |
              +----------------+
                      ↓
         java.util.Iterator (interface)


The Iterable interface has only one abstract method: iterator().

Any class that implements Iterable (like ArrayList, LinkedList, HashSet, etc.) must provide this iterator() method.

The iterator() method returns an object of a class that implements the Iterator interface.

That returned object is what allows you to loop using hasNext() and next()
