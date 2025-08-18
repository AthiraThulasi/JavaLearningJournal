# Method Overloading

```
Method Overloading means creating multiple methods within the same class with the same name, but with different parameters.
```
## How Java Decides Which Method to Call in method overloading?
```
Java looks at:

(1) The number of parameters

(2) The data types of parameters

(3) The order of data types in parameters**

This decision happens at compile time
```
## Calculator - Using Method Overloading

```java

01 public class CalculatorApp {
02     public static void main(String[] args) { / Excecution starts here
03         int a = 10;
04         int b = 20;        // local variables assigned with explicit values // stored in stack
05         int c = 30;
06         double d = 5.5;

07        // Method calls

08         addNumbers(a, b);         // Call 1
09         addNumbers(a, b, c);      // Call 2
10         addNumbers(d, b);         // Call 3
11     }
12       // Overloaded method 1: two ints
13     private static void addNumbers(int x, int y) {
14         System.out.println("Sum (int + int): " + (x + y));
15     }
16 
        // Overloaded method 2: three ints
17     private static void addNumbers(int x, int y, int z) {
18         System.out.println("Sum (int + int + int): " + (x + y + z));
19     }

20       // Overloaded method 3: double and int
21     private static void addNumbers(double x, int y) {
22         System.out.println("Sum (double + int): " + (x + y));
23     }
24 }

```
## How method overloading works Internally?

### Method Call on Line 8: addNumbers(a, b) → Control goes to Line 13 as it matches the method on Line 13.

``` java
main() starts
│
├── Line 8: addNumbers(10, 20)
│     └── Java looks for method: addNumbers(int, int)
│     └── Matches Line 13
│     └── Values pushed to stack:
│         ┌────────────┐
│         │ x = 10     │  ← copied from main()'s a
│         │ y = 20     │  ← copied from main()'s b
│         └────────────┘
│     └── Executes Line 14 → Output: Sum (int + int): 30
│     └── Method excecution finishes - Values popped out of Stack - Control returns to the caller (main method)
│
 At Line 8, local variables `a` and `b` are passed by value into `x` and `y`.

  Local variables from main() are copied into method arguments - Java's pass-by-value behavior.
```


### Method Call on Line 9: addNumbers(a, b, c) → Control goes to Line 17 as it matches the method on Line 17

``` java

main() continues
│
├── Line 9: addNumbers(10, 20, 30)
│     └── Java looks for method: addNumbers(int, int, int)
│     └── Matches Line 17
│     └── Values pushed to stack:
│         ┌────────────────┐
│         │ x = 10         │  ← from a
│         │ y = 20         │  ← from b
│         │ z = 30         │  ← from c
│         └────────────────┘
│     └── Executes Line 18 → Output: Sum (int + int + int): 60
│     └── Method excecution finishes - Values popped out of Stack - Control returns to the caller (main method)
│
 At Line 9, `a`, `b`, and `c` are passed by value into `x`, `y`, and `z`

 Local variables from main() are copied into method arguments - Java's pass-by-value behavior.

```

### Method Call on Line 10: addNumbers(d, b) → Control goes to Line 21 as it matches the method on Line 21


```java

main() continues
│
├── Line 10: addNumbers(5.5, 20)
│     └── Java looks for method: addNumbers(double, int)
│     └── Matches Line 21
│     └── Values pushed to stack:
│         ┌────────────┐
│         │ x = 5.5    │  ← from d
│         │ y = 20     │  ← from b
│         └────────────┘
│     └── Executes Line 22 → Output: Sum (double + int): 25.5
│     └── Method excecution finishes - Values popped out of Stack - Control returns to the caller (main method)
│
 At Line 10, `d` and `b` are passed by value into `x` and `y`.

  Local variables from main() are copied into method arguments - Java's pass-by-value behavior.

```
## Key Points:
```
Method overloading happens inside the same class.

The return type does not affect method overloading.

Java does not care about private, static, void, or modifiers when overloading.

Only the method signature (name + parameter list) matters.
```

## Why Return Type Doesn’t Matter in Overloading?
```
In Java, we do not use return type to differentiate overloaded methods.

If overloading were allowed based on return type alone, it would lead to ambiguity — the compiler would have no way to decide which method to execute during a method call.
```
```java


int show() {
    return 10; // return type is int
}
                                 // both methods have same name.
double show() {
    return 10.5; // return type is double

}
```
```
Even though both methods return different types (int and double), they have the same method name and have no parameters.

When we call show() >> The compiler cannot tell which version of show() we're referring to.

Java will throw an error because it only uses the method name and parameter list to resolve calls — not the return type.

```

