# Exception Handling


## What is Exception?
```
Exception refers to an unwanted interruption that affects the normal flow of a program.

```

## What is Exception Handling?
```
Exception Handling is finding ways to handle the unwanted interruptions.

We can handle this unwanted interruption caused by the risky code by giving proper error messages and make the code robust and user friendly!

```
## Why Exception Handling?  
```
We write code assuming things will work perfectly. But what if something goes wrong?

Situations like:

   (1) Reading a file – the file path may be wrong, or the file may not exist

   (2) Connecting to a database – the DB might be down

   (3) Accessing a null object – causes NullPointerException

   (4) Accessing a missing element – causes ElementNotFound-type errors

These interruptions should be handled properly, else the program will crash.
```

##  Benefits of Exception Handling

```
  Helps display proper error messages

  Improves the user experience

  Easier debugging — trace the exact line where the error occurred

  Makes code robust and reliable

```
##  Hierarchy of Exception Classes
```
                     Object  (Parent class)          Object is the parent of all classes in java (belongs to java.lang package)
                       │ extends
                  ┌────┴────┐
                  │Throwable│   ←     Throwable is the general class for all exceptions (belongs to java.lang)
    extends       └───┬────-┘ extends
             ┌────────┴────────┐
             │                 │
  (class)Exception            Error (class)

 ```  
 ```     
Throwable is the parent class of both Exception and Error

Belongs to the java.lang package

Throwable has two child classes - Exception & Error

Exception → can be handled using try-catch

Error → cannot be handled (e.g., OutOfMemoryError)
```
## Types of Exceptions

```
(1) Checked Exceptions  and 

(2) Unchecked Exceptions

```
## Checked Exceptions

Checked by the compiler at compile time	

## Why Are Some Exceptions "Checked"?
```
Exceptions like FileNotFoundException and SQLException are checked by the compiler because:

There is a high chance that things can go wrong in these cases

These problems are often out of our control — and Java wants us to handle them properly
```

markdown
###  Real-World Scenarios of Checked Exceptions

<table>
  <tr>
    <th>Exception</th>
    <th> Common Scenarios</th>
  </tr>
  <tr>
    <td><code>FileNotFoundException</code></td>
    <td>
      <ul>
        <li>File might be missing</li>
        <li>File path could be wrong</li>
        <li>File may be corrupted</li>
        <li>No permission to access the file</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><code>SQLException</code></td>
    <td>
      <ul>
        <li>Database might be down</li>
        <li>Connection might fail</li>
        <li>Query could be invalid</li>
      </ul>
    </td>
  </tr>
</table>

```
Since these are very common real-world risks that occur at runtime, Java wants us to prepare for them in advance — during compilation.

If we don’t handle them - Java throws a compile-time error - These are known as Checked Exceptions.

```
##  Unchecked Exceptions
```
Unchecked exceptions are RUNTIME Exceptions that are not checked by the compiler during compilation.


- The program compiles successfully, but may fail at runtime.

- Java does not force you to handle them using try-catch or throws.

- These exceptions occur due to programming mistakes or memory-related issues, such as:

  - Accessing null references → NullPointerException

  - Dividing by zero → ArithmeticException

  - Accessing invalid array indexes → ArrayIndexOutOfBoundsException


Explanation:

NullPointerException → when we try to use an object that is null

ArrayIndexOutOfBoundsException → when we access an array index that doesn't exist

ArithmeticException → when we perform illegal math (like 10 / 0)

```
## Who is the Parent of Exception?
```
All exceptions inherit from Throwable, which in turn extends Object, the parent of all classes in Java.

```

##  How to Handle Exceptions in Java ?

###  The best way to handle exceptions in java is Using try-catch block




```java

try {        // We use `try-catch` to handle exceptions and stop the program from crashing unexpectedly.
    
    // Risky code that might catch an exception

} catch (ExceptionType refVar) {

    System.out.print(e.getMessage());
    e.print StackTrace();
    
    // Handling code
}
```

##  Different Types of Exceptions

### (1) Arithematic Exception
```
ArithmeticException happens when you perform an illegal math operation in Java — most commonly dividing a number by zero.
```
```java

public class Main {                   // Main class of the program
    public static void main(String[] args) {  // Entry point of the program
        
        int a = 10, b = 0;             // Two integer variables, 'b' is 0 (this will cause divide-by-zero issue)
        int result = 0;                // Variable to store the division result

        try {                          // 'try' block → place risky code here
            result = a / b;            // This will cause ArithmeticException because dividing by 0 is not allowed
        } catch (ArithmeticException e) {  // 'catch' block → runs if an ArithmeticException happens
            System.out.println("can't divide a number by zero!"); // Custom friendly message to user
            System.out.println(e.getMessage());  // Shows Java's built-in short message (e.g., "/ by zero")
            e.printStackTrace();                 // Prints the full stack trace (type, message, line number)
        }

        // This will still run because we handled the exception instead of letting the program crash
        System.out.println("Result: " + result); // Prints '0' because division was not successful
        System.out.println("Hello");             // Just to show program continues
    }
}

```
### (2) ArrayIndexOutOfBoundsException
```
ArrayIndexOutOfBoundsException happens when we try to access an array index that does not exist.

Java arrays have fixed sizes, so valid indexes are from 0 to length - 1.
```
```java
public class Main {

    public static void main(String[] args) {

        // Creating an array of size 3 (valid indexes: 0, 1, 2)
        int[] a = new int[3];

        // Storing values in each index
        a[0] = 10;
        a[1] = 20;
        a[2] = 30;

        try {
            // Trying to store a value at index 3 (invalid, last valid index is 2)
        a[3] = 40;  // Will cause ArrayIndexOutOfBoundsException

        } catch (ArrayIndexOutOfBoundsException e) {

            System.out.println("Array Index doesn't exist"); // Friendly message to the user

            System.out.print(e.getMessage()); // Shows the exact error message (e.g., "Index 3 out of bounds for length 3")
            e.printStackTrace();               // Prints the full stack trace for debugging
        }

        // This line will still run because we handled the exception
        System.out.println("Hello");
    }
}


```

## 3. NullPointerException
```
A NullPointerException occurs when a reference variable is not pointing to any object, but we try to access its methods or properties.
```
```java

public class Main {
    public static void main(String[] args) {
        
        Person p = null;  // Reference variable 'p' is not pointing to any object
        
        try {
            System.out.println(p.getName()); //  Trying to call a method on null → NullPointerException
        } catch (NullPointerException e) {
            System.out.println("Object is null!");   // Custom friendly message
            System.out.println(e.getMessage());     // Shows Java's built-in message (usually null)
            e.printStackTrace();                    // Full stack trace (type, message, and line number)
        }
        
        System.out.println("Program continues..."); // Proves program didn’t crash
    }
}
```

# Practise Questions

## 1.Difference Between Exception and Error in Java ?

**Exception**

```
Represents conditions a program can recover from.

Can be caught and handled using try-catch.

Example:

FileNotFoundException → Ask user to choose another file.

SQLException → Retry database connection.
```
**Error**
```
Represents serious problems that are usually not recoverable.

Should not be caught and handled in most cases (though technically you can catch them, it’s not recommended).

Examples:

OutOfMemoryError → Program ran out of heap space.

StackOverflowError → Infinite recursion.
```

## 2. Explain the difference in behavior and exceptions between:
What happens if we try to access methods or properties on each of these variables?

```java
String name = null;   // Initialized with null
String name2;         // Declared but not initialized (local variable)
```
```
Case 1 – String name = null;

The code compiles.

The variable has been explicitly set to null, meaning it points to no object in memory.

If we try to call a method (e.g., name.length()), Java will throw a NullPointerException at runtime.

Case 2 – String name2;

The code will not compile if you try to use name2 before assigning a value.

Local variables in Java do not get default values.

Since it’s never initialized, the compiler gives an error before the program runs.

Therefore, no runtime exception occurs — the program can’t even start.

NOTE : If these variables were instance variables (declared at class level), both would automatically get a default value of null.

In that case, calling a method on either would cause a NullPointerException at runtime.


```

## 3. What is the purpose of the finally block?
```
finally is for code that must run no matter what — whether an exception happens or not. 

Example: Closing a database connection even if a query failed.
```
## 4. How do you create a custom exception?

Extend `Exception` (checked) or `RuntimeException` (unchecked) and throw it when a specific business rule fails.
```
```java
class AgeException extends Exception {
    public AgeException(String msg) { super(msg); }
}

```

## 5. Is a try block always required before a catch block?
```
Yes — catch must come after a try.

But a try can also be followed by a finally without a catch.
```

## 6. What types of exceptions are caught during compile time?
```
Checked exceptions — compiler forces us to handle them.

Example: FileNotFoundException, SQLException.
```
## 7. What are best practices for exception handling?

```
Catch only what we can handle → Don’t write a catch block if we can’t do anything meaningful to fix or respond to that exception.
Let it propagate to a higher level where it can be handled properly.

Log exceptions for debugging → Always log the full details (e.printStackTrace() or a logging framework) so root cause diagnosis is easy.

Show friendly messages to users → Never show technical error details to end users; use simple, helpful text. Example: “Something went wrong. Please try again.”

Clean up resources → Always close files, database connections, or network sockets in a finally block or use try-with-resources to prevent resource leaks.
```

## 8. What are throw and throws, and how do they differ?
```
throw → actually throws the exception object

throws → declares that a method might throw exceptions
```
## 9. How do you handle an exception?
```
By wrapping risky code in a try-catch and providing alternate steps.

Example: If payment gateway is down, show “Try again later” instead of crashing.
```
## 10. How can we catch multiple exceptions?
```
Either with : catch (IOException | SQLException e) { ... }  // Java 7+

or multiple separate catch blocks.
```
## 11. Differences between checked and unchecked exceptions?
```
Checked → compiler forces you to handle (IOException)

Unchecked → occurs at runtime, compiler doesn’t check (NullPointerException)
```
## 12. What is the difference between an exception and an error?
```
Exception → recoverable (e.g., file not found)

Error → serious problem, not recoverable (e.g., OutOfMemoryError)
```
## 13. What is exception chaining?
```
Passing one exception as the cause of another.

Helps keep original error details for debugging.
```
## 14. What is a stack trace and how does it help debug?
```
A detailed list showing where the exception happened in our code.

It includes class name, method, and line number.
```
## 15. Name the different types of exceptions in Java.
```
Checked (compile-time) & Unchecked (runtime)
```
## 16. Can a try block exist without a catch or finally?
```
No — it must be followed by either catch or finally (or both).
```
## 17. Difference between finally, final, and finalize?
```
finally → cleanup code block

final → keyword to make variable constant, method non-overridable, class non-inheritable

finalize() was a method called by Garbage Collector before object destruction, but it’s deprecated because cleanup should be done explicitly using try-with-resources or manual close methods."
```
## 18. What is try-with-resources?

```
try-with-resources is a try statement in Java that automatically closes resources (like files, database connections, sockets) after the try block ends.

It works with any class that implements the AutoCloseable (or Closeable) interface, so we don’t have to close resources manually in a finally block.

try (FileReader fr = new FileReader("a.txt")) 

```
## 19. Can multiple exceptions be caught in one catch block?
```
Yes, using - catch (IOException | SQLException e)

```
## 20. Can you rethrow an exception?
```
Yes — rethrowing means catching an exception in one method and then throwing it again so that it can be handled by another method higher up the call stack.

It’s often done when:

We want to log the exception or take some partial recovery steps,

But still let the caller method decide the final handling.
```

## 21. Why does an exception occur?
```
Because something unexpected happens in our code:

- File not found
- Database down
- Divide by zero
- Null reference access  

These can be due to programming mistakes or external problems.
```