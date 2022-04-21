# Interfaces

An interface contains definitions for a group of related functionalities that a non-abstract class or a struct must implement. An interface may define static methods, which must have an implementation. Beginning with C# 8.0, an interface may define a default implementation for members. An interface may not declare instance data such as fields, auto-implemented properties, or property-like events.

By using interfaces, you can, for example, include behavior from multiple sources in a class. That capability is important in C# because the language doesn't support multiple inheritance of classes. In addition, you must use an interface if you want to simulate inheritance for structs, because they can't actually inherit from another struct or class.


### An interface has the following properties:

- In C# versions earlier than 8.0, an interface is like an abstract base class with only abstract members. A class or struct that implements the interface must implement all its members.
- Beginning with C# 8.0, an interface may define default implementations for some or all of its members. A class or struct that implements the interface doesn't have to implement members that have default implementations. For more information, see default interface methods.
- An interface can't be instantiated directly. Its members are implemented by any class or struct that implements the interface.
- A class or struct can implement multiple interfaces. A class can inherit a base class and also implement one or more interfaces.

### Interfaces are contracts
Interfaces allow us to specify that a particular class meets certain expectations that other classes can rely on.

If we have a class that implements an interface, we can be sure that it will support all the methods that are defined in that interface.

At first glance interfaces seem to be similar to concrete inheritance, but there is a key difference.

Concrete inheritance says Car is an Automobile, while an interface says Car implements the Drivable interface.

When a class implements an interface, it does not mean that class IS that interface.  For this reason interfaces that completely describe the functionality of a class are usually wrong.

### interface (C# Reference)

- An interface defines a contract. Any class or struct that implements that contract must provide an implementation of the members defined in the interface. Beginning with C# 8.0, an interface may define a default implementation for members. It may also define static members in order to provide a single implementation for common functionality.