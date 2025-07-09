# 📘 Code Execution
Step-by-Step Breakdown of Java Code Execution

Line 1: package Example1;
Line 2: public class Example1 {
Line 3:     public static void main(String[] args) {
Line 4:         int a = 20;
Line 5:         long g = 2000;
Line 6:         char gender = 'm';
Line 7:         float percentage = 33.23f;
Line 8:         boolean isPercentage = false;
Line 9:         System.out.println(a);
Line 10:    }
Line 11: }


Line-by-Line Explanation:
Line 1: package Example1;

Declares that this class belongs to the Example1 package, which is used to organize Java files into namespaces.
 
 Line 2: public class Example1 {

Defines a Java class named Example1. The keyword class tells the compiler this is a class definition.
 
Line 3: public static void main(String[] args) {

This is the starting point of the program.
Java execution begins with the main() method.
•	public: So that JVM can access it from anywhere
•	static: So JVM can run the method without creating an object
•	void: It doesn’t return any value
•	Java only executes methods, not entire classes directly.

Execution happens inside Stack Memory, which is a LIFO (Last In First Out) data structure — the most efficient memory area in the Java for method execution.
 
Line 4: int a = 20; // Initialization
“a” is a variable declared inside the method – so it is called Local Variable
20 is stored inside a
Since it's declared inside a method, it's stored in the stack memory.
 
Line 5: long g = 2000;

Java checks the right-hand side first .
•	2000 is an integer literal, and by default, Java treats it as int.
•	long g = 2000; → Java sees that g is of type long.
•	Since int can safely fit into long, Java automatically promotes (aka widens) 2000 to 2000L behind the scenes.
•	This process is called widening primitive conversion and it happens automatically when moving from smaller to larger data types.
•	Like a, g is also a local variable and goes into the stack.
 
Line 6: char gender = 'm';

A character value 'm' is assigned to variable gender. Stored in stack memory.
 

 Line 7: float percentage = 33.23f;

Stores a floating-point number in variable percentage.
Note: The f is necessary to explicitly mark it as a float.
 

How the Stack Memory Looks Internally ?

```plaintext
Stack Memory
+---------------------------+
|                           |
|                           |
|       main() Frame        |   Top  <----------------------+
|  +---------------------+  |                         |
|  | isPercentage: false |  |                         |
|  | percentage: 33.23f  |  |                         |
|  | gender: 'm'         |  |                         |
|  | g: 2000L            |  |                         |
|  | a: 20               |  |                         |
|  +---------------------+  |                         |
|                           |                         |
|                           |                         |
+---------------------------+ 


```



The "top of the stack" refers to the memory location where the most recently added data is stored in a stack data structure.



Line 8: boolean isPercentage = false;

A boolean variable that stores either true or false.
Stored in the stack like the others.
 
Line 9: System.out.println(a);
Prints the value of variable a to the console.
•	System is a predefined class in Java
•	out is a reference to the output stream (usually the screen)
•	println() is a method that prints the value passed to it
 
Line 10: }

This marks the end of the main() method.
Once it ends, all local variables that were pushed onto the stack are now popped out — the stack is cleared for that method call.
 
Line 11: }

Ends the Example1 class definition.
 
Local Variables and Default Values
•	In Java, local variables (declared inside methods) are not automatically initialized.
•	If we write:
int a; // declared but not initialized
System.out.println(a); // ❌ Error: variable a might have not been initialized
We’ll get a compile-time error.
•	Why? Because the compiler can't guarantee what value a hold — it could be garbage or random — and Java wants to avoid unsafe behavior.

 Key Concepts:
•	Local Variables: Variables declared inside a method — like a, g, gender, etc. — are local and live temporarily in the stack during method execution.
•	Java does not automatically initialize local variables with default values — if we declare them without assigning, they hold garbage values.
•	Once main() completes, all the values are removed from stack memory.


















