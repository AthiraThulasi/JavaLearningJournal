# Encapsulation

## What is encaspsulation ?

```
Encapsulation protects the instance variables from invalid value assignments, which is achieved through public getter and setter methods by writing the validation logic.

```

## Real World Example

```

In a bank, there’s a minimum balance rule — say ₹5,000.

minium balance = 5000;

And if the minimum balance is not maintained, bank will charge a monthly fine of 500.

Without encapsulation, someone could set minBalance = 0, and suddenly no one gets charged the ₹500 penalty for not maintaining balance — costing the bank millions. 
```
```java

class BankAccount {
    int minBalance = 5000; // Rule for maintaining minm balance

    void showMinBalance() {
        System.out.println("Minimum Balance Required: ₹" + minBalance);
    }
}

public class Runner {
    public static void main(String[] args) {
        BankAccount account = new BankAccount(); // object creation // creating a real account
        account.showMinBalance();  // ₹5000

        // Anyone can directly change it to an invalid value
        account.minBalance = 0; // changed the balance to 0
        account.showMinBalance();  // 0 → Rule broken!
    }
}
```

## How can we achieve Encapsulation?
```
We can achieve encapsulation - by declaring the instance variable private.

"private" means - instance variables can be accessed only inside the class. So that no one can assign illegal values to instance variables.

```

```java

 class BankAccount {
    private int minBalance = 5000; // private instance variable

```

 ## What happens if we access the private variable in the main Runner class?

 ```java

 public class Runner {
    public static void main(String[] args) {
         BankAccount account = new BankAccount();
         account.minBalance = 0; // Compile-time error
    }
    }

    
    java gives error message - 

    Error in Intellij - minBalance has private access.
    Error in Eclipse - Field minBalance is not visible

    Reason: private variables can only be accessed within the class where they are declared. 
    Access from outside (even in the same package) is not allowed without public methods (getters/setters).

```
## How can we access a private variable inside main()?
```
we can access  private instance variables inside main - by Using public methods such as getters and setters.

Getter → Retrieves the value of a private instance variable.

Setter → Assigns a value to a private instance variable, passed as a parameter.

Can include validation logic to ensure only valid values are stored.

By using getters and setters, we achieve encapsulation.


```
## Code showing setters() and getters()

```java

package com.student.management.system.oop;

public class Student {
    private String name;
    private int age;
    private int rollNumber;

    // Getter and Setter for name
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name; // this initialize the instance variabe with the value we are passing
    }

    // Getter and Setter for age
    public int getAge() {
        return age;
    }

    public void setAge(int age) {
    if (age < 21 && age >= 10) {. // Validating age
        this.age = age; 
    } else {
        System.out.println("Invalid Age for Student!!");
    }
}

    // Getter and Setter for rollNumber
    public int getRollNumber() {
        return rollNumber;
    }

    public void setRollNumber(int rollNumber) { // validating rollnumber
    if (rollNumber >= 1) {
        this.rollNumber = rollNumber;
    } else {
        System.out.println("Invalid Roll Number");
    }
}


```
## Student Runener class
```java

package com.student.management.system.oop;

public class StudentRunner {
    public static void main(String[] args) {

        // Create Student object
        Student s1 = new Student();

        // Set values using setters
        s1.setName("John Doe");
        s1.setAge(15);
        s1.setRollNumber(101);

        // Get and print values using getters
        System.out.println(s1.getName());
        System.out.println(s1.getAge());
        System.out.println(s1.getRollNumber());
    }
}
```

## How to achieve encapsulation in java?

```
Declare instance variables private - It controls access to instance variables from outside the class.

Provide public getter and setter methods - It prevents invalid assignments by validating values before storing them.

```
## How to add setetrs and getters in our code?
```
1. Right-click inside your class file.
2. Select SOURCE (or use the menu bar: Code → Generate).
3. Click Generate Getters and Setters.
4. Select the fields you want to generate them for.
5. Click OK — the IDE will auto-create the methods.


```