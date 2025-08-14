
#  Bringing It All Together: Setters, Getters & Constructors → POJO

```
Now that we have learned:

(1) How to make variables private ?
(2) How to create public setter and getter methods ?
(3) How to define constructors to initialize objects ?

It’s time to bring all of these together to create something powerful yet simple — a POJO class!
```

## What is a POJO Class?
```
POJO stands for Plain Old Java Object.

A POJO class is used to map and convert external data formats (like JSON or XML) into Java objects and vice versa. 

It's a simple Java class used mainly to HOLD DATA.

It is a simple Java class that:

	> Only contains PRIVATE VARIABLES  
	> Uses GETTERS and SETTERS to access those variables  
	> May include a CONSTRUCTOR to initialize values  
	> Has NO logic, NO inheritance, NO annotations, NO framework-specific code

Basically, it’s just a CLEAN CONTAINER OF DATA

 ```
## POJO Class Example

```java

To store info about a person - name and age:

public class Person { 
    private String name;  //private instance variables
    private int age;

    // Constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getter for name
    public String getName() {
        return name;
    }

    // Setter for name
    public void setName(String name) {
        this.name = name;
    }

    // Getter for age
    public int getAge() {
        return age;
    }

    // Setter for age
    public void setAge(int age) {
        this.age = age;
    }
}
```
```

That’s a POJO! 

No logic, no extends, no implements, no annotations > just pure data holding.

```

## Summary: POJO 

```

| What does a POJO contain?           | Is it present? |
| ----------------------------------- | -------------- |
| Only private fields                 | Yes          |
| Public getters and setters          | Yes          |
| Business logic (e.g., calculations) | No           |
| Inheritance or annotations          | No           |

```

