## toString() Method in Java

##  What is toString()?

```
toString() is a method that converts an object into a string representation - It returns an one line description of the object's instance variables.

toString() is defined in the Object class, which is the parent of all Java classes.

```
## ToString Method - Code - How the o/p looks like?

```java
@Override
    public String toString() {
        return "Student [name=" + name + ", age=" + age + ", rollNumber=" + rollNumber + "]";
    }
```
```
OUTPUT - Student [name=Neil, age=10, rollNumber=30]
```
## Without toString() - What is going to be the o/p?

```
s1 is the reference variable which store hashcode of the object

If we print s1 without toString() - system.out.print(s1) - s1 returns hashcode >> com.student.management.system.oop.Student@512ddf17

```
##  Why use toString()?

```
Helps during debugging or logging, so we can see the exact values of variables.

Without overriding, calling System.out.println(obj) prints the hashcode by default.

Overriding allows printing meaningful data about the object.

```

## How toString() looks internally (inside Object class) ?
```java
public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
}
```
## What happens step by step ?
```
getClass().getName() >> Gets the runtime class of the object (e.g., Person, Student, Car).

Example → "Person"

hashCode() >> Returns a unique number (int) that represents the object in memory.

Example → 2052879

Integer.toHexString(hashCode()) >> Converts that number into hexadecimal format.

Example → "7a81197d"

Then it combines them like: Person@7a81197d


Output (default):

Person@7a81197d
```
## Summary

```
toString() exists in Object class, so all Java objects have it.

Default → className@hashCode.

Overriding → meaningful object data.

Best practice → always override toString() for user-defined classes.
```