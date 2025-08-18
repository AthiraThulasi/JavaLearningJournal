# Arrays

### What is an Array?
```
An array is a LINEAR DATA STRUCTURE in Java that stores multiple values of the same data type in contiguous memory locations. 

Arrays allow you to access data efficiently using an index.

Note : Data Structure is a way of organizing and storing data in memory so that it can be used efficiently.
```
## Key Characteristics
```
| Concept             | Explanation                                                                 
|---------------------|------------------------------------------------------------------------------|
| DATA TYPE.          | Arrays store elements of the same type — like `int[]`, `String[]`, etc.     |
| FIXED SIZE.         | Size is set at the time of creation and cannot be changed.                 |
| OBJECTS.            | Arrays are non-primitive — they are objects in Java.                       |
| MEMORY.             | Stored in heap memory even when declared inside a method.                  |
| INDEXING.           | Arrays are zero-indexed: first element is at index `0`, last at `length-1`.|
| TYPE SAFETY         | Java arrays are type-safe — only correct data types can be stored.         |
| ARRAY TRAVERSING.   | Traversing means looping from index `0` to `length - 1` to access elements.|
| COMMOM ERROR.       | Accessing an invalid index causes `ArrayIndexOutOfBoundsException`.        |
```

## How to Define an Array ?

``` java  

Single Dimensional Array

int[] arr = new int[5];     // Array definition with size

int[] marks = {90, 80, 70, 60}; // Array definition without size - array literal syntax (automatically set based on the number of values)
                        

```
```

1. int [ ] → Declares an array that will store integers.

2. arr → Is the reference variable, stored in the stack.

3. new int[5] → Allocates 5 contiguous memory locations in the heap.

4. Each element is automatically initialized to 0 (default value for int)

```
## How Array is stored in memory?


```
Stack Memory                Heap Memory

arr ────────────────►      [ 0 ][ 0 ][ 0 ][ 0 ][ 0 ]
                     Index: 0     1     2   3    4

```

## How to Add Elements in an Array ?
```
We add elements to an array by assigning values to specific indexes.
```
``` java

int[] arr = new int[5];  // Creates an array of size 5

arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
arr[3] = 40;
arr[4] = 50;

```

## How Array Looks in Memory After Adding Elements?

```
int[] arr = new int[5];

Index:      [ 0 ]   [ 1 ]   [ 2 ]   [ 3 ]   [ 4 ]
Value:      [10 ]   [20 ]   [30 ]   [40 ]   [50 ]

```
## How to access elements in an array?
```
Array elements are accessed using index numbers. Indexing starts from 0 and goes up to length - 1.
```
``` java

int[] marks = {90, 80, 70, 60};

System.out.println(marks[0]); // Accessing 0th index - Output: 90

System.out.println(marks[3]); // Accessing 3rd index - Output: 60
```

## What Happens If You Access an Invalid Index?
```
If we try to access an index outside the valid range, Java throws a runtime exception called - ArrayIndexOutOfBoundsException
```
```java

int[] marks = {90, 80, 70, 60};

System.out.println(marks[4]); // ❌ This will throw ArrayIndexOutOfBoundsException
```

### Why ArrayIndexOutOfBoundsException occurs?
```
Because marks[4] is invalid — the array has only 4 elements (index 0 to 3).

```
## length property in Arrays
```
In Java, every array has a built-in length property that tells us how many elements the array can hold.
```
``` java

int[] arr = new int[5];

System.out.println(arr.length);  // Output: 5

```

## Key Points
```
length is a property, not a method, no parentheses ().

It returns the total number of elements the array can store.

Indexing goes from 0 to length - 1.
```

``` java

int[] arr = new int[5];

Index:     [ 0 ]  [ 1 ]  [ 2 ]  [ 3 ]  [ 4 ]
               ↑                            ↑
         First Index                  Last Index = arr.length - 1

arr.length = 5

```

## Array Traversing Using For Loop
```
 Array traversing means moving through an array from the first index (0) to the last index (length - 1) to access each element.
```
```java 

int[] nums = {10, 20, 30, 40};

for(int i = 0; i < nums.length; i++) {       // Best Practise :  Use i < nums.length for dynamic range  instead of hardcoding i < 3


    System.out.println(nums[i]);  // helps in printing, searching, sorting, or performing operations on array elements.

}

```

### Notes:
```
i < nums.length is preferred over hardcoding (i < 4).

If you use i <=, make sure to write i <= nums.length - 1 to avoid ArrayIndexOutOfBoundsException.

```

##  Array Traversing Using Enhanced For Loop
```
The enhanced for loop is used when: We want to visit every element in the array.

We don’t need index here!
```
```java

int[] marks = {90, 80, 70, 60};

for (int mark : marks) {.     // mark is the loop variable that temporarily holds each element from the marks array during each loop cycle.
    System.out.println(mark);
}

```
## Points:
```
What is mark here? mark is a temporary variable (also called a loop variable).

It represents the current element of the marks array during each iteration.

Its type (int) must match the type of the array elements.

```
# 2D Arrays
```
A 2D array in Java is like a table with rows and columns.
```
```java

int[][] arr = new int[2][2];  // 2 rows, 2 columns

```
```
1. int[][]	Declares a 2D array that will store integers in rows and columns format.

2. arr	is the reference variable, stored in the stack, pointing to the 2D array in heap.

3. new int[2][3] - creates a 2D array with 2 rows and 3 columns (total 6 elements) in the heap memory.

4. Default Values - All elements are automatically initialized to 0 (default value for int).
```


```
     ↓ columns
     0   1
   ┌─────────
0 │  0   0
1 │  0   0
↑
rows
```


## Assigning Values to a 2D Array

```java

arr[0][0] = 10;
arr[0][1] = 20;
arr[1][0] = 30;
arr[1][1] = 40;
```

 **Now the array looks like:**
```
     0    1
   ┌──────────
0 │ 10   20
1 │ 30   40
```

## Traversing a 2D Array


```java

for (int rowIndex = 0; rowIndex < arr.length; rowIndex++) {        // arr.length ➤ gives number of rows

     for (int colIndex = 0; colIndex < arr[0].length; colIndex++) {    // arr[0].length ➤ gives number of columns (for that row)

        System.out.print(arr[rowIndex][colIndex] + " ");
    }
    System.out.println();
}
```

## Disadvantages of Array!

### 1. Fixed Size
```
Once declared, the size of an array cannot be changed.

You either run out of space or waste memory if the size is not planned correctly.
```
### 2. No Inbuilt Methods
```
Java arrays do not offer built-in methods for common operations like:

Searching, Sorting, Inserting or deleting elements

All of these must be done manually or with helper methods.
```
### 3. Insertion and Deletion are Hard
```
Inserting a new element in the middle or deleting one means:

Shifting elements manually or Updating indexes carefully

There’s no automatic shifting or resizing.
```
### 4. Must Track Indexes Manually
```
You need to remember and manage indexes to avoid ArrayIndexOutOfBoundsException.

There's no method like get(index) or remove(index) as in Lists.
```
### 5. Stores Only Homogeneous Data
```
Arrays are type-specific:

An int[] can store only integers.

A String[] can store only strings.

We can't mix types like in ArrayList<Object>.
```
