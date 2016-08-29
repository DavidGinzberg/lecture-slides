# Decorator

-
### Patterns we will cover

- Creational

  - Singleton
  - Prototype
  - Factory

- Structural

  - **Decorator**
  - Facade

- Behavioral

  - Mediator
  - Observer


-
### What does Decorator pattern do?

- Attach additional responsibilities to an object dynamically.
- Provide a flexible alternative to subclassing for extending functionality.


-
### Decorator signature in Java

- Forked class hierarchy
  - A branch for base classes
  - A branch for add-ons/decorators
- Decorators have a reference to the decorated object (using shared parent class type) 
- Decorators pass methods through to the decorated object (with or without modification)

-
### Example Without Decorators

- Create a Car class with a getPrice method.
- Create a class that represents a car with a nav system.
- Create another class for a car with a luxury interior.
- How would you create a car with both a nav system and luxury interior?

-
### Vehicle Hierarchy Example

- Vehicle (interface)
  - AbstractVehicle (abstract)
    - Car (abstract)
      - Sedan
      - SportsUtilityVehicle
    - **AbstractVehicleOption (abstract)**
      - **VehicleLuxuryInteriorOption**
      - **VehicleNavPackageOption** 

-
### Decorator Pattern Lab

Using the example code as a base, add two more kinds of vehicles under a `Truck` abstract class (`Truck` should be a sibling to `Car`) and two more decorators.  
Demonstrate several different configurations of the new and old vehicles and decorators including applying multiple decorators to the same vehicle.

-
### More Resources

- [Decorator Pattern on SourceMaking](https://sourcemaking.com/design_patterns/decorator)
- [Decorator Pattern on C2](http://c2.com/cgi/wiki?DecoratorPattern)
