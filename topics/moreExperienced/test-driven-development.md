#### 14. TDD test driven development
- TDD is an iterative software development process where you first write the test with the idea that it must fail. This is a different approach to the traditional development where you write the application functionality first and then write test cases.
-
EJB 3.0 Interview Questions
Test Driven Development Interview Questions

What is Test Driven Development (TDD) ?
TDD is an iterative software development process where you first write the test with the idea that it must fail. This is a different approach to the traditional development where you write the application functionality first and then write test cases. The major benefit of this approach is that the code becomes thoroughly unit tested (you can use JUnit or other unit testing frameworks). TDD is based on two important principles preached by its originator Kent Beck:
Write new business code only if an automated unit test has failed: Business application requirements drive the tests and tests drive the actual functional code. Each test should test only one business concept, which means avoid writing a single test which tests withdrawing money from an account and depositing money into an account. Any change in the business requirements will impact pre and post conditions of the test. Talking about pre and post conditions, following design by contract methodology helps achieving TDD. In design by contract, you specify the pre and post conditions that act as contracts of a method, which provides a specification to write your tests against.
Eliminate duplication from the code: A particular business concept should be implemented only once within the application code. Code for checking an account balance should be centralized to only one place within the application code. This makes your code decoupled, more maintainable and reusable. I can hear some of you all saying how can we write the unit test code without the actual application code. Let's look at how it works in steps. The following steps are applied iteratively for business requirements.
STEP: 1
write some tests for a specific business requirement.
STEP: 2
write some basic structural code so that your test compiles but the test should fail (failures are the pillars of success). For example just create the necessary classes and corresponding methods with skeletal code.
STEP: 3
write the required business code to pass the tests which you wrote in step 1.
STEP: 4
finally refactor the code you just wrote to make it is as simple as it can be. You can refactor your code with confidence that if it breaks the business logic then you have unit test cases that can quickly detect it.
STEP: 5
run your tests to make sure that your refactored code still passes the tests.

#### What is the point of Test Driven Development (TDD) ? What do you think of TDD ?
- TDD process improves your confidence in the delivered code for the following reasons.
- TDD can eliminate duplication of code and also disciplines the developer to focus his mind on delivering what is absolutely necessary. This means the system you develop only does what it is supposed to do because you first write test cases for the business requirements and then write the required functionality to satisfy the test cases and no more.
- These unit tests can be repeatedly run to alert the development team immediately if someone breaks any existing functionality. All the unit tests can be run overnight as part of the deployment process and test results can be emailed to the development team.
- TDD ensures that code becomes thoroughly unit tested. It is not possible to write thorough unit tests if you leave it to the end due to deadline pressures, lack of motivation etc.
- When using TDD, tests drive your code and to some extent they assist you in validating your design at an earlier stage.
- TDD also helps you refactor your code with confidence that if it breaks the business logic it gets picked up when you run your unit tests next time.
- TDD promotes design to interface not implementation design concept.
