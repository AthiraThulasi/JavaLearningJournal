# How to Compare Java Objects - equals() & Hashcode() !

```java

class Student {
    private String name;

    public Student(String name) {
        this.name = name;
    }
}
```

```java

public class MainApp {
    public static void main(String[] args) {
        Student s1 = new Student("Anu");
        Student s2 = new Student("Ann");
        Student s3 = new Student("Ann");


        // Comparing two objects using  .equals()

        System.out.println(s1.equals(s2));     // false - content not same
        System.out.println(s2.equals(s3));    // true - content same // value of instance variable same

    }
}
```

## equals()
```
equals() is a method used to compare two objects in java.

2 objects are said to be equal -

       > When they belong to the same class type.

       > values of instance variables should be same

       > 2 objects are going to have same hashcode
```
```
  NOTE: When 2 objects are equal >> they will have same hashcode value!
```

## Internal representation of .equal()

```java

@Override
    public boolean equals(Object obj) { // comparing 2 objects// parameter is of parent class// datatype of reference is obj
        // Step 1: Check if both references point to the same object

        if (this == obj) { // this talks about the current instance// comparing s1.equals(s1)
            return true; // then return true!
        }

        // Step 2: Check if the passed object is null 
        if (obj == null )// passing null - couldn't compare which doesn't exist ie obj reference is NULL
          return false; //   return false!

        // step 3: ocheck if the passed obj is of the same class
        if(getClass() != obj.getClass()) { // getClass() gives the class type // if 2 classes are not equal - return false
            return false; // return false
        }


        // Then do type casting - after that value of each instance variable of one object is compared with other one.
 ```

 ##   Where do we use .equals() in Automation Framework?

```
 .equals() is commonly used in assertions to compare expected and actual results

```
 ```java

Student expectedData = new Student("Ann", 20, 18, 75, 82, 69, "B");

System.out.println(expectedData);

Student actualData = new Student("Ann", 20, 18, 75, 82, 69, "B");

System.out.println(expectedData.equals(actualData));  // true → if equals() is properly overridden

```