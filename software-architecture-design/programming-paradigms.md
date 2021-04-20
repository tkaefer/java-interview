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

## Relationships between classes

![image](https://user-images.githubusercontent.com/29313557/115466545-dedae100-a24d-11eb-9693-ec64c9a4cdb8.png)

**Association** : An Association is the basic term to represent the relation between objects. Example : _A student and a teacher are having an association_.

**Aggregation** : Aggregation is more specific than Association. It is a variant of the **"has a"** or association relationship. referred to as a **Weak Association**:  Example : Relationship between library and student is aggregation. A student can exist without a library and therefore it is aggregation

**Composition** : Composition is more specific than aggregation. It is a stronger variant of the "**owns a"** or association relationship. Composition is also referred to as a Strong Association or Death relationship Example : Relationship between library and book is composition. A book cannot exist without a library and therefore its a composition

**Dependency**: Dependency is more specific than Composition. It is a weaker form of relationship which indicates that one class depends on another because it uses it at some point of time. I.e. One class depends on another.  Example: Relationship between shape and circle is dependency.

**Multiplicity** : Multiplicity is more specific than Composition. This is association relationship indicates that (at least) one of the two related classes makes reference to the other. I.e. one contains other and vice-versa.

**Realization** : A realization relationship between classes and interfaces and between components and interfaces shows that the class realizes the operations offered by the interface. A particular model of a car ‘GTB Fiorano’ that implements the blueprint of a car realizes the abstraction.

**Generalization**: Generalization uses a “is-a” relationship from a specialization to the generalization class. Common structure and behavior are used from the specialization to the generalized class. Example: Consider there exists a class named Person. A student is a person. A faculty is a person. Therefore here the relationship between student and person, similarly faculty and person is generalization.



