# Method Excecution in java

```
Let's understand the method excecution with the help of a program - Calculator App!
```

##  What Do We Need for a Calculator App?
```
1. Declare variables with the appropriate type (like `int` or `double`) to store the numbers we want to calculate.

2. Define a variable to store the result.

3. We'll define these variables **inside the `main()` method, so they become local variables — stored in **stack memory.

4. Next, we need to create methods like `add()` and `subtract()` to perform our calculations.

5. We’ll pass the LOCAL VARIABLES (holding the numbers) as arguments to these methods so they can use them.
```


##   CalculatorApp

```java

1  public class CalculatorApp {

2      public static void main(String[] args) { // Execution starts here

3          double num1 = 100;    // Initialization → num1 is a local variable stored in stack
4          double num2 = 10;     // Initialization → num2 is also stored in stack

5          double result;        // Declaration only → holds garbage value since not assigned
                                // Local variables in Java are not initialized by default

6          double sum = getCalculatedSum(num1, num2); 
           // Method Call 1: Java says — go and execute this method
           // Java searches the method "getCalculatedSum" inside the method first and then inside class, finds method at line 11 → control goes there

7          System.out.println(sum); // Prints: 110.0

8          double diff = getCalculatedDiff(num1, num2); 
           // Method Call 2: control goes to line 15

9          System.out.println(diff); // Prints: 90.0
10     }

11     public static double getCalculatedSum(double num1, double num2) { 
         // Control from line 6 reaches here → this method is pushed to the stack

12         double result = num1 + num2; // result = 100 + 10 = 110

13         return result; 
         // The result (110) is returned to result is returned back to the caller - 
         // line 6 and assigned to variable 'sum'
         // Garbage value from line 5 is replaced with 110
14     } // Method ends → popped from stack → control returns to line 7

15     public static double getCalculatedDiff(double num1, double num2) {
         // Control from line 8 reaches here → this method is now pushed to stack

16         double result = num1 - num2; // result = 100 - 10 = 90

17         return result; 
         // Returns 90 to line 8 and assigned to variable 'diff'
18     } // Method ends → popped from stack → control returns to line 9

19 }


```

## How Method works Internally ?
```
Main Method Execution Starts at (Line 2)

At line 2, the main() method is pushed to the stack.

num1 = 100 and num2 = 10 are local variables stored in stack memory

result is declared but not initialized, so it holds a garbage value
```
```
+--------------------------+
| main()                  |  ← top       top in stack means - This is the method currently executing
| num1 = 100              |
| num2 = 10               |
| result = ??? (garbage)  |
+--------------------------+

```

## Why is the main() method able to directly call getCalculatedSum() or getCalculatedDiff()?
```
The main() method is always declared as public static.

In Java, a static method can directly call another static method in the same class without using an object reference.

```
## Calling getCalculatedSum(num1, num2) - Line 6
```
At line 6, java calls the method getCalculatedSum(num1, num2) - Method call

Java search for the method inside the method first and then inside the class

Control goes to Line 11 and the getCalculatedSum () in line 11 is pushed to top of the stack 

Values of num1 and num2 from the main are passed into this method.

Result is calculated and returned to the caller method - Line 7

Once the method completes, it is popped off (removed) from the stack and control goes to Line 8.
```
```
+----------------------------------+
| getCalculatedSum()              |  ← top        top in stack means - This is the method currently executing
| num1 = 100                      |
| num2 = 10                       |
| result = 110                    |
+----------------------------------+
| main()                          |
| num1 = 100                      |
| num2 = 10                       |
| result = ??? (garbage)          |
+----------------------------------+
```

## Calling getCalculatedDiff(num1, num2) - Line 8
```
At line 15, java calls the method getCalculatedDiff() - Method call

Java search for the method inside the method first and then inside the class

Control goes to Line 15 and the getCalculatedDiff () is pushed to top of the stack 

Values of num1 and num2 from the main are passed into this method.

Result is calculated and returned to the caller method - Line 9

Once the method completes, it is popped off (removed) from the stack and control goes to Line 8.
```


```
+----------------------------------+
| getCalculatedDiff()             |  ← top**     top in stack means - This is the method currently executing
| num1 = 100                      |
| num2 = 10                       |
| result = 90                     |
+----------------------------------+
| main()                          |
| num1 = 100                      |
| num2 = 10                       |
| result = ??? (garbage)          |
| sum = 110                       |
+----------------------------------+
```


## Final Stack (Just Before Program Ends)

```
+------------------------------+
| main()                      |  ← top
| num1 = 100                  |
| num2 = 10                   |
| result = ??? (garbage)      |In final stack, sum and diff store actual results,but "result" in main() still holds garbage bcs nothing was assigned to it.
| sum = 110                   |
| diff = 90                   |
+------------------------------+
```
```
All lines in main() executed

No more methods to call
```

 ### At this point:

```
- All local variables (`num1`, `num2`, `sum`, `diff`, `result`) are cleared from memory.
- The `main()` method is popped off the stack.
- Stack becomes empty.
- The Java program ends gracefully.
```









