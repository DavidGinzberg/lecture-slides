#Generics

-
-
##Terms

- Parameterized Type
- Generic Type
- Type Inference


-
-
## Examples of generic Types

- List (ArrayList, LinkedList, etc)
- Map (HashMap, TreeMap, etc)


-
-
## A container to hold anything

```Java
class NonGenericBox{

  private Object contents;

  public void put(Object thing){ contents = thing; }

  public Object get(){ return contents; }
}
```

-
### Using the non-generic box

```Java
public static void main(String[] args){
  NonGenericBox box = new NonGenericBox();
  String helloString = "Hello";
  box.put(helloString);
  // ...Several lines later
  String s = (String)box.get();
  // s = box.get(); //Compile error!
}
```

-
## Defining A Generic type

```Java
class OneItemBox<T>{

  private T contents;

  public void put(T thing){ contents = thing; }

  public T get(){ return contents; }
}
```

-
### Generics can have multiple type parameters

```Java
class TwoTuple<A,B>{
  public final A first;
  public final B Second;
  public TwoTuple(A a, B b){ first = a; second = b; }
```

-
### Extend generics with or without specific types

```Java
class TwoDPoint extends TwoTuple<Integer, Integer>{}
```

```Java
class ThreeTuple<A,B,C> extends TwoTuple<A, B>{
  public final C third;
  public ThreeTuple(A a, B b, C c){super(a, b); third = c; }
}
```

-
### Diamond operator (`<>`)

- Introduced in Java 7
- Used for type inference in generic constructors
- Helps make code less verbose

Before Java 7:  
`List<Foo> sList = new ArrayList<Foo>()`  
After Java 7:  
`List<Foo> sList = new ArrayList<>()`

-
### Primitive types cannot be type parameters

Example:

```Java
// This will not compile!!!!
class PrimitiveGeneric<T>{}
public class Main{
  public static void main(String[] args){
    PrimitiveGeneric<int> pg = new PrimitiveGeneric<>();
  }
}
```

-
### The solution? Wrapper classes!

```Java
class PrimitiveGeneric<T>{}
public class Main{
  public static void main(String[] args){
    PrimitiveGeneric<Integer> pg = new PrimitiveGeneric<>();
  }
}
```

-
### Primitives and autoboxing

```Java
public static void main(String[] args){
  int x, y;
  x = 5;
  OneItemBox<Integer> box = new OneItemBox<>();
  box.put(x);
  y = box.get();
  System.out.println(y);
```

-
-
#### If A extends B, does List&lt;A&gt; extend List&lt;B&gt;?

**NO!**

[Stack Overflow](http://stackoverflow.com/a/2745301/3444548) said it best:

```Java
List<Dog> dogs = new List<Dog>();
List<Animal> animals = dogs; // Awooga awooga
animals.add(new Cat());
Dog dog = dogs.get(0); // This should be safe, right?
```

"Suddenly you have a *very* confused cat."


-
-
# Next time

- Bounding
- Erasures
- Self-bounding
