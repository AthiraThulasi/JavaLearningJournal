# POJO Class 

## What is a POJO Class?
```
POJO stands for Plain Old Java Object.

A POJO class is used to map and convert external data formats (like JSON or XML) into Java objects and vice versa. 

It's a simple Java class used mainly to HOLD DATA.

It is a simple Java class that:

	> Only contains PRIVATE  VARIABLES.

	> Uses GETTERS and SETTERS to access those variables.

	> Has no logic, no inheritance, no annotations, no framework-specific code

Basically, it’s just a CLEAN CONTAINER OF DATA
 ```
## POJO Class Example

```java

To store info about a person - name and age:

public class Person {
    private String name;
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

## ✅ Summary: POJO 

```

| What does a POJO contain?           | Is it present? |
| ----------------------------------- | -------------- |
| Only private fields                 | Yes          |
| Public getters and setters          | Yes          |
| Business logic (e.g., calculations) | No           |
| Inheritance or annotations          | No           |

```

