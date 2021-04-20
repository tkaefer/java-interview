# Programming Paradigms

## Functional Programming
- Process of building software by composing **pure functions**, avoiding **shared state**, **mutable data**, and **side-effects**. 
- **Declarative (what to do)** rather than **imperative(how to do it)**, and application state flows through pure functions. 
- Examples :**JavaScript**, **Python**.

## Structured Programming
- Aimed at improving the clarity, quality, and development time of a computer program by making extensive use of the structured control flow constructs of selection (if/then/else) and repetition (while and for), block structures, and subroutines.
- Code will execute the instruction by instruction one after the other. It doesn’t support the possibility of jumping from one instruction to some other with the help of any statement like GOTO, etc. 

## Object-Oriented Programming 
- relies on the concept of **classes** and **objects**.
- Used to structure a software program into simple, reusable pieces of code blueprints (usually called classes), which are used to create individual instances of objects.


### Benefits of OOP
- OOP models complex things as reproducible, simple structures
- Reusable, OOP objects can be used across programs
- Allows for class-specific behavior through polymorphism
- Easier to debug, classes often contain all applicable information to them
- Secure, protects information through encapsulation

### Building blocks of OOP
fundamental building blocks of an OOP program are:
- Classes : abstract blueprint used to create more specific, concrete objects. 
- Objects: instances of classes
- Methods : represent behaviors. 
- Attributes: information that is stored

### Four Principles of OOP
- **Inheritance**: child classes inherit data and behaviors from parent class. **Inheritance supports reusability**. In JavaScript, inheritance is also known as prototyping.
- **Encapsulation**: containing information **in an object**, exposing only selected information. **Encapsulation adds security and Hides complexity**
- **Abstraction**: only exposing high level public methods for accessing an object. **Simple classes to represent complexity**. Abstraction is an extension of encapsulation.
- **Polymorphism**: refers to the same object exhibiting different forms and behaviors. many methods can do the same task. Designing objects to **share behaviors**.

### Method overriding and Method overloading.
 Polymorphism allows the same method to execute different behaviors in two ways: method overriding and method overloading.
 **Method Overriding**: **Runtime(Dynamic)** polymorphism uses method overriding. In method overriding,a child class can provide a different implementation than its parent     class. 
 **Method Overloading**: **Compile Time(or Static)** polymorphism uses method overloading. Methods or functions may have the same name, but a different number of parameters     passed into the method call. Different results may occur depending on the number of parameters passed in.

### Abstract classes
- An abstract class is a restricted class that cannot be used to create objects and can only be accessed through inheritance.
- These kinds of classes are declared using the abstract keyword.
- An abstract class can have an abstract method, unlike a regular class.
- An abstract method has no body or definition and must not be private
- An abstract class can have everything else as same as a normal Java class has, i.e. constructor, static variables, and methods.

### Constructors in Java
-  Used for initializing new object states. 
-  **Default Constructor**: This is also known as a no-argument constructor. It is the most basic type of constructor. Here, the default values of for data members of the        class are defined, which creates an object with data members initialized with default values.
-  **Parameterized Constructor** : In a parameterized constructor, we pass arguments to the constructor and set them as the values of our data members. They are used to set      fields of a class with your own values.
-  If a constructor is not defined within a class, the JVM will insert a default constructor without an argument and set its arguments to null or zero.

![image](https://user-images.githubusercontent.com/29313557/115464933-71c64c00-a24b-11eb-9a87-c9254542c997.png)

