# Dependency Injection & Repository Design Pattern

## Dependency injection in ASP.NET Core

### Overview of dependency injection
A *dependency* is an object that another object depends on. Examine the following MyDependency class with a WriteMessage method that other classes depend on:

```C#
public class MyDependency
{
    public void WriteMessage(string message)
    {
        Console.WriteLine($"MyDependency.WriteMessage called. Message: {message}");
    }
} 
```
> The class creates and directly depends on the MyDependency class. Code dependencies, such as in the previous example, are problematic and should be avoided for the following reasons:

- To replace MyDependency with a different implementation, the IndexModel class must be modified.
- If MyDependency has dependencies, they must also be configured by the IndexModel class. In a large project with multiple classes depending on MyDependency, the configuration code becomes scattered across the app.
- This implementation is difficult to unit test.
Dependency injection addresses these problems through:

- The use of an interface or base class to abstract the dependency implementation.
- Registration of the dependency in a service container. ASP.NET Core provides a built-in service container, IServiceProvider. Services are typically registered in the app's Program.cs file.
- Injection of the service into the constructor of the class where it's used. The framework takes on the responsibility of creating an instance of the dependency and disposing of it when it's no longer needed.


### Entity Framework contexts
By default, Entity Framework contexts are added to the service container using the scoped lifetime because web app database operations are normally scoped to the client request. To use a different lifetime, specify the lifetime by using an AddDbContext overload. Services of a given lifetime shouldn't use a database context with a lifetime that's shorter than the service's lifetime.

### Lifetime and registration options
To demonstrate the difference between service lifetimes and their registration options, consider the following interfaces that represent a task as an operation with an identifier, OperationId. Depending on how the lifetime of an operation's service is configured for the following interfaces, the container provides either the same or different instances of the service when requested by a class:


#### Scope validation
See Constructor injection behavior in Dependency injection in .NET

#### Request Services
Services and their dependencies within an ASP.NET Core request are exposed through HttpContext.RequestServices.

The framework creates a scope per request, and RequestServices exposes the scoped service provider. All scoped services are valid for as long as the request is active.


### The Repository pattern
Repositories are classes or components that encapsulate the logic required to access data sources. They centralize common data access functionality, providing better maintainability and decoupling the infrastructure or technology used to access databases from the domain model layer. If you use an Object-Relational Mapper (ORM) like Entity Framework, the code that must be implemented is simplified, thanks to LINQ and strong typing. This lets you focus on the data persistence logic rather than on data access plumbing.

The Repository pattern is a well-documented way of working with a data source. In the book Patterns of Enterprise Application Architecture, Martin Fowler describes a repository as follows:

> A repository performs the tasks of an intermediary between the domain model layers and data mapping, acting in a similar way to a set of domain objects in memory. Client objects declaratively build queries and send them to the repositories for answers. Conceptually, a repository encapsulates a set of objects stored in the database and operations that can be performed on them, providing a way that is closer to the persistence layer. Repositories, also, support the purpose of separating, clearly and in one direction, the dependency between the work domain and the data allocation or mapping.

### Repositories shouldn't be mandatory
Custom repositories are useful for the reasons cited earlier, and that is the approach for the ordering microservice in eShopOnContainers. However, it isn't an essential pattern to implement in a DDD design or even in general .NET development.

For instance, Jimmy Bogard, when providing direct feedback for this guide, said the following:

> This'll probably be my biggest feedback. I'm really not a fan of repositories, mainly because they hide the important details of the underlying persistence mechanism. It's why I go for MediatR for commands, too. I can use the full power of the persistence layer, and push all that domain behavior into my aggregate roots. I don't usually want to mock my repositories – I still need to have that integration test with the real thing. Going CQRS meant that we didn't really have a need for repositories any more.

Repositories might be useful, but they are not critical for your DDD design, in the way that the Aggregate pattern and rich domain model are. Therefore, use the Repository pattern or not, as you see fit. Anyway, you'll be using the repository pattern whenever you use EF Core although, in this case, the repository covers the whole microservice or bounded context.

## Repository Design Pattern

## Abstraction
The idea with this pattern is to have a generic abstract way for the app to work with the data layer without being bother with if the implementation is towards a local database or towards an online API.

## Compromise
I chose to compromise and go half way between the repository and my old DAOs. I have my interface with all the CRUD methods. I also add one more method readById(K id). This interface will cover most of my basic use cases.

## Is Your Code SOLID?
The SOLID Principals of software development is the brain child or Robert “Uncle Bob” Martin. In the early 2000 he described five principals that software developers could use to guide them in creating software that was well designed, high quality and easier to maintain than what was being produced at the time. These five ideas are simple, promote good practices in software design and development, and go a long way to help us in our practice of TDD.
 
## Single Responsibility Principle
The Single Responsibility Principal (SRP) is the idea that every method or class in your application should have exactly one reason to change. You can logically extend that to say that every class or method in your application should have exactly one (a single) job or responsibility. The short way of saying this is that each method and each class should be responsible for one, and only one task. For example let’s consider a class the functions as a shopping cart for an e-commerce website. As a virtual shopping cart it would be logical for the class to hold a collection of items that a user has added to the cart to purchase and perhaps a way to communicate with a service for the user to checkout. To extend this example let’s say that the site has a loyalty rewards program that rewards points to customers based on purchases. Any functionality to award, track or manage points would not be appropriate to add to the shopping cart. That functionality should reside in a separate service. The shopping cart should not be responsible for, or actually have any concept of the rewards program. The shopping cart has one job; store a list of items the user wants to purchase. Therefore the shopping cart only has one reason to change; the methodology of storing the list of items a customer has selected has changed. Changes to the rewards program should have no effect on the shopping cart, and thus not require that class to change if a change is made to the rewards program. By ensuring that we are writing methods and classes that have only one responsibility, we make these methods easier to test. Methods that try to do too much tend to require tests with more complex and elaborate “Arrange” sections that make the test longer and more difficult to understand and maintain. We can also extend the SRP to our tests and how we write them. Ideally each test we write should test exactly one thing. This will result in more tests, but those tests will be more granular. There are many benefits to this approach. To start with, the tests themselves will be simpler and easier to understand. Another benefit of this approach is that when a test fails you’ll have a pretty specific piece of information in terms of where to look for the issue. If a test does one thing and it fails you should only have one place to look. If a test tests two or more things you’ve increased the amount of time you have to spend diagnosing the problem. Conforming to SRP when writing your tests will keep your tests simple and help you know where to look when the test fails.

### Summary
If you weren’t familiar with the SOLID Principles before this post I hope it has piqued your interest in learning more about them. I’ve only scratched the surface here and there is far, far more to learn about each of the principles. For another take on the SOLID Principles you should check out this post. If you already were familiar with SOLID I hope this review has given you a renewed perspective on the principles and how they affect our practice of TDD. In the next post we’ll dive back into some code by discussing Dependency Injection.

#### Liskov Substitution Principle
Subclasses should be substitutable for their base classes
If you are at a restaurant, and order a salad, the way you eat it (and when it gets served) doesn’t vary just because this time you ordered a Caesar Salad and last time you ordered a house salad.  In the same way, derived classed must be able to be used by the client code without any adverse effects on the function of the client code.

#### Interface Segregation Principle
Many client specific interfaces are better than one general purpose interface
Just like in Visual Studio where you can pick you development profile (C#, VB.NET), your classes should tailor their interfaces to the clients that consume them.  Fine grained interfaces reduce the analysis paralysis that can occur when there are too many choices.

#### Dependency Inversion Principle
Depend upon Abstractions. Do not depend on concretions.
For those of you who drive, do you have to build your car every time you go to work?  Can you drive more than one different car, or can you only drive one physical instance of a car?  Have you ever borrowed a car (or rented one?)

Think of this in your software.  When your code instantiates a concrete class and then uses that instance, it completely depends on that particular implementation, and will never be able to use another one until you change how the code is written.  However, if you code to an Interface, you can borrow a car, rent a car, or buy a new one!
