# Builder Design Pattern

## Let's Understand: What is a Design Pattern and Why Do We Need It?

```markdown
Design patterns are a toolkit of tried and tested solutions to common problems in software design.

They also help apply Object-Oriented Programming (OOP) principles in a more structured and scalable manner.

```

## Types Of Design Patterns!

```markdown
| Type           | What it does                                   | Example Patterns             |
| -------------- | ---------------------------------------------- | ---------------------------- |
| Creational     | Deals with how objects are created             | Builder, Singleton, Factory  |
| Structural     | Deals with how objects are organized/connected | Adapter, Decorator, Proxy    |
| Behavioral     | Deals with how objects communicate and behave  | Observer, Strategy, Iterator |
```

## Where Does Builder Design Pattern Fit?
```markdown
The Builder Design Pattern is a creational design pattern.

It is used to build complex objects step by step, especially when there are many parameters or optional fields.

```

## Before We Dive In – Let’s Revisit: How We Usually Pass Values — Using Constructors?
```markdown
A constructor is a special method that has the same name as the class.

It is used to initialize objects and pass values to instance variables at the time of object creation.

Typically, we pass all the required values (i.e., instance variables) directly into the constructor.

But what if a class has 10… 15… or even 25 fields? Passing all of them through a constructor becomes hard to read and error-prone.

We'll end up writing multiple overloaded constructors with different combinations - this is called the Telescoping Constructor Problem.

It becomes messy and hard to maintain.

```
## So, What About Setters?
```markdown
Why not create the object first and use setters to assign values?

Setters make the object mutable (values can change anytime).

It also turns object creation into a two-step process (not clean for required fields).

There's no guarantee that all mandatory fields are set before using the object.

```
## So what's the Solution? That’s Where Our Saviour Comes In — The Builder Design Pattern!
```markdown
Builder Design Pattern offers flexibility.

It avoids constructor telescoping (multiple overloaded constructors).

        > Constructor telescoping happens when we create multiple constructors with different combinations of parameters to handle various configurations of an object.

It improves code readability and maintainability.

```

## What is a Builder Design Pattern?
```markdown
The Builder Design Pattern is used to create objects step by step, when there are many fields — especially when some fields are optional and some are mandatory.

Instead of writing many constructors - We can :

   > Build the object step-by-step.

   > Set values using method calls.

   > Finally, call .build() to get the object.

   > It makes code cleaner, readable, and less confusing.

```
## Why is it called Builder Design Pattern?

```markdown
Because, It literally "builds" the object step-by-step — like how a builder constructs a house.

We don’t dump everything into one messy constructor.

Instead, we call methods one by one to set values (like putting walls, windows, and paint).

Finally, we call .build() — and boom - we get a complete object.

So, since it BUILDS THE OBJECTS IN PARTS and then combines them into a final form — it's called the BUILDER DESIGN PATTERN!
```

# How builder design pattern works?

## Step 1 : Create an Outer Class


```java
public class SimpleBuilderForStudent { //  Outer Class
    private final String name; // Mandatory 
    private final int rollNumber; 
    private final String course;
    private final Integer phoneNumber;  // Non - Mandatory
    }
```

```

Create an OUTER CLASS and declare the instance variables .

NOTE:  Mark all INSTANCE VARIABLES as 

                           (1) FINAL (one of the big reasons to use the Builder pattern in the first place)

                           (2) PRIVATE  
```
```
| Modifier  | Why We Use It                                                                                                 |
| --------- | --------------------------------------------------------------------------------------------------------------|
| `private` | To enforce encapsulation — variables can't be accessed directly from outside.                                 |
| `final`   | To ensure the variables are assigned only once (usually in the constructor), making the object IMMUTABLE.     |

```
### Why instance variable is Final ?
```
When we declare instance variables as final > helps make our object immutable - they can be assigned only once (usually in the constructor).

After the object is built, its values cannot be changed !

Immutability improves: (1) Thread safety (2) Reliability (3) Ease of debugging.
```

### Why Use private instance variable?
```
1. Hides the variable from outside the class
So no one can change it directly

2. Keeps the data safe
Only the class (or builder) can control how values are set
```

### Let's create Constructor - and see whom should we pass to the constructor!
```
In traditional constructors, we’d pass all the variables like -  SimpleBuilderForStudent(String name, int roll, String course, Integer phone) 

But with the Builder Design Pattern, we do it differently! 

Let's park it here - We will decide whom to pass to constructor -  after meeting an important person!
 ```
```java

private SimpleBuilderForStudent(?????) // Constructor parked without passing anything for now.

```

## Step 2: Create a static inner class & Step 3: declare the same instance variables as outer class

```
Static Inner Class - Create a STATIC INNER CLASS called - "Builder" inside our outer class.

The Builder holds all the data needed to build the object.

It uses the same variables as the outer class (but without final).

This inner Builder class acts as a data carrier.

Instead of passing each value separately to the outer class constructor > we pass the whole Builder object — which contains all the necessary values.

So now we clearly understand whom we should pass to the constructor —It’s the Builder, not the individual variables.

```
   ```java
        public static class Builder { // Static Inner Class
         private String name;
         private int rollNumber;
         private int phoneNumber; 
         private String course;
            }
```
 ## Step 4: Create Setter Methods in Builder  - called Builder Methods!

 ```java

The setter methods in the Builder class is used to assign values to the variables in the static Builder class.

These values are stored temporarily and later used to create the final object when .build() is called.

    
    // Setter methods for rollNumber 

    public Builder setRollNumber(int rollNumber) {  //  Return type of the method setRollNumber -  Builder
                                                   // Since we're inside the static inner class Builder - This method returns a Builder object.
➤
    this.rollNumber = rollNumber;                 // this.rollNumber → Refers to the instance variable of the Builder class.
                                                 // rollNumber (on the right side) - is the method parameter (the local variable passed to the setter).
        return this;                            // 'this' refers to the current Builder object
    }

    // ... more setters
}
```

```
One Important Thing to Note:

 The RETURN TYPE of the setter method is Builder — but why?

 Because we're inside the static inner class Builder, and this method needs to return the same Builder object (i.e., this) to allow method chaining.


```
```
What do the builder methods do? 
 
  Each method in the builder class returns the same builder object(this) , so we can chain one call after another like a fluent sentence.

   This is called method chaining.
  
   Method Chaining : Builder -> set name  -> return Builder -> set rollNumber > return Builder.
  
   So now, the static inner class named Builder holds all the instance variables and their setter methods.

```

## Step 5: Create a Constructor in the outer Class
```
Since the Builder class already holds all the required values through its instance variables and setter methods,

we don’t need to pass each variable separately to the outer class constructor.

Instead, we pass the Builder object itself, and the outer class can access all the values from it to initialize its own fields.
```
```java
     private SimpleBuilderForStudent(Builder builder) { // Constructor with builder object

Builder → The class name of the static inner class (used as the data type)  

builder → The reference variable (holds the data when passed as a parameter)
```


## Why the name Builder ? Can we give any name to the static inner class?
```
Yes! Technically, We can name the static inner class anything we want. It's just a class.

But, Builder is the convention (not a rule) — and naming it "Builder" makes our code - (1) Easier to read  (2) Instantly recognizable to other's going through the code.

```
## why the constructor takes Builder as a parameter ?

```java
private SimpleBuilderForStudent(Builder builder)
```

```
The parameter type of the constructor is Builder because that's the name of the static nested class inside outer class - SimpleBuilderForStudent.

We pass a Builder object to this constructor so that we can access all the values that were set using the Builder methods and use them to initialize the outer class fields.

```
## Step 6: Add a build() Method in Builder! What it does?

```
The build() method is written inside the Builder class — and it is the final step of the Builder Design Pattern.

- Creates the final object of the outer class

- Finalizes the object construction process

- Takes the values stored in the Builder object

- Passes them to the outer class via its constructor

- Returns the fully built object

```
```java

// Build method to create final object

         public SimpleBuilderForStudent build() {

         return new SimpleBuilderForStudent(this); // Final object is created here

         // This build() method is called at the end in the runner class, after all the setter methods are chained.
      }
```
## Step 7: Create a Runner Class and Call the Builder

### Why do we need a Runner class?
```
The Runner class is used to test and create objects using the Builder pattern.

It helps demonstrate how we can set values using method chaining and finally build the actual object of the outer class.

```
### What happens inside the Runner class?
```
We first create an object of the Builder class.

Then we use method chaining to set the required fields.

At the end, we call .build() — this is the step that creates the final object of the outer class.
```
```java

SimpleBuilderForStudent student = new SimpleBuilderForStudent.Builder()
                                       .setName("Athira")
                                       .setRollNumber(101)
                                       .setCourse("Java")
                                       .build(); //  Creates the final object

```
### What does .build() do?
```
.build() is a method defined inside the static Builder class.

It uses new SimpleBuilderForStudent(this) to call the private constructor of the outer class.

It passes the current Builder object (this) to the constructor.

The constructor extracts all the values from the Builder object and initializes the outer class’s fields.

This works because both the Builder class and the constructor exist inside the same outer class, even if the constructor is private.
```
### How to handle Optional Fields in Builder ?
```
In the Builder pattern, if a field is optional (like phoneNumber) - we simply don’t call its setter in the Runner class.

The field will take its default value (e.g., 0 for int, null for String).
```
### Notes:
```
If we skip setPhoneNumber( ) >> it will stay as default 0.

If we skip setCourse() >> it will stay as null.

We don’t need any special logic — just don’t call the setter!
```

### Do we need to write the setter method for an optional field?
```
 Yes, we should write the setter — even if it's optional.
```
### But why write it if we’re not always passing values?
```
Because the Builder Pattern gives users the choice to set only the fields they want. We’re not forcing them — we’re just making the option available.

Even if the field is not always set, it’s part of the class design — and without the setter: The user can’t set the value even if they want to and object becomes inflexible and incomplete.
```
### Builder Design code with comments !

```java
  package builderdesignpatternpractice;

public class SimpleBuilderForStudent {

  
    // Making instance variables final to ensure immutability after object creation
    private final String name;        // Mandatory
    private final int rollNumber;     // Mandatory
    private final int phoneNumber;    // Optional
    private final String course;      // Optional

    // Step 5: Constructor of outer class accepts Builder object - Instead of passing each field, we pass the Builder object
    private SimpleBuilderForStudent(Builder builder) {
        this.name = builder.name;
        this.rollNumber = builder.rollNumber;
        this.phoneNumber = builder.phoneNumber;
        this.course = builder.course;
    }

    // Optional: toString method for printing object details
    @Override
    public String toString() {
        return "SimpleBuilderForStudent{" +
                "name='" + name + '\'' +
                ", rollNumber=" + rollNumber +
                ", phoneNumber=" + phoneNumber +
                ", course='" + course + '\'' +
                '}';
    }

    // Step 2: Static Inner Builder Class
    public static class Builder {

    // Step 3: Declare same fields as outer class
        private String name;
        private int rollNumber;
        private int phoneNumber;
        private String course;

        // Step 4: Create setter methods (method chaining enabled by returning 'this')

        public Builder setName(String name) {
            this.name = name;
            return this; // Allows method chaining
        }

        public Builder setRollNumber(int rollNumber) {
            this.rollNumber = rollNumber;
            return this;
        }

        // Optional field: phoneNumber
       public Builder setPhoneNumber(int phoneNumber) {
           this.phoneNumber = phoneNumber;
           return this;
}

        }

        public Builder setCourse(String course) {
            this.course = course;
            return this;
        }

        // Step 6: Build method to return the final object
        public SimpleBuilderForStudent build() {
            return new SimpleBuilderForStudent(this); // Pass builder to outer class constructor
        }
    }
}

```
## Runner

```java
 package builderdesignpatternpractice;

public class StudentRunner {
    public static void main(String[] args) {

        // Step 7: Create Builder object and chain setters
        SimpleBuilderForStudent student = new SimpleBuilderForStudent.Builder()
                .setName("Athira")           // Mandatory
                .setRollNumber(101)          // Mandatory
                //.setPhoneNumber(123456789)   // Optional: skipped
                .setCourse("Java")           // mandatory
                .build();                    // Final object created

        // Print object content
        System.out.println(student);
    }
}

```

