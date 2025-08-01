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

## Think about this?
```
(1) But what if our class has 10+ FIELDS ? 

(2) What if some are OPTIONAL and some MANDATORY ? Can we keep adding more and more overloaded constructors?

(4) How does the constructor become messy in such cases?

```

## When we already have constructors, why do we need the Builder Design Pattern?
```
Constructors help initialize objects by assigning values to instance variables.

But when the number of parameters grows — especially optional vs required ones — constructors become:

Hard to read.

Easy to mess up the order of arguments.

Difficult to maintain.

Prone to error (e.g., passing values in the wrong order)

```
That’s where the Builder Design Pattern comes in:

It offers flexibility

It avoids constructor telescoping (multiple overloaded constructors)

It improves code readability and maintainability










## What is a Builder Design Pattern?
```
The Builder Design Pattern is used to create objects easily when there are many fields — especially when some fields are optional and some are mandatory.

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

Why do we use constructors?
To initialize object properties (instance variables) during object creation.

2. ❓ What happens when there are many instance variables?
Constructors become hard to read, error-prone, especially with many optional fields. This is called the telescoping constructor problem.

3. ❓ Can we use setters instead?
Yes, but setters make the object mutable and break immutability. Also, object creation becomes a two-step process — not clean for mandatory fields.

4. ❓ So what’s the better solution?
Use the Builder Design Pattern – it helps build complex objects step by step.

5. ❓ What does the builder do?
Instead of passing all fields to a constructor, we pass them to a separate Builder class using method chaining and then call .build() to construct the object.

6. ❓ Where is the constructor used in this pattern?
The real constructor is private, and the builder internally calls it during .build() with the collected values.