# Builder Design Pattern
```
Before diving into the Builder Design Pattern, let’s revisit why we use constructors and how they help in object creation ?
```
## Constructor and Object Creation – A Quick Recap 
```
When we create an object, the class gets loaded into memory.

The constructor is automatically called at the time of object creation.

The constructor initializes instance variables.

If we don’t define a constructor, Java provides a default constructor.
```
```java

Employee e = new Employee("Athira", "QA Engineer", 5);

new triggers the constructor → which sets values → object is created and initialized in heap memory.

```

## The Limitations of Using Constructors with Optional and Mandatory Fields !

```
(1) What if our class has 10+ FIELDS - some are OPTIONAL and some MANDATORY ? 
    
    > When the number of parameters grows — especially optional vs required ones -  When a class has both required and optional fields, we often write multiple overloaded constructors to support different combinations
    
    — constructors become:

  (1) Hard to read.

  (2) Easy to mess up the order of arguments.

  (3) Difficult to maintain.

  (4) Prone to error (e.g. passing values in the wrong order)
    
(2) Can we use setters instead?
    
    > Yes, but setters make the object mutable and break immutability. Also, object creation becomes a two-step process — not clean for mandatory fields.

```
## That’s Where Our Saviour Comes In — The Builder Design Pattern!

It offers flexibility.

It avoids constructor telescoping (multiple overloaded constructors).

        > Constructor telescoping happens when you create multiple constructors with different combinations of parameters to handle various configurations of an object.

It improves code readability and maintainability.


## What is a Builder Design Pattern?
```
The Builder Design Pattern is used to create objects step by step, when there are many fields — especially when some fields are optional and some are mandatory.

Instead of writing many constructors, we:

   > Build the object step-by-step.

   > Set values using method calls.

   > Finally, call .build() to get the object.

   > It makes code cleaner, readable, and less confusing.

```
## Why is it called Builder Design Pattern?

```
Because, It literally "builds" the object step-by-step — like how a builder constructs a house.

We don’t dump everything into one messy constructor.

Instead, we call methods one by one to set values (like putting walls, windows, and paint).

Finally, we call .build() — and boom, we get a complete object.

So, since it BUILDS THE OBJECTS IN PARTS and then combines them into a final form — it's called the BUILDER DESIGN PATTERN!

```
## How builder design pattern works?
```
In the Builder Design Pattern, instead of passing all instance variables directly into the constructor (which can become messy with many parameters)

we follow a cleaner and more flexible approach.

    >  Create a main class (e.g. `Student`) — but DO NOT pass all variables directly into the constructor.

    >  Inside the main class, we define a STATIC NESTED BUILDER CLASS and declare the same fields as in the outer class .

    >  Pass an OBJECT of this static nested class called `Builder` to the constructor. 
    
    > The type of the OBJECT passed in the constructor should be the name of STATIC NESTED BUILDER CLASS .

    > Add "setter-style" methods (e.g., `withName()`, `withPhone()`, etc.) inside the Builder class that return the `Builder` object itself — enabling method chaining.

    >  Define a `build()` method inside the Builder class that returns a new object of the main class by calling its private constructor and passing `this` (the current Builder object).

    >  In the main class's private constructor, use the received `Builder` object to assign values to the main class fields.

```
## Builder Design Explanation with code

```java
1.  package builderdesignpatternpractice;

2.  public class SimpleBuilderForStudent {

3.      // instance variables
4.      private String name;
5.      private int rollNumber;
6.      private int phoneNumber;
7.      private String course;

8.      // private constructor to accept builder and initialize fields
9.      private SimpleBuilderForStudent(Builder builder) {
10.         this.course = builder.course;
11.         this.name = builder.name;
12.         this.rollNumber = builder.rollNumber;
13.         this.phoneNumber = builder.phoneNumber;
14.     }

15.     // Override toString() to display object content
16.     @Override
17.     public String toString() {
18.         return "SimpleBuilderForStudent{" +
19.                 "name='" + name + '\'' +
20.                 ", rollNumber=" + rollNumber +
21.                 ", phoneNumber=" + phoneNumber +
22.                 ", course='" + course + '\'' +
23.                 '}';
24.     }

25.     // Static inner Builder class
26.     public static class Builder {
27.         private String name;
28.         private int rollNumber;
29.         private int phoneNumber;
30.         private String course;

31.         // Setter for name
32.         public Builder setName(String name) {
33.             this.name = name;
34.             return this;
35.         }

36.         // Setter for rollNumber
37.         public Builder setRollNumber(int rollNumber) {
38.             this.rollNumber = rollNumber;
39.             return this;
40.         }

41.         // Setter for phoneNumber
42.         public Builder setPhoneNumber(int phoneNumber) {
43.             this.phoneNumber = phoneNumber;
44.             return this;
45.         }

46.         // Setter for course
47.         public Builder setCourse(String course) {
48.             this.course = course;
49.             return this;
50.         }

51.         // Build method to create final object
52.         public SimpleBuilderForStudent build() {
53.             return new SimpleBuilderForStudent(this);
54.         }
55.     }
56. }
```
## Runner
1.  package builderdesignpatternpractice;

2.  public class StudentRunner {
3.      public static void main (String[] args) {

4.          // Creating object using builder pattern, skipping optional field
5.          SimpleBuilderForStudent student = new SimpleBuilderForStudent.Builder()
6.                  .setName("Athira")
7.                  .setRollNumber(101)
8.                  .setPhoneNumber(123456789)
9.                  // .setCourse("Java") — Skipped to test default value
10.                 .build();

11.         System.out.println(student);
12.     }
13. }

How it works (Step-by-Step)

Builder is a static inner class inside SimpleBuilderForStudent.

It holds the same fields as the outer class.

Setter methods like setName() return the Builder object itself — allowing method chaining.

When .build() is called, it creates the outer class by passing the builder instance.

The private constructor in the outer class uses the builder's values to initialize fields.

If any optional fields are not set, you can assign a default value (like "Not Assigned").

🧠 Real-World Analogy:

📦 Think of the Builder as a box with compartments:

First, you set the name → the name compartment now holds "Athira"

Then you return the box (Builder) so you can add:

rollNumber → that compartment gets 101

phoneNumber → add that too

Finally, you call .build() to wrap up and hand over the final product 🎁 (a SimpleBuilderForStudent object)

✅ Why use Builder Pattern?

Avoids constructor confusion when many parameters exist (especially optional ones)

Makes object creation more readable, modular, and maintainable

Prevents issues like telescoping constructors

Supports optional fields without creating multiple constructors


Non - Mandatory
Exactly ✅ — if a field is not mandatory, you simply don’t call its setter in the runner class. That’s the beauty of the Builder Pattern.

🔁 Here's how it works:
✅ Optional field (e.g., course)
You define it in both outer and builder class.

But in the runner, you can skip calling .setCourse()