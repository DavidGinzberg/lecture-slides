# Singleton

There can be only one

-
### Patterns we will cover

- Creational

  - **Singleton**
  - Prototype
  - Factory

- Structural

  - Decorator
  - Facade

- Behavioral

  - Mediator
  - Observer

-
## Singleton Design Pattern

- Restricts object creation to a single instance of a class
- Additional requests for an object return the same instance

-
### Example

```java
public class SimpleSingleton {

    static SimpleSingleton instance;

    private SimpleSingleton(){}

    public static SimpleSingleton getInstance(){
        if (instance == null){
            instance = new SimpleSingleton();
        }
        return instance;
    }
}
```

-
### Code Walkthrough examples

- SimpleSingleton
- SingletonWithInstanceCounter
- ConfigOptions
- EventLogger

-
### When to use singletons (sparingly)

- When an object is expensive and duplicates aren't necessary
- when you truly need one and only one object
- when you need to preserve state 

-
### More Information

- [Seven ways to implement singletons](http://www.softwaregeek.net/2013/01/singleton-design-pattern-in-java.html)
- [Singleton Pattern on SourceMaking](https://sourcemaking.com/design_patterns/singleton)