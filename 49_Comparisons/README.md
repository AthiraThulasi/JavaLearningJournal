# Comparisons

## (1) Local Variable Vs Instance Variable

```

| Feature                   | Local Variable                                         | Instance Variable                                                    |
|-------------------------- |--------------------------------------------------------|----------------------------------------------------------------------|
| Declaration               | Declared inside a method or block                      | Declared inside a class                                              |
| Scope                     | Only accessible within the method/block where declared | Accessible by all methods of the class (via object)                  |
| Memory Allocation.        | Stored in stack memory                                 | Stored in heap memory                                                |
| Default Value             | No default value, must be initialized before use       | Default values (e.g., null, 0, false)                                |
| Lifetime.                 | Exists only during method execution                    | Exists as long as the object exists                                  |
| Access Modifier.          | No access modifier                                     | Can have access modifiers (public, private, protected)               |
| Storage Location          | Stored in the stack                                    | Stored in the heap (object)                                          |
| Connection to Heap.       | No connection to heap                                  | Reference variable in the stack points to the object in the heap     |
-------------------------------------------------------------------------------------------------------------------------------------------------------------
```

```java

    // Instance variables declared inside class - reference variable (name,age,address) is stored in stack and points to object (john,25,)in stack
    public class Person {

    // Instance variables with different access modifiers
    private String name = "John";  // Private instance variable
    public int age = 25;           // Public instance variable
    protected String address = "123 Main St";  // Protected instance variable

    // Method to display local variable - stored in stack
    public void displayInfo() {
        // Local variable (no access modifier)// 
        int x = 10; //  local variable

        // Main method to run the program
    public static void main(String[] args) {
        // Creating an object of Person class
        Person person = new Person(); 
      
    }
}
```
```
+-------------------------------------------+        +-------------------------------------------+
|       Stack   -  Local Variable           |        |    Heap - Instance Variables              |
+-------------------------------------------+        +-------------------------------------------+
| Reference variable: person -> 0x12345     |  --->  | Object: Person                            |
| Local variable: x = 10                    |        |  - name = "John"                          |
+-------------------------------------------+        |  - age = 25                               |
                                                     |  - address = "123 Main St"                |
                                                     +-------------------------------------------+
                                                     |  (The reference 'person' in the stack     |
                                                     |   points to the memory address of the     |
                                                     |   object in the heap)                     |
                                                     +-------------------------------------------+
```

## Key points
```
 Local variables must be explicitly initialized before they can be accessed. If they are not initialized, trying to access them will lead to a compiler error.

 Instance variables do not require initialization explicitly, they will be initialized to default values when the object is created. 
```
```java

int x;  // Declaring local variable without initializing

System.out.println(x);  // Error: variable x might not have been initialized

```


## Constructors Vs Setters


| Constructor                                                                          | Setter                                                                         
| -------------------------------------------------------------------------------------| ------------------------------------------------------------------------------ |
| Special method with the SAME NAME AS CLASS                                           | NORMAL METHOD follows camelCase naming.                                        |
| Has NO RETURN TYPE                                                                   | Has a return type (commonly `void`).                                           |
| Called ONCE during object creation.                                                  | Can be called **multiple times** after object creation.                        |
| Used to INITIALIZE instance variables.                                               | Used to UPDATE/CHANGE instance variables.                                      |
| If only constructors are used → object is **Immutable** (values fixed after creation).| Using setters makes object **Mutable** (values can be updated).                |
| Can be **overloaded** (multiple constructors with different parameters).             | Setters are **not overloaded**, but multiple setters exist (one per variable). |
| Values are assigned only **once** when the object is created.                        | Values can be updated **any number of times**.                                 |

------------------------------------------------------------------------------------------------------------------------------------------------------------------------
