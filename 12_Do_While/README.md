#  Do-While Loop
```
The do-while loop excecutes once whether the condition is True or False.
```
 ## Syntax

```java

do {
    
    // Code to execute

} while (condition);

```
##  Key Points
```
The loop executes the block first, then checks the condition.

So, even if the condition is false the first time, the block still executes once.

Often used when you want to take input from the user at least once.
```

## Example

```java

int i = 1;

do {
    System.out.println("i = " + i);
    
    i++;
} 
while (i <= 5);
```

 Output:

```
i = 1

i = 2

i = 3

i = 4

i = 5
```

##  Difference Between while and do-while
```
| Feature              | WHILE loop                            | DO-WHILE loop                            |
| -------------------- | ------------------------------------- | ---------------------------------------- |
| Condition Check      | Before executing the block            | After executing the block                |
| Guaranteed Execution | Not guaranteed                        | Always executes AT LEAST ONCE.           |
| Use Case             | When we want to check condition first | When we want at least one-time execution |
```


## When While Condition is Initially False  !

``` java

int i = 10;

while (i < 5) {

    System.out.println(i);  //  ✅ This will print once
    
    i++;
}


```

## Excecution:
```
The do block runs once no matter what.

i starts at 10.

After printing, i++ makes it 11.

Then while(i < 5) is false → so it exits.
```