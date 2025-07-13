# Linked List

## 1. What is a LinkedList?

### A LinkedList is a linear datstructure where each element (called a node) contains (1) a value and  (2) a reference (pointer) to the next node.

### The last node has no pointer — it ends with null.

```java

	 (1) Data – the actual value 
     (2) Reference – a pointer to the next node
```

## Node:

``` java 

Node → [ Data | Reference to Next Node ]

Nodes are connected one after another using the references — like a chain scattered across the memory, not continuous like in Array/ArrayList.

```

## What Does a LinkedList Look Like Internally?
```

       Node →
       ┌────┬────┐            
       │ 10 │200 │ ─────────┐
       └────┴────┘          │ pointer
         ↑     ↑            ▼
       data  ref →     ┌────┬────┐
                       │ 20 │444 │ ────────────────┐
                       └────┴────┘                 │
                         ↑     ↑                   ▼ pointer
                       data  ref →           ┌────┬────┐
                                             │ 33 │null│ Last Node - No next node after this! So reference is NULL!
                                             └────┴────┘
                                              ↑     ↑
                                            data  null (end)

 Each node is in a separate place in memory — only connected by pointers.

 ```

## Why Is the Last Node’s Reference null?

**In a LinkedList, each node has a reference (pointer) to the next node.**

**But for the last node >>> There is no next node after this.**

**So the reference is set to null — meaning >> This pointer is not pointing to any object in memory.**



## Why Use LinkedList When We Already Have Array and ArrayList?

### Let’s understand it like a story -

```java
We started with Arrays — but they come up with a limitation: Arrays have a fixed size. Once created, we can’t resize them. ❌

```
```java

To overcome that, Java gave us: ArrayList — A resizable array that can grow and shrink automatically.

But ArrayList has another drawback: It stores data in contiguous memory locations.

So when we do frequent insertions or deletions (especially in the middle), it becomes slow due to shifting of elements.❌

```

 ### So, What’s the Solution >> LinkedList.

```java

 A data structure where nodes are not stored together in memory. Each node just knows where the next node is. ✅

Because of this:

(1) Insertion and deletion are faster (no shifting!)

(2) It works well even if memory is fragmented (no need for big continuous blocks)

(3) Time complexity for insertion/deletion is O(1) when node reference is available.

(4) Time complexity for insertion/deletion is O(N), when there is no direct reference means whenwe need to search for the node (e.g., by index, by value, or by traversing from the head)

```
 
### Types Of LinkedLists

```
                        LinkedList
                             │
     ┌──────────────────────┼──────────────────────┐
     │                      │                      │
Singly LinkedList   Doubly LinkedList   Circular LinkedList

```
## Singly LinkedList

**The reference in each node allows traversal in only one direction — from the first node (head) to the last node - forward movement.**

**We can’t go backward because nodes don’t store a reference to the previous node.**
```

         ┌─────────────┐
         │ 10  |  666  │
         └─────────────┘
          ↑      ↑
        data   reference (next node)

                  │
                  ▼

         ┌──────────────┐
         │ 50  |  null  │
         └──────────────┘
          ↑       ↑
        data   reference (null → end of list)
```


## Doubly Linked List

**In a Doubly Linked List, each node contains references to both the previous and the next node.**

```
┌────────────────────┬────────┬───────────────────┐
│Address of Prev Node│ Data   │ Address of Next Node 
└────────────────────┴────────┴───────────────────┘ 

```
**This allows traversal in both directions:**

**(1) Forward (head → tail)**

**(2) Backward (tail → head)**



 ### NOTE :**Java's LinkedList class uses Doubly Linked List structure internally.**

```
 
┌──────┬────┬──────┐        
│ null │ 10 │ 666  │ ─────                                                  
└──────┴────┴──────┘       │
  Prev   D    next         │
         ↑                 ▼
      777 (address)   ┌──────┬────┬──────┐
                      │ 777  │ 11 │ null │
                      └──────┴────┴──────┘
                        Prev   D    next
                                 ↑
                             last node


```

### Node 1

**777 is the memory address of the first node.**

**Address of previous Node is null because no previous node exists(this is the head)**

**666 is the pointer to the next node.**

### Node 2

**777 is the address of the previous node (Node 1). It allows backward movement.**

**11 is the actual data stored.**

**null in the next field  as there is no node after this → so this is the last node (tail).**

## Circular LinkedList

**In a circular linked list, each node stores: Data  +  reference (pointer) to the next node.**

**The last node does not point to null, Instead, it points back to the first node.**

**This creates a continuous loop where, we can keep traversing from one node to the next and eventually we will come back to the starting node.**

**That’s why it's called a “circular” linked list — the nodes form a closed circle.**

```
                  +--------------------------------+
                  |                                |
                  V                                |
       777 --> +-------+-----------+      666 --> +-------+-----------+
               | Data  | Reference | --->           | Data  | Reference |
               +-------+-----------+                +-------+-----------+
                 |  9    |    666    |                  |   10    |    555    |
                 +-------+-----------+                +-------+-----------+
                     ^                                      |
                     |                                      V
                     |                          555 --> +-------+-----------+
                     |                                  | Data  | Reference |
                     |                                  +-------+-----------+
                     +--------------------------------- |   11    |    777    |
                                                        +-------+-----------+
```
