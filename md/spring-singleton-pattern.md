## Singleton

-
## Benefits of Singleton Pattern

- Ensures only one instance of a class (per Classloader)
- Repeated requests produce the same instance
- Ensures shared state
- Reduces overhead to acquire a reference to the class

-
## Drawbacks of Singleton Pattern

- Introduces global state (unless stateless)
- Can be difficult to test

-
-
## Implementation

-
### Pojo Implementation

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
### Better Pojo Implementation

```Java

public enum EnumSingleton {
  INSTANCE
}

```

-
-
### Spring

- Beans are singletons by default (bean scope - no extra annotation needed)
- The same bean can be autowired into many dependencies
- Singletons in Spring are managed per container
- Mutable state in a bean will be reflected across all dependencies (!Caution)
