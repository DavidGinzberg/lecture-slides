# Factory Method

-
### Patterns we will cover

- Creational

  - Singleton
  - Prototype
  - **Factory**

- Structural

  - Decorator
  - Facade

- Behavioral

  - Mediator
  - Observer

-
### What does the Factory Method pattern do?

- Abstracts object creation
- Creates specialized objects based on need
- Delegates object selection/creation to a subclass implementation
- **Note:** Overlaps with Abstract Factory pattern

-
### Example Hierarchy

- AbstractCustomObject **(abstract)**
  - LockingCustomObject
  - MutableCustomObject
  - CustomObjectWithLogging
- BasicFactory **(abstract)**
  - BasicLockingCustomObjectFactory
  - BasicMutableCustomObjectFactory
  - CustomObjectWithLoggingFactory



-
### Resources

- [Factory Pattern on SourceMaking](https://sourcemaking.com/design_patterns/factory_method)
- [Factory Labs](https://gist.github.com/DavidGinzberg/b9cb42c9748122146aca#file-1_factorylab-md)