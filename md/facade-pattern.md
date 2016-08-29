# Facade

-
### Patterns we will cover

- Creational

  - Singleton
  - Prototype
  - Factory

- Structural

  - Decorator
  - **Facade**

- Behavioral

  - Mediator
  - Observer

-
### What does Facade do?

- Provide a unified interface to a set of interfaces in a subsystem.
- Defines a higher-level interface that makes the subsystem easier to use.

-
### Facade signature

- A single class providing a simplified interface to a class or system with a more complex interface (abstraction)
- The abstracted interface/s are still accessible if needed.
- The facade might not provide access to all aspects of the abstracted interface

  
-
### Example: VehicleFacade

```Java
public class VehicleFacade {

    public void prepareForSale(Vehicle vehicle){
        Registration reg = new Registration(vehicle);
        reg.allocateVehicleNumber();
        reg.allocateLicensePlate();

        Documentation.printBrochure(vehicle);

        washCar(vehicle);
        vehicle.takeForTestDrive();
    }

    public void washCar(Vehicle vehicle) {
        vehicle.cleanInterior();
        vehicle.cleanExteriorBody();
        vehicle.polishWindows();
    }
}
```

-
### Facade Lab

- Add methods to the `Vehicle` interface for the following tasks
  - Rotate tires
  - change oil
  - replace air filter
- Implement these methods in TinyCar
- Provide a method on the `VehicleFacade` to perform all of these tasks, call it `tuneUpVehicle`


-
### Resources

- [Facade on SourceMaking](https://sourcemaking.com/design_patterns/facade)