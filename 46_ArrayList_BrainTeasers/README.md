
## ArrayList - Concept Review: How Much Do You Remember?



 ### Q1. What is the default capacity of an ArrayList in Java? 
 ```
→ 10
```
### Q2. How does an ArrayList grow when the capacity is full? 
``` 
→ It increases by 50% of its current capacity.  
→ Formula: `new capacity = old + (old / 2)`
```

 ### Q3. What is the difference between size() and capacity in an ArrayList?
 ```
→ `size()` = number of elements added  
→ `capacity` = number of elements the internal array can hold
```


### Q4. Where is an ArrayList stored in memory? 
```
→ The reference (e.g., `al`) is stored in the stack  
→ The actual data is stored in the heap
```


### Q5. What happens when an ArrayList is full and a new element is added?  
```
→ A new internal array is created with increased capacity,

 old elements are copied into it, and the reference is updated.
```


### Q6. Is ArrayList thread-safe? 
``` 
→  No. It is not synchronized by default.
```


### Q7. How to make an ArrayList thread-safe?
``` 
→ Use Collections.synchronizedList(list) or CopyOnWriteArrayList<>
```

### Q8. What is the drawback of CopyOnWriteArrayList?  
```
→ It is expensive — creates a new copy on every write operation.
```


### Q9. Can an ArrayList hold primitive types like `int`? 
```
→  No. It can only hold objects like `Integer` (wrapper class).
```

### Q10. What will happen if you try to access an index greater than size? 
```
→ IndexOutOfBoundsException

```

### Q11. How to remove all elements from an ArrayList? 
```
→ Use clear ()
```

### Q12. Can ArrayList store null values?  
```
→ Yes, multiple null`s are allowed
```

### Q13. Does ArrayList maintain insertion order?
```
→  Yes
```

### Q14. How do you sort an ArrayList? 
```
→ Collections.sort(list) for natural order  
→ list.sort(Comparator) for custom order
```

 ### Q15. Difference between remove(int) and remove(Object)?  
 ```
→ remove(index) removes at given index  
→ remove(object) removes first occurrence of that object
```

 ### Q16. What does contains() vs indexOf() do? 
 ```
→ contains(obj) returns true/false  
→ indexOf(obj) returns index or `-1` if not found.
```

 ### Q17. Can we clone an ArrayList?  
 ```
→ Yes, using .clone() — it performs a shallow copy
```

### Q18. How to make a read-only ArrayList? 
```
→ Collections.unmodifiableList(list)
```

 ### Q19. Is ArrayList fail-fast or fail-safe?
 ```
→ Fail-fast — throws ConcurrentModificationException if modified while iterating.
```

 ### Q20. How does ArrayList differ from array in memory management? 
 ```
→ Arrays are fixed-size; ArrayList grows dynamically & manages internal memory.
```

 ### Q21. Can we manually set the capacity of an ArrayList?**  
 ```
→ Yes, using new ArrayList<>(initialCapacity)

```

