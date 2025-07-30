# Builder Design Pattern


## What is Builder Design Pattern?
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