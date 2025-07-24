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