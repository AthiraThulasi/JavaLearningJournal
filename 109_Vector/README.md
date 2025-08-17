# Vector


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


```
Vector was introduced in Java 1.0 to overcome limitations of traditional arrays.

> It is part of java.util package.

> It is a re-sizable array that can store elements dynamically.

> Every method in Vector is synchronized, making it thread-safe.

> However, this comes at the cost of slower performance.

```
```java

Syntax:

Vector<Integer> vector = new Vector<Integer>();
```
## Key Characteristics

> Internally works like an array (with indexed elements).

> Resizes automatically: When full, the capacity doubles (2x).

> All methods are thread-safe → Safe for multi-threaded environments.

> Due to synchronization overhead, it is slow, even in single-threaded use cases.

> Became legacy after Java 1.2, retained only for backward compatibility.

> ArrayList was introduced as a DIRECT REPLACEMENT FOR VECTOR in Java 1.2, as part of the Java Collections Framework.

## Vector vs ArrayList

| Feature                | Vector                               | ArrayList                                                                                   |
| ---------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------- |
| Introduced In          | Java 1.0                             | Java 1.2 (as part of Collection Framework)                                                  |
| Package                | java.util                            | java.util                                                                                   |
| Thread Safety          | Synchronized (Thread-safe)           |  Not synchronized (Not thread-safe)                                                         |
| Performance            | Slower due to synchronization        | Faster in single-threaded environments                                                      |
| Capacity Growth        | Grows by 100% (doubles capacity)     | Grows by 50%                                                                                |
| Default Use Case       | Multi-threaded environments          | Single-threaded environments                                                                |
| Flexibility in Threads | Always synchronized                  |  Can be made synchronized using Collections.synchronizedList() or CopyOnWriteArrayList      |
| Status                 | Legacy class (use discouraged)       | Preferred in Java collections                                                       



## Methods In Vector!


``` java

import java.util.*;

public class Vector101 {
    public static void main(String[] args) {

        // Creating a Vector of Integers
        Vector<Integer> vector = new Vector<>();

        // Adding elements using legacy method addElement()
        vector.addElement(10);  // Legacy method
        vector.addElement(20);
        vector.addElement(40);
        vector.addElement(50);
        vector.addElement(650);

        System.out.println(vector);  // Prints all elements

        // Accessing elements - Legacy methods
        System.out.println(vector.firstElement());      // First element (Legacy)
        System.out.println(vector.lastElement());       // Last element (Legacy)
        System.out.println(vector.elementAt(2));        // Element at index 2 (Legacy)
        System.out.println(vector.get(2));              // Collection interface method

        // -------------------------------
        // Removing elements from Vector
        // -------------------------------
         vector.remove(3);                        // Remove by index (Collection)
         vector.removeElementAt(0);               // Legacy method
         vector.remove(new Integer(20));          // Remove by value (Collection)
         vector.removeElement(new Integer(650));  // Legacy remove

        // --------------------------------
        // Iteration using Iterator
        // Iteration using Iterator (Way to retrieve elements from any Collection)
        // --------------------------------
        System.out.println("---- Iterator ----");
        Iterator<Integer> vIterator = vector.iterator();
        while (vIterator.hasNext()) {
            System.out.println(vIterator.next());  // / Retrieves each element from the Vector
        }

        // --------------------------------
        // Iteration using Enumeration (Legacy) - 
        // Enumeration is a legacy interface used to traverse (iterate) through the elements of legacy collections like Vector and Hashtable.
        // --------------------------------
        System.out.println("---- Enumeration ----");
        Enumeration<Integer> vEnum = vector.elements();
        while (vEnum.hasMoreElements()) {
            System.out.println(vEnum.nextElement());  // Iterates using Enumeration
        }

        
        //size() gives the total number of elements present in vector
        System.out.println(vector.size());           // Total elements

        // Ensures capacity is 35 (increases if needed)
        vector.ensureCapacity(35);  // when we know the capacity of vector                 

        // Convert vector to Array
        Integer[] data = vector.toArray(new Integer[0]);     // Collection

        Integer[] myData = new Integer[vector.size()];
        
        vector.copyInto(myData);                             // Legacy copy method

        System.out.println(Arrays.toString(myData));         // Prints copied array
    }
}
```
