# Methods


##  What is a Method?
```
A method is a code block designed to perform a specific task. It is like an instruction that tells the program to do something specific, like an action.
```
## Think of it like giving a command to do something:
```
print the bill

calculate total

Login with credentials
```

## How to define a method structure ?

```java

returnType methodName(argument1, argument2) { // Method Signature // arguments are the local variables(stored in stack memory) passed into the methods
    
 //  What we are going to do inside the method body
}
```
## What is a Method Signature?
```
Method Signature is  - Method Name + Return Type + Parameter List (argument1, argument2)**
```

```text
  
    int addNumbers(int a, int b)                   // Method Name + Return Type + Parameter List (argument1, argument2)
    ↑     ↑         ↑        ↑
    |     |         |        |
 Return  |     Argument1   Argument2
  Type   |   (local var)  (local var)
         |
     Method Name
```


## What is a Method Declaration?
```
What we are going to do inside the braces (code block)!
```
##  What is a Return Type ? 
```
The return type tells us what the method will give back after execution (the type). It is specified before the method name during definition.
```
# Let's learn from examples!

## 1. Method With Return Type (int)

```
Adding two numbers returns a number as result. So int is the return type of this method.
```
```java

public int addNumbers(int a, int b) { // Adding two numbers returns a number as result. So int is the return type of this method.

    return a + b; // returns sum of two numbers (int)
}
```

## 2. Method with Return Type (String)
```
This method returns name which is of type String.
```
```java

public String greet(String name) {

    return "Hello, " + name + "!"; // returns name which is of type String
}
```

## 3. Method with void Return Type

```
This method performs an action (printing), but doesn't return anything — so the return type is void.

void is a reserved keyword in java.

```
```java

public void printWelcome() {.    // void is a reserved keyword in java

    System.out.println("Welcome to Java Learning Journal!"); //This method returns a String greeting message based on the input.
}
```

## Real-Life Actions → Method Names in Java

```

| Real-Life Action                 | Method Name (Java)        | Return Type Example | What It Might Do                                      
|----------------------------------|---------------------------|----------------------|--------------------------------------------------------|
| Print the bill                   | printBill()               |   void               | Prints the bill to a printer or screen                |
| Calculate total price            | calculateTotal()          |    int               | Returns total after adding price + tax                |
| Show welcome message             | showWelcomeMessage()      |    void              | Displays a welcome message on screen                  |
| Check if user is logged in       | isUserLoggedIn()          |   boolean            | Returns `true` or `false` based on login status       |
| Get full name from first & last  | getFullName()             |   String             | Combines first and last name and returns full name    |
| Read input from user             | readInput()               |   String             | Reads and returns user input from console             |
| Save data to file                | saveToFile()              |   void               | Saves current data to a file                          |
| Convert Celsius to Fahrenheit    | convertTemperature()      |  `double              | Converts temp and returns the Fahrenheit value       |
```

## Benefits of Using Methods
```

REUSABILITY – Write once, use many times. Avoid repeating the same logic.

READABILITY – Code becomes easier to understand and maintain.

MODULARITY – Breaks large programs into smaller, manageable pieces.

```

## Best Practices
```
Keep methods small and do one task per method.

Create reusable methods to avoid redundancy.
```
## Types of Methods
```
| Type             | Description                                         |
|------------------|-----------------------------------------------------|
| Static Methods   | Utility methods that belong to the class            |
| Instance Methods | Non-static methods that belong to objects           |
```

## Utility Method -  Use Cases
```
Reading from CSV

Taking screenshots

Connecting to a database
```

