# 📘 Writing the First Code

## Where Do Java Files Go?

## Java Source File Location

- All Java source files are typically stored inside a **`src`** (source) folder.
- Java source files use the **`.java`** extension.
- It's best practice to organize source files using **packages**.

src

└── javaprograms

└── MyClass.java



##  Package 

- A **package** in Java is like a folder on our computer.
Just like a folder can contain many files, a package can contain many Java classes (files).

- Helps in:
  - Organizing code
  - Avoiding name conflicts
  - Controlling access

**Syntax to declare a package:**

package javaprograms;

package is a **reserved keyword** in Java.

Package names should be written in **lowercase** by convention.


## Java Program Structure

A basic Java class looks like this:

public class Example {

    public static void main(String[] args) {

        // Code block starts

        // Write your logic here

        // Code block ends
    }
}

## Bracket Visualization
Below is a version of the program that highlights where each block starts and ends:

// Class starts here 👇
public class HelloWorld {

    // Method starts here 👇
    public static void main(String[] args) {
        System.out.println("Hello, Java!");

    } // 👈 Method ends here

} // 👈 Class ends here


##  Key Components Explained

| Part                  | Meaning                          |
|-----------------------|--------------------------------------------|
| `public class`        | Declares a class accessible from anywhere  |
| `main(String[] args)` | Entry point of the Java program            |
| `{ }`                 | Code block boundaries                      |
| `args`                | Runtime arguments passed during execution  |


## Can We Create a `private` Class?

In Java:

- A **top-level class** is a class declared directly in a `.java` file (outside of any other class).
- A **nested class** is a class defined **inside another class**.

---

| Class Type                  | Allowed? | Explanation                                                               |
|-----------------------------|----------|---------------------------------------------------------------------------|
| **Top-level private class** | ❌ No     | Java requires the main class to be accessible — `public` or default only. |
| **Nested private class**    | ✅ Yes    | A private class *inside* another class is allowed, used for hiding logic. |

---

**Simple Tip to Remember:**

> A **nested class** is like a helper class that lives *inside* another class.  
> A **top-level class** is the outer class — and it **cannot** be `private` because Java needs to access it to run our code.



##  How many Public Classes allowed per java file?

Only one public class is allowed per .java file, and the file name must match the public class name.

// File name: MyClass.java


public class MyClass {

    public static void main(String[] args) {

        System.out.println("Hello");
    }
}
✅ File name = MyClass.java

✅ One public class = MyClass

## Why multiple public classes not allowed in java?

**Entry Point Clarity**  

   - The Java compiler and JVM need a clear, unambiguous entry point for program execution.

   - Allowing multiple public classes would create confusion about which one to load.

## What You Cannot Do - Adding multiple public class!

// File name: MyFile.java

public class A {
    
}

public class B {
    // ❌ Compilation error: Only one public class is allowed
}



## Summary

Place .java files under src/package_name/.

Always start the file with a package declaration (unless in the default package).

Only one public top-level class is allowed per .java file.

Class name must match the filename when using public.


## Interview Question

**Q: Why does Java allow only one public class per `.java` file? What happens if you try to define two public classes in the same file?**


Java enforces a one-to-one relationship between the public class and the file name for clarity, maintainability, and proper class loading by the JVM.

- If two public classes are defined in the same `.java` file, the compiler will throw an error:  
  *“The public type X must be defined in its own file.”*

- Only one class can be public, and its name **must match the file name**.


