# Stack

## Hierarchy Diagram

```

                 +-------------------------+
                 |  Collection (interface)  |
                 +-------------------------+
                            ↑
                        extends
                 +--------------------------+
                 |     List (interface)     |
                 +--------------------------+
                            ↑
                      implements
                 +-------------------------+
   Synchronized  |   Vector (class)        | Legacy Class (retained only for backward compatibility)
    Thread safe  +-------------------------+ since java 1
                            ↑
                      extends
                 +------------------------+
   Synchronized  |   Stack (class)        | LIFO , 
   Thread safe    +------------------------+
                    child of vector       
```
## Properties of Stack

```
Stack is a Linear Data structure from java.utilpackage.

It is a re-sizable array.

Follows LIFO - Last in Frst Out principle.

Stack is a child of vector. Since vector is synchronized - Stack is also synchronised( thread safe).

JVM uses stack data structure for method excecution.

```
## Stack Working - LIFO: Last-In First-Out
```
Imagine we have 5 books stacked on a table — one over the other.

We place Book 1 on the table.

Then you place Book 2 on top of Book 1.

Then Book 3 on top of Book 2...

Then Book 4, then finally Book 5 on top.

```
```
Top of Stack
   ┌──────────┐  ◄── Book 5 (last inserted)
   |  Book 5  |
   ├──────────┤
   |  Book 4  |
   ├──────────┤
   |  Book 3  |                     In Stack, the top pointer always points to the last added element.
   ├──────────┤
   |  Book 2  |
   ├──────────┤
   |  Book 1  |  ◄── Book 1 (first inserted)
   └──────────┘

Bottom of Stack
```
```
Now if we want to take a book - The only way is to take the top book first.

That means - We take Book 5, then Book 4, then Book 3, and so on...

We CANNOT access Book 1 directly unless we remove all the books above it.

This is how a Stack works in Java - The last item added (Book 5) is the first one to be removed >> This is called LIFO (Last-In First-Out).
```

## Stack Operations

push() > Add elements to stack.

pop() > Removes and returns the top element.

peek() > Returns the top element without removing it.

empty() > cReturns true if the stack has no elements, otherwise returns false.

search() - Search whether element present in stack or not.
        > If present, stack.search(element) returns the 1-based position from the top of the stack.
        > If not present, it returns -1.


```java
Initial Stack:                   After POP:                 After PEEK:

 ┌──────────┐                   ┌──────────┐               ┌──────────┐
 |  Book 3  | ← Top             |  Book 2  | ← Top         |  Book 2  | ← Peeked (still in stack)
 ├──────────┤     stack.pop()   ├──────────┤   Popped      ├──────────┤
 |  Book 2  |  ------------->   |  Book 1  |  ---------->  |  Book 1  |
 ├──────────┤  Removes &        └──────────┘   stack.peek  └──────────┘
 |  Book 1  |  returns Book 3    Top = Book 2              Returns Book 2 (not removed)
 └──────────┘                    
Bottom of stack → Book 1 (First inserted)

```

```
search()
---------
stack.search(book3) > returns 1
stack.search(book4) > returns -1

   ┌──────────┐     ← Top (Position 1)
   |  Book 3  |
   ├──────────┤     ← Position 2
   |  Book 2  |
   ├──────────┤     ← Position 3
   |  Book 1  |
   └──────────┘
```


## Summary

Vector and Stack are legacy classes .

Replacement for vector is Array list (not synchronized - better perfomance in single threaded applications) .

Replacement for stack is Deque (Double Ended Queue - not synchronized and better perfomance in single threaded applications) .











