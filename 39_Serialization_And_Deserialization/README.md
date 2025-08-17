## Serialization & De - Serialization !
```
Let’s start with a simple example of creating an object in Java. 

This will help us understand where the object lives in memory and why we eventually need serialization ?
```
```java
Contact contactPerson = new Contact("Java", "9876543210"); // This line creates an object contactPerson .
```
 
##  Where is this Object Stored?
```
 It is stored in heap memory, which is part of volatile memory (short term memory) in Java.
 ```
## How Long Does It Stay There?
```
Only as long as the program is running.

Once the program ends, the JVM shuts down, and all memory (heap, stack, static) is cleared by the OS.

That’s why heap memory is called volatile memory.
```
## Different Types of Memory !

```
|  Memory Type          |     Description                        |   Examples          |
|-----------------------|--------------------------------------- |---------------------|
|  Volatile Memory.     | Temporary, lost after program ends     | Heap, Stack, Static |
| Persistent Memory     | Long-term, survives after program ends | File, Database      |
```
 
## So What If We Want to Save This Object After the Program Ends?
```
We need to store the object in persistent memory, like a file or database - To do this, we use Serialization.

```
 
## What is Serialization?
```
Serialization is the process of converting a Java object into a byte stream so that it can be:

	> Saved to a file (.ser)

	> Sent over a network

	> Stored in a database
```
## Why Use Serialization?
```
   > To store Java objects permanently

   > To send objects across a network

   > To retrieve object data later

   Example: In Instagram — our profile and data are saved permanently even after we close the app - That’s persistent memory.
```

## Requirements for Serialization
```
The class must implement the Serializable interface

```
## What is Serializable interface?
```
The Serializable interface in Java is a marker interface from the java.io package.

It has no methods — that’s why it’s called a marker interface.

It is used to indicate that a class can be serialized — i.e., its objects can be converted into a byte stream and saved to a file or sent over a network.

Add the transient keyword to variables that don’t need to be serialized — i.e., variables that should not be saved permanently in the .ser file.

When a class implements Serializable, all its non-transient, non-static fields are included in the serialized form.

```
The following class Contact implements Serializable:

```java
package com.serialization;

import java.io.Serializable;

// Class must implement Serializable

public class Contact implements Serializable {
    private static final long serialVersionUID = 1L; // Add a serialVersionUID (recommended for version control)

    private String name;
    private String contactNumber;

    // transient → this field won't be saved during serialization
    private transient String emergencyContactNumber;
}
```
## Important

     >	If a class does not implement Serializable, and we try to serialize it, we'll get a NotSerializableException.

## How we write java object into a .ser File - Serialization!
  
```   

 FileOutputStream - Create FileOutputStream (fos) to open a file named contact.ser to write bytes into it.

 ObjectOuputStream - Wrap the byte-level file stream (fos) so we can write entire Java objects into it.

 Call writeObject () to perform serialization.

 ```
     
 ```java

 public class ContactRunner1 {
    public static void main(String[] args) {
        Contact contactPerson = new Contact("java", "9898989890", "1000000000");
        // Object created in heap memory (volatile)

        FileOutputStream fos; //  declare outside try block
        ObjectOutputStream oos;

        try {
            fos = new FileOutputStream("contact.ser"); 
            //  Opens/creates a file named contact.ser to write bytes into it

            oos = new ObjectOutputStream(fos); 
            //  Wraps the byte-level stream into object-level stream 
            // so we can write entire Java objects

            oos.writeObject(contactPerson); 
            //  Converts your object into byte stream and writes it into file
        } catch (IOException e) {
            e.printStackTrace(); // Or rethrow exception
        }

        System.out.println(contactPerson); 
        // Prints object (via toString), not the serialized bytes
    }
}
```
## What is contact.ser?
```	
It is a file that stores the object data in binary format [ blob file – Binary Large Obj]

It is not human-readable

We can use Deserialization to get the object back from it later
 ```
## Advantages of Serialization
```
Data Persistence: Information can be securely stored and can be reloaded at any time without the need for re-entry. 

Automation: The process of saving and retrieving data becomes automated, reducing manual intervention. 

Error Reduction: By minimizing human input, the chances of errors in data entry are significantly reduced.
```
## What is Deserialization?
```
Deserialization is the reverse process -

Reading the byte stream and converting it back to the original Java object.

We need to read the file(blob/stream file) and create object out of it. So we need fileinput stream for reading it

```
## How we read java object from a .ser file - Deserialization!

```
FileInputStream – Creates a stream to read bytes from a file.

ObjectInputStream – Wraps the FileInputStream and converts the byte stream back into a Java object (Deserialization).

readObject()  – This method is used to perform deserialization.

readObject() returns a value of type `Object`, which is the most general type in Java.

Since we know the actual object stored in the file is a `Contact`, we need to cast it back to `Contact` using type casting.

This process is called TYPE CASTING, where we convert the generic `Object` type to a specific class type (`Contact` in this case), like this:

Contact data = (Contact) ois.readObject();
```
```java
public class ContactRunner2 {
    public static void main(String[] args){

        FileInputStream fis;
        ObjectInputStream ois;
        try {
             fis = new FileInputStream("contact.ser"); //  Opens the .ser file to read bytes
            ois = new ObjectInputStream(fis);       //  Converts byte stream back to Java object
            Contact data = (Contact) ois.readObject();//
            //  Read the object from the file and convert it back into a Contact object
            System.out.println(data);                                 //  Prints the deserialized object
            //It's called type casting because we're converting the object’s type from Object (generic) to Contact (specific) using a cast.
            //  Always close streams after use
            ois.close();
            fis.close();
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace(); // Handles both IO and class load failures
        }

```
##  Final Takeaway
```
If we want to store Java objects permanently - use Serialization to save them to a .ser file.

Deserialization to bring them back when needed.
```
## Serializable: Parent-Child Relationship

```
If the parent class implements Serializable, then all child classes automatically become serializable.

If only the child class implements Serializable, but the parent does not, then - the parent’s fields will not be serialized.

During deserialization, the parent’s no-arg constructor will run to reinitialize those parent fields (since they weren’t saved).

```
# Serialization & Deserialization using File!

```
Using the File class in serialization/deserialization gives extra control over file handling (existence, metadata, directories), unlike basic serialization which directly uses file paths.

```

## When and Why to Use the File Class in Serialization?
```
- The `File` object is used to define the file path or name. It gives extra control to:

     > Check if file exists

     > Get file metadata

     > Work with directories

We can then pass it to `FileOutputStream` for writing the byte stream.
```
## Serialization using the File class
```java

//  Create Array of objects
Student[] studentArray = new Student[3];
studentArray[0] = s1;

for (Student s : studentArray) {
    System.out.println(s);
}

//  Using a File Object Before FileOutputStream
File serializedData = new File("student.ser");
FileOutputStream fos;

try {
    fos = new FileOutputStream(serializedData);     // Opens file using File object
    ObjectOutputStream oos = new ObjectOutputStream(fos); // Wraps stream
    oos.writeObject(studentArray);                  // Serialize the array of objects
    System.out.println("Data is stored");
    oos.close();
    fos.close();
} catch (IOException e) {
    e.printStackTrace();
}
```
 
##  Deserialization using the File class

```java
//  Deserialize the student array from the file "student.ser"
File serializedData = new File("student.ser"); //  Define the file to read from

FileInputStream fis;   //  Reads raw bytes from the file
ObjectInputStream ois; //  Converts byte stream back into Java objects
Student[] data = null; //  Will store the deserialized Student[] object

try {
    fis = new FileInputStream(serializedData);   //  Open the file for reading
    ois = new ObjectInputStream(fis);            //  Wrap FileInputStream with ObjectInputStream
    data = (Student[]) ois.readObject();         //   Read the object and cast it to Student[]

    // Print deserialized array content
    for (Student s : data) {
        System.out.println(s);
    }

    ois.close();
    fis.close();
} catch (IOException | ClassNotFoundException e) {
    e.printStackTrace(); //  Handles both IO and class-not-found exceptions
}
```
 
### Note :
```
When we serialize an array (e.g., Student[]), the .ser file stores the entire array object.

But when we deserialize, the method readObject() always returns a generic Object.

That’s why we must cast it back to the specific type.

Student[] data = (Student[]) ois.readObject();
```
## Why Casting Is Needed?
```
readObject() returns Object (the most general type in Java).

The JVM doesn’t know at compile time that the stored object is a Student[].

By casting, we’re telling the compiler - I know this is actually a Student[], not just any Object.

```

## Concept Check!

### What is Serialization in Java?
```
Serialization is the process of converting a Java object into a byte stream so that it can be saved to a file or transmitted over a network.

```
### What is Deserialization in Java?
```
Deserialization is the process of converting a byte stream back into a Java object.

```
### Which interface must a class implement to be serializable?
```
java.io.Serializable

```
### Does Serializable interface have any methods?

```
 No, it's a MARKER INTERFACE (doesn’t have any methods)
```
### How do you serialize an object in Java?
```
FileOutputStream fos = new FileOutputStream("data.ser");
ObjectOutputStream oos = new ObjectOutputStream(fos);
oos.writeObject(object);
```
### How do you deserialize an object in Java?
```
FileInputStream fis = new FileInputStream("data.ser");
ObjectInputStream ois = new ObjectInputStream(fis);
MyClass obj = (MyClass) ois.readObject();
```
### What is the role of serialVersionUID?
```
It is a unique identifier used during deserialization to verify that the sender and receiver of a serialized object have loaded classes for that object that are compatible.
private static final long serialVersionUID = 1L;
```
### What happens if serialVersionUID is not declared?
```
JVM generates one at runtime, but changes in class structure (like adding/removing fields) can lead to InvalidClassException during deserialization.

```

### Can a static variable be serialized?
```
No. Static variables belong to the class, not the object, so they are not part of the serialized object.

```

### What if a parent class is not Serializable but the child is?
```
 Parent class fields won’t be serialized. You must handle them manually in the child class

 ```

### What happens if you try to deserialize an object without the class being available?
```
 A ClassNotFoundException will be thrown

 ```

### Can you serialize an object that has a reference to another object?
```
 Yes, if the referred object is also Serializable. Otherwise, a NotSerializableException will occur.

 ```

### You mark a field as transient but want to store it manually. How do you do that?
```
 Use custom writeObject() and readObject() methods to handle that field manually.

 ```

### What will happen if you modify a class after serializing its object, then try to deserialize it?
```
 If serialVersionUID doesn’t match, we’ll get an InvalidClassException

```








