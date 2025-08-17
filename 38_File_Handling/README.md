# File Handling in Java

### File handling means to **read from**, **write to**, **create**, **delete** and **manipulate** contents of files programatically.

---

### File handling allows Java programs to perform file I/O (input-output) operations like:

**- Creating files**

**- Checking if a file exists**

**- Deleting files**

**- Reading or writing file content**

---

##  Packages for File Handling

**Java provides two main packages:**

- `java.io` –  I/O operations
- `java.nio` – new I/O operations 


##  File Class in Java

**`File` is a class in `java.io` package.**

**The File class in Java acts as a reference to a file or directory path on the system.**

**It helps us to interact with external files or directories — such as checking if they exist, creating new ones, deleting them, or retrieving their properties (like name, path, size).**

## How to create an object of file class ?

```java
File file = new File("path/to/file.txt");
```
### IMP NOTE

**Path of the file should be SYSTEM INDEPENDENT.**

For windows - path separator is a BACKWARD slash & For Mac, Linux & Unix - path separator is FORWARD slash.

**In Java, always prefer forward slash (/) — Java handles it internally.**

**Always use Relative path (file name) over Absolute path( starts from root).**


---

##  File Handling Program in Java

```java

1 package com.filehandling;

2 import java.io.File;
3 import java.io.IOException;
4 import java.sql.SQLOutput;

5 public class FileRunner {

6     public static void main(String[] args){

          // Creating a file object from file class to check existence

7         File file = new File("/Users/athira/Documents/2025/Java_Project/Javaprograms_SDET/demo.txt");
        
          //  Create new file - Creating a new file object to attempt file creation
8         File newfile = new File("/Users/athira/Documents/2025/Java_Project/Javaprograms_SDET/demo1.txt");

9         try {
10             if(newfile.createNewFile()){
11                 System.out.println("File " + file.getName() + " created successfully");
12             }
13             else{
14                 System.out.println("Cannot create file - file already exists");
15             }
              //  // Handle any IOException during file creation
16         } catch (IOException e) {
17             System.err.println("Cannot create file " + newfile.getName() + ", something went wrong");
18             e.printStackTrace();
19         }

           // exists() -  Check if the file exists
20         if(file.exists()){
21             System.out.println(file.getName() + " file present");
22             System.out.println("Path: " + file.getAbsolutePath());
23         }
24         else {
25             System.out.println("File not present");
26         }

            // delete() - To delete a file
27         if(file.delete()){
28             System.out.println(file.getName() + " successfully deleted");
29         }
30         else{
31             System.out.println("Cannot delete file");
32         }
33     }
34 }


```

---

##  Explanation of File Methods

###  `exists()`
```
The exists() method checks whether the file or directory referred to by the File object exists on the file system (i.e., in the specified path on the computer).  

 Line 20 → To check whether a file exists in the specified path on the computer.

Return : TRUE if the file is present, 
Return : FALSE if the file is not present.  


```
### `getName()`  
``` 
Returns the file name along with its extension.

- Line 11 → To get the name of the newly created file.
- Line 17 → To show the name of the file when creation fails (inside `System.err`).
- Line 21 → To get the name of an existing file.
- Line 28 → To confirm the name of the deleted file.

```

### getAbsolutePath() 

```
Returns the complete path of the file.  

Line 22: Returns the complete path of the file, starting from the root directory.
```
### createNewFile()
```  
Creates a new physical file on the disk if it doesn't already exist.

Returns TRUE : If the file is created successfully.
Returns FALSE : If the file already exists or could not be created.
 
Line 8 → Creates a File object in memory (no file created yet — just a reference to the path)
Line 12 → Actually attempts to create the file in the file system using createNewFile()

 Tip: Always use createNewFile() inside a try-catch block to handle IOException.

```

## delete()
```
Deletes the file from the file system.

Returns TRUE – If the file was deleted successfully  
Returns FALSE – If the file could not be deleted (e.g., file doesn't exist or is in use)

Line 27 → Checks whether the file can be deleted using `file.delete()`
Line 28 → Prints confirmation if deleted  
Line 31 → Prints error if deletion fails

```
---

## Why we handle Exception in File operation?

### When working with files, there’s always a chance of encountering unexpected issues like:

> **File not found**

> **Permission/access restrictions**

> **Corrupted or unreadable files**

> **Disk or I/O failures**

Since these are **checked exceptions (i.e., compile-time exceptions)**, Java forces us to handle them — or else the program won't compile.

 That’s why it's essential to wrap file operations inside a try-catch block.

 ### Try-Catch Block helps to:

**(1) Prevent unwanted program interruptions.**

**(2) Provide user-friendly messages for failures.**

**(3) Handle errors like missing files or restricted paths gracefully.**

```java

try {
    // File operations like createNewFile(), read, write

} catch (IOException e) {

    // Handle errors without crashing the application
}
```
 **Always assume file operations may fail — prepare our program to recover smoothly.**

 ## Methods to Check File Properties


```java

1 package com.filehandling;

2 import java.io.File;
3 import java.io.IOException;

4 public class FileRunner2 {

5     public static void main(String[] args) {

           
6         File myFile = new File("demo\\report.txt");

          // Returns the name of the file with extension
7         System.out.println(myFile.getName());

         // Returns the full absolute path of the file
8         System.out.println(myFile.getAbsolutePath());

         // Checks if this path is a file
9         System.out.println(myFile.isFile());

         //Checks if this path is a directory (expected false here)
10         System.out.println(myFile.isDirectory()); // false

         //Checks if the file has read permission
11         System.out.println("Can read?? " + myFile.canRead());

         //Checks if the file has write permission
12         System.out.println("Can Write?? " + myFile.canWrite());

         //Checks if the file has execute permission
13         System.out.println("Can Execute?? " + myFile.canExecute());

         // Returns the parent directory path of the file
14         System.out.println("Parent Folder: " + myFile.getParent());

         // Returns the size of the file in bytes
15         System.out.println("Size of the file: " + myFile.length()); // bytes

16        // Create a directory
17         File logDirectory = new File("logs");

         // Makes a directory with the name 'logs' if it doesn't exist
18         logDirectory.mkdir();

         // Confirms whether the directory was created
19         System.out.println(logDirectory.isDirectory()); // true

20     }
21 }
```

### Methods Used in This Program

>**getName()** >> Line 7 - Returns the name of the file or directory.

>**getAbsolutePath()** - Line 8 - Returns the full path to the file on the system.

>**isFile()** - Line 9 - Checks if the given path is a file.

>**isDirectory()** - Line 10 - Checks if the given path is a directory.

>**canRead()** - Line 11 - Returns true if the file is readable.

>**canWrite()** - Line 12 - Returns true if the file is writable.

>**canExecute()** - Line 13 - Returns true if the file can be executed.

>**getParent()** - Line 14 -  Returns the name of the parent directory where the file resides.

>**length()** - Line 15 - Returns the size of the file in bytes.

>**Directory Creation** - Line 18 -  mkdir()  - Creates a new directory named "logs" in the current project location.

>**isDirectory()** - Line 19 - Used to verify if the "logs" directory was successfully created.












