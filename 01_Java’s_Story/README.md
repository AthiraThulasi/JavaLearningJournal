# Java's Story

```
"Write Once, Run Anywhere” (WORA) - The promise that made Java a legend! 

Java's official slogan - introduced by Sun Microsystems when Java was launched in the mid-1990s.

```
### What it means?

```
We can write Java code on one platform (say, Windows), compile it to bytecode, and then run it anywhere — Linux, macOS, embedded systems — as long as a 

Java Virtual Machine (JVM) exists there. 

We don’t need to rewrite our code for each OS.
```
### Facts:

```
Created by James Gosling at Sun Microsystems in 1995.

Originally called Oak, renamed to Java (inspired by coffee!)

Platform-independent thanks to the JVM (Java Virtual Machine)

Runs billions of devices — from Android apps to ATMs!
```

### Major Java Version Highlights!
```

| Version        | Year       |  Major Highlights                                                  |
| -------------- | ---------- | ------------------------------------------------------------------ |
| Java 1.2       | 1998       | Introduced Collections Framework (List, Set, Map)                  |
| Java 5         | 2004       | Generics, Annotations, Enhanced for-loop, Enum                     |
| Java 8         | 2014       | Lambda Expressions, Streams API, Functional Interfaces             |
| Java 9         | 2017       | Modular System (Project Jigsaw)                                    |
| Java 10–14.    | 2018–2020  | var keyword, Switch Expressions, Text Blocks                       |
| Java 17        | 2021 (LTS) | Sealed Classes, Pattern Matching                                   |
| Java 21        | 2023 (LTS) | Performance boosts, new preview features like String Templates     |
```
### JAVA'S main components !
```
| Component     | Role                                                       |
| ------------- | ---------------------------------------------------------- |
| Java Code     | What we write (.java file)                                 |
| Compiler      | Converts .java to .class (bytecode)                        |
| Bytecode      | Intermediate code everyone understands                     |
| JVM           | Runs the bytecode on any computer                          |
| JRE           | Java Runtime Environment (JVM + libraries to run the code) |
| JDK           | Java Development Kit (JRE + tools to write & compile code) |
```

###  JVM - Java Virtual Machine
```
- Runs the compiled `.class` bytecode.
- Converts bytecode to machine code line by line.
- Part of JRE.
```
###  JRE - Java Runtime Environment
```
- Contains JVM + essential libraries to run Java programs.
- Does NOT contain development tools like compiler.
```
### JDK - Java Development Kit
```
- JRE + development tools (javac, debugger, etc).
- Used to write and compile Java programs.
```
### Java Execution Flow !

```java 
System.out.println("Hi, I'm Java!");

```
```
+-------------------+        +--------------------+       +-------------------+
|   Our Java Code  |         |     Compiler       |       |     JVM           |
|  (MyProgram.java) | -----> | (javac command)    | ----> | (Java Virtual     |
|                   |        | Converts to        |       | Machine) runs the |
|                   |        | Bytecode (.class)  |       | Bytecode          |
+-------------------+        +--------------------+       +-------------------+
                                                          |
                                                          v
                                                +-----------------------+
                                                |   Output on Screen    |
                                                |   "Hi, I'm Java!"     |
                                                +-----------------------+

```

