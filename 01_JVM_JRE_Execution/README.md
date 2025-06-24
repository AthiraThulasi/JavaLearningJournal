# 01 - Introduction to Java: JVM, JRE, JDK, and Program Execution


**What is Java**?

Java is a **high-level, object-oriented programming language** known for being platform-independent, which means we can write code once and run it anywhere.

 # JDK

**JDK** stands for **Java Development Kit**. It is what we install to **write, compile, and run** Java programs.

JDK includes:
- JRE (Java Runtime Environment)
- Tools like `javac` (compiler), `java` (runner)

 # JRE

**JRE** stands for **Java Runtime Environment**.
It is used to **run** Java applications and contains:
- JVM (Java Virtual Machine)
- Pre-built libraries needed during runtime

We **can’t write or compile code** with JRE — only run it.

# JVM

**JVM** stands for **Java Virtual Machine**.
It’s the part of Java that actually **executes our compiled `.class` files** (bytecode).

JVM makes Java platform-independent by running the same bytecode on different operating systems.


# How Java Code Runs (Simple Flow)

Our Code (.java)
      Compile using javac

Bytecode (.class)
      Run using JVM

Output on screen

# Detailed Explanation

# Our Code (.java)
This is the human-readable source code weßß write, saved with a .java extension (e.g., MyProgram.java). It contains instructions, logic, and syntax following the Java language rules.

# Compile using javac (Java Compiler)
The javac command (part of the Java Development Kit - JDK) takes our .java source files.
It translates this human-readable code into a platform-independent intermediate format called bytecode.
If there are any syntax errors in our code, javac will report them, and the compilation will fail.

# Bytecode (.class)
This is the compiled output, saved with a .class extension (e.g., MyProgram.class).
Bytecode is a low-level, machine-independent instruction set that is understood by the Java Virtual Machine (JVM). It's not directly executable by our computer's operating system or processor. This "write once, run anywhere" capability is a key feature of Java, as the same bytecode can run on any system with a compatible JVM.

# Run using JVM (Java Virtual Machine)
The java command takes our .class bytecode files.
The JVM acts as a runtime environment. It reads the bytecode instruction by instruction.
Inside the JVM, there's a Just-In-Time (JIT) compiler. The JIT compiler can convert frequently executed bytecode sequences into native machine code at runtime, which significantly improves performance.
The JVM also manages memory (garbage collection) and handles other runtime aspects.

# Output on screen
The result of our program's execution, displayed in the console or performing its intended actions (e.g., file operations, network communication, GUI display).