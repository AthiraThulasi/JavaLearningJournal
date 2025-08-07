# Builder Design Pattern

## Let's Understand: What is a Design Pattern and Why Do We Need It?

```
Design patterns are a toolkit of tried and tested solutions to common problems in software design.

They also help apply Object-Oriented Programming (OOP) principles in a more structured and scalable manner.

```

## Types Of Design Patterns!

```
| Type           | What it does                                   | Example Patterns             |
| -------------- | ---------------------------------------------- | ---------------------------- |
| Creational.    | Deals with how objects are created             | Builder, Singleton, Factory  |
| Structural     | Deals with how objects are organized/connected | Adapter, Decorator, Proxy    |
| Behavioral     | Deals with how objects communicate and behave  | Observer, Strategy, Iterator |
```

## Where Does Builder Design Pattern Fit?
```
The Builder Design Pattern is a creational design pattern.

It is used to build complex objects step by step, especially when there are many parameters or optional fields.

```

## Before We Dive In – Let’s Revisit: How Do Constructors Pass Values to Instance Variables?
```
Constructors are used to pass values to instance variables at the time of object creation.

When we create an object, the constructor gets triggered and sets values to those variables.

But what if a class has 10… 15… or even 25 instance variables?

Passing all of them through a constructor becomes hard to read and error-prone.

We'll end up writing multiple constructors with different combinations — this is called the Telescoping Constructor Problem.

It becomes messy and hard to maintain.
```
## So, What About Setters?
```
Why not create the object first and use setters to assign values?

Setters make the object mutable (values can change anytime).

It also turns object creation into a two-step process (not clean for required fields).

There's no guarantee that all mandatory fields are set before using the object.

```
## That’s Where Our Saviour Comes In — The Builder Design Pattern!

It offers flexibility.

It avoids constructor telescoping (multiple overloaded constructors).

        > Constructor telescoping happens when you create multiple constructors with different combinations of parameters to handle various configurations of an object.

It improves code readability and maintainability.


## What is a Builder Design Pattern?
```
The Builder Design Pattern is used to create objects step by step, when there are many fields — especially when some fields are optional and some are mandatory.

Instead of writing many constructors - We can -

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

Finally, we call .build() — and boom - we get a complete object.

So, since it BUILDS THE OBJECTS IN PARTS and then combines them into a final form — it's called the BUILDER DESIGN PATTERN!

```
## How builder design pattern works?

### Step 1: Create an Outer Class
### Step 2: Create a static inner class
### Step 3: Declare Same Instance Variables
### Step 4: Create Setter Methods in Builder
### Step 5: Create a Constructor in the Main Class
### Step 6: Add a build() Method in Builder
### Step 7: Use the Builder in Runner Class

## Step 1 : Create an Outer Class

```java
public class SimpleBuilderForStudent { // Main Class
    private final String name;
    private final int rollNumber;
    private final String course;
    private final Integer phoneNumber; // optional
```
}
```Create an OUTER CLASS and declare the instance variables .

Mark all instance variables as final helps make your object immutable — which is one of the big reasons to use the Builder pattern in the first place!

Benefits:

Once the object is created, values can’t be changed

Helps write safe and thread-safe code

Promotes cleaner design with guaranteed initialization


— But DO NOT pass all variables into the constructor.

But wait… If we’re not passing instance variables into the constructor, where do we pass them? 

```
```java

private SimpleBuilderForStudent(?????) // Constructor parked without passing anything for now.

Did you Notice - Constructor is private? why - we will find out later!

```

Let's park it here - We will come back after meeting an important person!

### Step 2: Create a static inner class & Step 3: Declare Same Instance Variables

```
The important person is  - Static Inner Class!

We create a STATIC INNER CLASS called - "Builder" inside our main class.

Declare the same instance variables as the outer class(SimpleBuilderForStudent).
```
   ```java
        public static class Builder { // Static Inner Class
         private String name;
         private int rollNumber;
         private int phoneNumber; 
         private String course;
            }
```
 ### Step 4: Create Setter Methods in Builder  - called Builder Methods!
```
One Important Thing to Note:

  > The RETURN TYPE of the setter method is Builder — but why?

  > Because we're inside the static inner class Builder, and this method needs to return the same Builder object (i.e., this) to allow method chaining.

What do the builder methods do? 
 
 > Each method in the builder class returns the same builder object(this) , so we can chain one call after another like a fluent sentence.

   This is called method chaining.

   It goes like this : Builder -> set name  -> return Builder -> set rollNumber > return Builder 

```
 ```java

    // Setter methods for each variable

    public Builder setRollNumber(int rollNumber) { // Builder - is the return type of the method.
                                                   // Since we're inside the static inner class Builder - This method returns a Builder object.
➤
    this.rollNumber = rollNumber; // this.rollNumber → Refers to the instance variable of the Builder class.
                    // rollNumber (on the right side) - is the method parameter (the local variable passed to the setter).
        return this;
    }

    // ... more setters
}
```

So now, the static inner class named Builder holds all the instance variables and their setter methods.

Yay! Now We found what we need to pass inside the constructor!

### Step 5: Create a Constructor in the outer Class
```
We’ll pass the Builder object into the outer class constructor, so that the outer class can access and use all the values.
```
```java
     private SimpleBuilderForStudent(Builder builder) { // Constructor with builder object

Builder → The class name of the static inner class (used as the data type)  

builder → The reference variable (holds the data when passed as a parameter)

  ```
  
### Why Is the Constructor private in Builder Pattern?
```
We make the constructor private so that:

   (1) Objects of the outer class cannot be created directly from outside using new.

   (2)  object can only be created inside the static Builder class, using the build() method.[We will see build() in the coming section]

   (3)  It ensures controlled, step-by-step construction of objects.

```
## Why the name Builder? Can we give any name to the static inner class?
```
Yes! Technically, We can name the static inner class anything we want. It's just a class.

But, Builder is the convention (not a rule) — and naming it "Builder" makes our code -

Easier to read

Instantly recognizable to other's going through the code.

```
## Why is the parameter type Builder?
```
When we create a constructor inside the main class, the constructor's parameter type must match the name of the inner class.

Because, Builder is the name of the static nested class we defined inside main class.

So, when we create a constructor inside the main class, its parameter type must match the name of that class

```
### Step 6: Add a build() Method in Builder! What it does?

The build() method is written inside the Builder class — and it is the final step of the Builder Design Pattern.

- Creates the final object of the outer class

- Finalizes the object construction process

- Takes the values stored in the Builder object

- Passes them to the outer class via its constructor

- Returns the fully built object

// Build method to create final object
```java
         public SimpleBuilderForStudent build() {

         return new SimpleBuilderForStudent(this); // Final object is created here

         // This build() method is called at the end in the runner class, after all the setter methods are chained.
      }
```
### Step 7: Create a Runner Class and Call the Builder
```

In the Runner class, we create a Builder object and use method chaining to set the values.

At the end, we call .build() — this is the step that creates the final object.

The .build() method called from the Runner class, but it is defined inside the static inner Builder class.

nside .build(), we use new Student(this) to call the outer class constructor.

It passes the Builder object to that constructor.

The constructor then instantiates the outer class's instance variables using the values stored in the Builder.

 The constructor is accessible because the Builder class is defined within the same outer class.


```
```java
public class StudentRunner {
    public static void main(String[] args) {
        Student student = new Student.Builder() //  Start building the Student object using Builder pattern
                              .setName("Athira")
                              .setRollNumber(101)
                              .setPhoneNumber(9876543210)
                              .setCourse("SDET 2025")
                              .build(); // Final object created here

        System.out.println("Student created: " + student);
    }
} 
```

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
26.      public static class Builder {
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

```java
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
```
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