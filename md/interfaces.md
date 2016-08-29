#Interfaces



-
-
## Syntax

```Java
interface MyInterface{
  void aMethod();
  int anotherMethod(String s);
}

class MyClass implements MyInterface{
  ...
}
```


-
## Uses for Interfaces

- Define how to interact with a particular class
- Apply similar properties to dissimilar classes
- Mark classes as belonging to a certain category
- Provide a form of multiple inheritance


-
### Interfaces are polymorphic

Objects of classes that implement an interface can be treated as an instance of that interface

```Java
interface BluetoothDevice{}

class MagicMouse implements BluetoothDevice{}

public class App{ public static void main(String[] args){
    connectBluetoothDevice(new MagicMouse());
  }
  
  public void connectBluetoothDevice(BluetoothDevice btd){...}
}
```

-
### Define how to interact with a class

Methods have no body and are implicitly public

```Java
interface PointingDevice{

  void leftClick();
  void rightClick();
  void scrollUp();
  void scrollDown();

```

-
### Exercise: Similar properties, dissimilar objects

- Name several devices that can be recharged
- Define class hierarchies for these items
- Use an interface to state which methods all rechargeable devices need
- Create a UniversalCharger that can `recharge()` any rechargeable device


-
### Simulate multiple inheritance

```Java
interface Keyboard{}

interface BluetoothDevice{}

class BluetoothKeyboard implements Keyboard, BluetoothDevice{}
```


-
-
### Implements vs Extends

- Interfaces can extend other interfaces
- concrete and abstract classes implement interfaces

```Java
interface PeripheralDevice{}

interface BluetoothDevice extends PeripheralDevice{}

class MagicMouse implements BluetoothDevice{}
```

-
### Interfaces vs abstract classes

- Interfaces can be multiply implemented
- Abstract classes have state and private fields and methods available
- Concrete classes extend abstract classes; they implement interfaces (syntax difference)
- Abstract classes can implement interfaces; the reverse is not allowed

-
### Fields

- Fields in interfaces are `static final`
- This provides a way to set constants for classes that implement an interface
- Not often used any more (enums provide this behavior and more)

-
### Default methods

- introduced in Java 8
- Allows default implementation of methods in interfaces
- No references to object state allowed; must only use other methods.
- Good for defining complex procedures by delegating to other methods.
