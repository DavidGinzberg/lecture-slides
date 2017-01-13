# Initialization and Cleanup

-
### Important Terms

- Constructor: A special function that creates an instance of a class
- Overloading: Creating multiple methods with the same name but different argument lists.
- Declaration: Specifying the name and type of a variable 
- Initialization: The first value assignment a variable or reference receives

-
### Examples: Constructor

```
class Foo{

// Constructor for Foo
  public Foo(){ ... }
}
```

-
### Examples: Overloading

```
public static int sum(int x, int y){ return x + y;}

public static int sum(int[] nums){
  int total = 0;
  for(int i : nums){ total += i; }
  return total;
}
```

-
### Examples: Declaration

```
int x;
String s;
Document independence;
```

-
### Examples: Initialization

```
int pi = 3; // ಠ_ಠ
Repo myRepo = new Repo();
double realPi = pi + 0.14159265358979324;
```


-
-
# Constructors

-
## Constructors

- Constructors are special methods that perform set-up tasks for an instance of a class.  
- Constructors are only called once in the life cycle of an instance.  
- Constructors are named after the object class they belong to.

-
### Constructors are methods

- Constructors have parameters and access just like any other method
- Constructors have access to instance variables of an object
- Constructors have no return value or type

-
### Constructors are special

Constructors have no return value (different from void return).  
Constructors are called without an instance (but aren't static).  
Cannot be called as member methods of an initialized instance.

-
#### No return value

```
public Kung(){...}
public Kung foo(){...}
public void bar(){...}
```

-
#### Called without instance

Constructors are not static, but do not require an instance to be called.

```
String str = new String("");
//     NOT:  str.String("");
```

-
#### Cannot be called as member methods

```
Manchu foo = new Manchu();
foo.Manchu();
/***
* Foo.java:20: error: cannot find symbol
* foo.Manchu();
*    ^
*   symbol:   method Manchu()
*   location: variable foo of type Manchu
***/
```

-
-
## Overloading Methods


-
### Overloading vs Overriding

**Overloading** - Creating alternate versions of the same method  
**Overriding** - replacing the existing method with a new one


-
### Distinguishing Overloaded Methods

Overloaded methods have distinct argument lists (number and type).  
Three overloaded methods:

```
public int foo(int x) {return x;}
public boolean foo(boolean y) {return !y;}
public boolean foo(char c, int x) {return c == 's' || x > 5; }
```


-
### Overloading return values

Not allowed in Java. Ambiguous example:

```
public int foo(){ System.out.println("int"); return 0; }
public void foo(){ System.out.println("void"); return; }
public static void bar(){ foo(); } //which foo?
```

-
-
### Default Constructors

-
### Automatically created

If no constructor is defined, java automatically creates a no-arg constructor (aka default constructor)

```
class Foo{}
public class Bar{
  private Foo myFoo = new Foo(); //default constructor
}
```

-
### Only available when no others exist

Default constructors are not created if other constructors have been defined.

```
class Baz{ 
  public Baz(int x) {} 
}
public class Main {
  public static void main(String []args){
    Baz inga = new Baz(); // Error!!!
  }
}
```

-
-
### Keyword: `this`

- Refers to the object that "owns" the current method  
- Can't be used in a static context
- Used to call overloaded constructors (from other constructors, must be first line)

```
public Foo(int x){
    this();
    this.x = x;
}
```

-
-
### Member Initialization

All class members are initialized to default values  
0, `false`, or [`'U+0000'`](https://unicode-table.com/en/#0000) for primitives.  
`null` for object references.  
Static members are initialized the first time that class is referenced.  
Local variables (inside methods) are not auto-initialized.

-
-
### Constructor Initialization

All instance and static fields initialized before constructor runs.  
Use constructors to set custom initial values.

-
-
### Array Initialization

Arrays are objects and will receive a default value of `null`  
Two ways to initialize:

```
int[] arr1 = {1, 2, 3} // Array Literal
```
OR

```
int[] arr2 = new int[3]
arr2[0] = 3;
arr2[1] = 2;
arr2[2] = 1;
```
-
### Array Access

Access array elements with `[index]` where index is a number.  
Array indexes start at 0. Arrays have a `length` field built in.  
Arrays are references.

```
int[] arr1 = {1, 2, 3};
int[] arr2 = arr1;
arr2[0] = 5;
System.out.println(arr1[0]);
// output: 5
```


-
-
### Enumerated types

Enumerated types are a way to create a list of possible values.  
Created using the `enum` keyword.

```
public enum CompassDirection {NORTH, SOUTH, EAST, WEST }
...
CompassDirection heading = CompassDirection.SOUTH;
```


-
-
# Cleanup

-
# Destructors?

Some languages have a method type called a destructor.  
Destructors free up memory when it is no longer needed.  
Explicit memory management is complex and prone to bugs.

-
### No Java Destructors

Java uses a Garbage Collector.  
Out of scope objects are garbage collected and their memory freed automatically.  
Garbage Collector is automatic and thus not predictable.

-
-
# Lab

Implement the following features for the calculator project (starred on the lab):

All calculators should have the following features:  
Each operation should automatically update the display

- A state, representing the value currently displayed on the calculator (default 0)
- Get the current number on the display
- Clear the display
- Change the number on the display
- Add, subtract, multiply, and divide the value on the display by a given number
- Calculate the square (x<sup>2</sup>) and square root (√x) of the number on the display
- Calculate the inverse of the number on the display (1/x)
- Update the display to `Err` if an error occurs (eg: Division by zero)
- Errors must be cleared before any other operation can take place
- Memory - Store up to one numeric value in memory for recall later (default to 0) *
  - (`M+` key) Add the currently displayed value to the value in memory (store in memory and update display) *
  - (`MC` key) Reset memory *
  - (`MRC` key) Recall the current value from memory to the display *


