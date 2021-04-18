# Design Principles

- Design principles provide high-level guidelines to design better software applications. 
- They are concerned with providing means to handle the complexity of the design process effectively.
- Helps in Keeping code flexible and testable.


## SOLID principles

- S = Single Responsibility - Each class/instance should have only 1 responsibility
- O = Open Closed - Objects should be open for extension closed for modification
- L = Liskov substitution - Instance objects can be replaced with subtypes without altering correctness
- I = Interface Segregation - Multiple specific interfaces are better than big general one
- D = Dependency Injection - High level and Low level modules should both depend on abstraction

## Other design principles

- Code to interface not implementation
- Favor composition over inheritance
- Encapsulate what changes/varies
- Strive for loose coupling between objects
- Law of Demeter (LoD) or principle of least knowledg = Talk only to immediate friends - 
- The hollywood principle: "Don't call us, we'll call you". In other words, you don’t have to bother about when your turns come. When your turns come, they will call you.          Example : Upload resume for on company portal and company sends mails for interviews. 
   Spring DI: Think about Spring, where we declare beans in XML, and Spring containers call these beans to create Spring beans. We inject other beans into it, returning a fully    configured bean. So with the help of XML, we feed the strategy, and the Spring container calls them when required. We often call it Dependency Injection. In fact, you might    also know the Hollywood Principle by another name: IoC (Inversion of Control).
- **DRY (Do Not Repeat Yourself)** - Aimed at reducing repetition of software patterns, replacing it with abstractions or using data normalization to avoid redundancy.
- **YAGNI (You Aren't Gonna Need It) or You don't need it now" (YDNIN)** - It states a programmer should not add functionality until deemed necessary. In other words, Always implement things when you actually need them, never when you just foresee that you need them.
