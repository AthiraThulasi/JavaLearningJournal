## toString() Method in Java

## 1. What is toString()?

```

toString() is a method that converts an object into a string representation.

toString() is defined in the Object class, which is the parent of all Java classes.

toString() Returns a String value (one-line description of object’s instance variables).

```

2. Why use toString()?

Helps during debugging or logging, so you can see the exact values of variables.

Without overriding, calling System.out.println(obj) prints the hashcode by default.

Overriding allows printing meaningful data about the object.

3. Behavior Without toString() Override
Student s1 = new Student("Uday", 17, 25, 80, 70, 71, "B");

System.out.println(s1);           
// Prints: Student@2f92e0f4 (className@hashCode)

System.out.println(s1.getName()); 
// Prints: Uday

4. Behavior With toString() Override
@Override
public String toString() {
    return "Student [name=" + name + ", age=" + age + 
           ", rollNumber=" + rollNumber + ", marks=" + marks + "]";
}


Output:

Student [name=Uday, age=17, rollNumber=33, marks=80...]

5. Default Implementation of toString()

Defined inside Object class:

public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
}


getClass().getName() → class name of object

hashCode() → unique identifier of object in memory (converted to hex)

6. Example
class Person {}

public class Main {
    public static void main(String[] args) {
        Person p = new Person();
        System.out.println(p);
    }
}


Output (default):

Person@7a81197d

7. Key Points (Summary)

toString() exists in Object class, so all Java objects have it.

Default → className@hashCode.

Overriding → meaningful object data.

Best practice → always override toString() for user-defined classes.