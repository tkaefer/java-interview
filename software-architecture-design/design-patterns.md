## Design Patterns

- Design Pattern provides low-level solutions related to the implementation, of commonly occurring **object-oriented problems**

## Design principles vs Design Patterns
 - **Principle:** We should teach others in order to educate ourselves as well as others, and overall make our nation a progressive nation.
   **Pattern:** In our country, each medical doctor graduate is supposed to teach 6 months in a far-away village to complete his/her degree.

 - **Principles:** apply to all of programming. You should have a very good reason any time you choose not to follow principles.
   **Patterns:** apply to specific, common problems. You should have a very good reason any time you choose to implement a pattern.

### Creational

- Singleton-  Single instance of class. Either Eager (static) or Lazy (broken pre-JDK5). Eg: Logger, Configurer, java.lang.Runtime#getRuntime()
- Factory - Create types of instances. Centralized and not exposed to composing classes Eg: Trade type (Bonds, Bill, Notes), java.util.Calendar#getInstance()
- Abstract Factory - Factory of factories of related products. Eg: Trade Type (GermanBond, EuroBond, GermanBill, EuroBill), DocumentBuilderFactory#newInstance()
- Builder -alternative way to construct complex objects.Control on object creation procces.creating immutable classes Eg: StringBuilder
- Prototype - Copying costly-creation objects. Classes should implement clone or similar method eg java.lang.Object#clone() (the class has to implement java.lang.Cloneable)
- Object pool - Re-use instances. Eg: Threadpool

### Structural

- Adapter - Adapting to a non-direct-compatible class/module/system. e.g java.util.Arrays#asList()
- Decorator - Wrap class with another Eg: FileReader, BufferedReader
- Facade - Hiding complexity behind simple interfaces. Eg: Turbo Tax software, 
- Proxy - Eg: Hibernate proxy for lazy fetch. @Spy instances for JUnit/Mockito.
- Flyweight - Store common characteristics of multiple objects in single place. Eg: Glyph for all characters in a document.
- Bridge - Decouple abstraction from implementation so that both can vary independently. Bridge pattern is often created using Adapter pattern. 
- Composite - Eg: Folder and files
- 
### Behavioral

- Observer - Reactive streams. publish-subscribe pattern
- Strategy - Encapsulate algorithms and execute either. Eg: Trading strategy, select one and execute.
- Command - Object encapsulates action with common interface which executor calls. Eg: Remote click.
- State - Behavior based on current state of object.
- Visitor - Object which visits all similar instances. Eg: File Traverse, or Calculate total bill from cart.
- Iterator - Iterating through a collection of objects.
- Chain of Responsibility - object passes through various instances, coordinated by Handler. Eg: Stream API
- Template - Eg: HTML templates
- Interpreter - Format converter. Eg: JVM converts byte to native for JVM.
- Memento - Save and restore state of object.



### Resources

- [Design patterns explained too simply](https://github.com/kamranahmedse/design-patterns-for-humans)
- [Examples of design patterns in Java libraries](http://stackoverflow.com/questions/1673841/examples-of-gof-design-patterns-in-javas-core-libraries/2707195#2707195)
- [Full Stack Software Design and Architecture](https://www.freecodecamp.org/news/software-design/)
