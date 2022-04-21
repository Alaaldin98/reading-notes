## Classes & Objects
are the basic concepts of Object-Oriented Programming which revolve around the real-life entities. A class is a user-defined blueprint or prototype from which objects are created. Basically, a class combines the fields and methods(member function which defines actions) into a single unit. In C#, classes support polymorphism, inheritance and also provide the concept of derived classes and base classes.

### Classes & Memory Management
Links to an external site.A type that is defined as a class is a reference type. At run time, when you declare a variable of a reference type, the variable contains the value null until you explicitly create an instance of the class by using the new operator, or assign it an object of a compatible type that may have been created elsewhere
#### Declaring Classes
Links to an external site.Classes are declared by using the class keyword followed by a unique identifier

#### Creating objects
Links to an external site.Objects can be created by using the new keyword followed by the name of the class that the object will be based on

#### Class inheritance
Links to an external site.When you create a class, you can inherit from any other class that is not defined as sealed, and other classes can inherit from your class and override class virtual methods. Furthermore, you can implement one or more interfaces.



### Constructors
Whenever a class or struct is created, its constructor is called. A class or struct may have multiple constructors that take different arguments. Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.



#### Properties
- A property is a member that provides a flexible mechanism to read, write or compute the value as a private fields
- Properties enable a class to expose a public away of getting and setting values while hiding the implementation or verification code
- A value keyword is used to define the value being assigned by the set or init accessor

### Stack vs Heap

#### Stack
Stack is more or less responsible for keeping track of what's executing in our code (or what's been "called").
Value types are stored in the Stack.
(FILO) -> First In Last Out.
Links to an external site.Heap
#### Heap
Heap is responsible for keeping track of our objects.
Reference Types are stored in the heap.
