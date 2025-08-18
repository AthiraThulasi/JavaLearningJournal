# Linked List

##  What is a LinkedList?
---

**A LinkedList is a linear data structure where elements are stored in the form of nodes**.  

**These nodes are connected like a chain — each node holds a reference (pointer) to the next node.**
**Unlike ArrayList, the nodes in a LinkedList are stored in scattered memory locations, not in a continuous block.**

**The **last node** doesn’t point to anything — its pointer is set to `null`, marking the end of the list.**

**We use LinkedList when we need frequent insertions and deletions, especially in the middle of the list, because shifting is not required like in arrays.**

```
Each node contains:
1. A value (the data)
2. A reference (or pointer) to the next node in the list.
```

## What is a Node?
---

``` java 

Node → [ Data | Reference to Next Node ]

Nodes are connected one after another using the references — like a chain scattered across the memory, not continuous like in Array/ArrayList.

```

## What Does a LinkedList Look Like Internally?
---
```

       Node →
       ┌────┬────┐            
       │ 10 │200 │ ─────────┐
       └────┴────┘          │ pointer
         ↑     ↑            ▼
       data  ref       ┌────┬────┐
                       │ 20 │444 │ ────────────────┐
                       └────┴────┘                 │
                         ↑     ↑                   ▼ pointer
                       data  ref             ┌────┬────┐
                                             │ 33 │null│ Last Node - No next node after this! So reference is NULL!
                                             └────┴────┘
                                              ↑     ↑
                                            data  null (end)

 Each node is in a separate place in memory — only connected by pointers.

 ```

## Why Is the Last Node’s Reference null?
---

**In a LinkedList, each node has a reference (pointer) to the next node.**

**But for the last node >>> There is no next node after this.**

**So the reference is set to null — meaning >> This pointer is not pointing to any object in memory.**



## Why Use LinkedList When We Already Have Array and ArrayList?
---

### Let’s understand it like a story:

```java
We started with Arrays — but they come up with a limitation: Arrays have a fixed size. Once created, we can’t resize them. 

To overcome that, Java gave us: ArrayList — A resizable array that can grow and shrink automatically.

But ArrayList has another drawback: It stores data in contiguous memory locations.

So when we do frequent insertions or deletions (especially in the middle), it becomes slow due to shifting of elements.

```

 ### So, What’s the Solution ?  LinkedList !
 ---


```java

 LinkedList is a data structure where nodes are not stored together in memory. Each node just knows where the next node is. 

 ```

 ### Why LinkedList Works Better for Certain Scenarios ?
 ---

 ```

1. Insertion and deletion are faster (no shifting!)

2. It works well even if memory is fragmented (no need for big continuous blocks)

3. Nodes are connected using references, not physical positions

4. Supports **bi-directional traversal** if it's a Doubly Linked List
```

### What is Time Complexity ? 
---

```
Time Complexity is a way to measure how efficient a data structure is, based on how the performance changes when you give it more data to handle.

```

### What is the Time Complexity of linkedList and Why?
---

```
Time Complexity of LinkedList is O(1) - Constant Time, when we have a direct reference to the node or its predecessor.

 Operation takes roughly the same amount of time no matter how big the list is.ie, Even if the list gets bigger, Time complexity remains same as O(1), with no extra time

Time Complexity of LinkedList is O(N) - Linear Time, when accessing an element by index or Searching for an element by value .

```
### Why O(1)? 
---

>> **In a LinkedList** 
---

```
- nodes are NOT stored in continuous memory.
- To insert or delete, we just update the `next` (and maybe `prev`) pointers to skip or connect around the node.
- This pointer adjustment takes **constant time — O(1). 


Before deletion:
[10] → [20] → [30]

After deleting 20:
[10] ─────────→ [30]

No shifting. No resizing. Just a simple reference change.

```
---
>> **In an ArrayList**
---
```
- If we want to insert or delete an element from the middle:
- we have to shift all the other elements to fill the gap or make space — which takes O(n) time.
- This makes the operation **O(n)** in the worst case.

```
> **That’s why LinkedList is preferred when frequent updates are needed in the middle of the structure.**


### Types Of LinkedLists
---
```


                        LinkedList
                             │
     ┌──────────────────────┼──────────────────────┐
     │                      │                      │
Singly LinkedList   Doubly LinkedList   Circular LinkedList

```
## Singly LinkedList
---

**The reference in each node allows traversal in only one direction (Single direction)  — from the first node (head) to the last node - forward movement.**

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
---

**In a Doubly Linked List, each node contains references to both the previous and the next node.**

```
┌────────────────────┬────────┬───────────────────┐
│Address of Prev Node│ Data   │ Address of Next Node 
└────────────────────┴────────┴───────────────────┘ 

```
**This allows traversal in both directions (bi-directional traversing):**

**(1) Forward (head → tail)**

**(2) Backward (tail → head)**

Bi-directional traversing makes traversal more efficient compared to a singly linked list.

 ### NOTE :**Java's LinkedList class uses Doubly Linked List structure internally.**

```
 
┌──────┬────┬──────┐        
│ null │ 10 │ 666  │ ─────                                                  
└──────┴────┴──────┘       │
  Prev   D    next         │
  |      ↑                 ▼
  |   777 (address)   ┌──────┬────┬──────┐
  |                   │ 777  │ 11 │ null │ last node
  |                    └──────┴────┴──────┘
  |                     Prev   D    next
  |                              ↑
  |                         666 (address)  

This is the head → No previous node, so Prev = null

```

### Node 1
---

**777 is the memory address of the first node.**

**Address of previous Node is null because no previous node exists(this is the head)**

**666 is the pointer to the next node.**

### Node 2
---

**777 is the address of the previous node (Node 1). It allows backward movement.**

**11 is the actual data stored.**

**null in the next field  as there is no node after this → so this is the last node (tail).**

## Circular LinkedList
---

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


##  ArrayList vs LinkedList – Performance Comparison
```

| Operation      | ArrayList                                                | LinkedList                                      
|----------------|------------------------------------------------       |----------------------------------------------------------------|
| add()          | ✅ **Faster** – added at the end in continuous memory | ❌ **Slower** – Java must find and link scattered memory nodes |
| get()          | ✅ **Faster** – direct index access                   | ❌ **Slower** – must traverse from head                        |
| update()       | ✅ **Faster** – update by index                       | ❌ **Very slow** – must locate node before updating            |
| delete()       | ❌ **Slower** – shifting needed after removal         | ✅ **Super fast** – just unlink 1 or 2 nodes                   |

```
###  Key Notes
---

- **ArrayList** provides fast access and update, but is slower for deletions due to shifting.

- **LinkedList** excels in insertion and deletion, especially when done at the head or tail.


### Frequently Asked in Interviews
---

 **How to reverse a LinkedList ?**

 **Why do we use linkedlist for manipulation and not ArrayList?**
 ```

When it comes to frequent **insertions and deletions**, especially in the **middle or beginning**, `LinkedList` outperforms `ArrayList` due to its internal structure.

## ✅ Key Reason:

- **LinkedList** uses **nodes with pointers** — allowing quick changes without shifting elements.
- **ArrayList** uses a **contiguous array** — making insertion/deletion expensive because elements need to be moved.

---

## 📊 Performance Comparison

| Operation                                                  | LinkedList                                                              | ArrayList                                        |
| ---------------------------------------------------------- | ----------------------------------------------------------------------- | ------------------------------------------------ |
| **Insertion/Deletion** (especially in the middle or start) | ✅ **Efficient** → Just re-link pointers → `O(1)` (if position is known) | ❌ **Slow** → Needs shifting of elements → `O(n)` |
| **Memory Layout**                                          | Elements are not stored in contiguous memory blocks                     | Elements are stored in contiguous memory blocks  |
| **Overhead**                                               | Slightly more memory (extra pointers)                                   | Less memory overhead                             |

---

## 💡 Example

```java
// Insert at the beginning
linkedList.addFirst("new"); // ✅ Very fast — no shifting needed
arrayList.add(0, "new");    // ❌ Slow — shifts all elements right

```
                     |

