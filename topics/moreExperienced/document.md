#### 8. Lazy loading and lazy fetching?
- Say you have a parent and that parent has a collection of children. Hibernate now can "lazy-load" the children, which means that it does not actually load all the children when loading the parent. Instead, it loads them when requested to do so. You can either request this explicitly or, and this is far more common, hibernate will load them automatically when you try to access a child.
- "Lazy loading" means that an entity will be loaded only when you actually accesses the entity for the first time.
- Lazy fetching decides whether to load child objects while loading the Parent Object. You need to do this setting respective hibernate mapping file of the parent class.


#### 10. http verbs:
- The POST verb is most-often utilized to **create** new resources. In particular, it's used to create subordinate resources. That is, subordinate to some other (e.g. parent) resource. In other words, when creating a new resource, POST to the parent and the service takes care of associating the new resource with the parent, assigning an ID (new resource URI), etc.
On successful creation, return HTTP status 201, returning a Location header with a link to the newly-created resource with the 201 HTTP status.
POST is neither safe nor idempotent
- The HTTP GET method is used to **read** (or retrieve) a representation of a resource. In the “happy” (or non-error) path, GET returns a representation in XML or JSON and an HTTP response code of 200 (OK). In an error case, it most often returns a 404 (NOT FOUND) or 400 (BAD REQUEST).
- PUT is most-often utilized for **update** capabilities, PUT-ing to a known resource URI with the request body containing the newly-updated representation of the original resource.
However, PUT can also be used to create a resource in the case where the resource ID is chosen by the client instead of by the server. In other words, if the PUT is to a URI that contains the value of a non-existent resource ID
- PATCH is used for **modify** capabilities. The PATCH request only needs to contain the changes to the resource, not the complete resource.
- DELETE is pretty easy to understand. It is used to **delete** a resource identified by a URI.
On successful deletion, return HTTP status 200 (OK) along with a response body, perhaps the representation of the deleted item (often demands too much bandwidth), or a wrapped response (see Return Values below). Either that or return HTTP status 204 (NO CONTENT) with no response body. In other words, a 204 status with no body, or the JSEND-style response and HTTP status 200 are the recommended responses.


#### 11.  What is Exception Handling?
- Exception Handling is a mechanism to handle runtime errors.
- 1) Checked Exception
The classes that extend Throwable class except RuntimeException and Error are known as checked exceptions e.g.IOException, SQLException etc. Checked exceptions are checked at compile-time.

2) Unchecked Exception
The classes that extend RuntimeException are known as unchecked exceptions e.g. ArithmeticException, NullPointerException, ArrayIndexOutOfBoundsException etc. Unchecked exceptions are not checked at compile-time rather they are checked at runtime.

3) Error
Error is irrecoverable e.g. OutOfMemoryError, VirtualMachineError, AssertionError etc.




#### 13. explain flow of things when user clicks ui to backend?
- https://www.quora.com/How-do-front-end-and-back-end-technologies-work-together


#### Automatic dirty checking?
- Hibernate uses a strategy called inspection, which is basically this: when an object is loaded from the database a snapshot of it is kept in memory. When the session is flushed Hibernate compares the stored snapshot with the current state. If they differ the object is marked as dirty and a suitable SQL command is enqueued. If the object is still transient then it is always dirty.

#### Automatic Json validate?
``` java
public static void main( String[] args ) throws IOException, ProcessingException
{
    File schemaFile = new File("/Users/XYZ/schema.json");
    File jsonFile = new File("/Users/XYZ/data.json");

    if (ValidationUtils.isJsonValid(schemaFile, jsonFile)){
    	System.out.println("Valid!");
    }else{
    	System.out.println("NOT valid!");
    }
}
```
- using jacksson library

#### what is cors?
- Cross-Origin Resource Sharing (CORS) is a mechanism that uses additional HTTP headers to let a user agent gain permission to access selected resources from a server on a different origin (domain) than the site currently in use. A user agent makes a cross-origin HTTP request when it requests a resource from a different domain, protocol, or port than the one from which the current document originated.

#### Stringbuilder or buffer?
- StringBuffer is synchronized, StringBuilder is not.
- StringBuilder is faster than StringBuffer because it's not synchronized.

#### What is countdown latch?
- CountDownLatch is used to make sure that a task waits for other threads before it starts.
- When we create an object of CountDownLatch, we specify the number of threads it should wait for, all such thread are required to do count down by calling CountDownLatch.countDown() once they are completed or ready to the job. As soon as count reaches zero, the waiting task starts running.
- https://www.geeksforgeeks.org/countdownlatch-in-java/
-  once count reaches zero you cannot use CountDownLatch any more


#### joint point vs point cu
- Pointcut: a predicate that matches join points. A point cut is something that defines at what join points an advice should be applied

These spring interview Questions are not very difficult in nature and focused on spring fundamentals rather than focusing on advanced feature of session management, sprint security, authentication etc. we will cover of those question on some other interview article. I would also suggest that share some spring questions asked to you guys during interview and then I can put together those with their answers for quick reference of everybody.

When you go out to a restaurant, you look at a menu and see several options to choose from. You can order one or more of any of the items on the menu. But until you actually order them, they are just “opportunities to dine”. Once you place the order and the waiter brings it to your table, it’s a meal.

- Join points are the options on the menu and pointcuts are the items you select. A joinpoint is an opportunity within code for you to apply an aspect…just an opportunity. Once you take that opportunity and select one or more joinpoints and apply an aspect to them, you’ve got a pointcut.

#### CI/CD pipeline
- continuous integration and deployment
- Continuous Integration can be defined as “Building software and taking it through as many tests as possible with every change”.
- What steps are in continuous integration? More steps in continuous integration means more stability.
Compilation
Unit Tests
Code Quality Gates
Integration Tests
Deployment
Chain Tests

#### how can you improve performance of web app?
- https://stackify.com/java-performance/




#### what are the important spring security parameters hat you should follow?
- How does Spring Security Authentication work? Here are a few steps to know.

The user logs in with a name (username or email) and a password. These two credentials are combined into an instance of the class UsernamePasswordAuthenticationToken (which is itself an instance of the Authentication interface). Then, they’re passed to the AuthenticationManager for verification.
If the password does not match the username, the BadCredentialsException is returned along with the message “Bad Credentials.”
If the password and username match, it will return a populated Authentication instance.
The user sets a security context by calling the SecurityContextHolder.getContext () method setAuthentication (…), where the object that returned the AuthenticationManager is passed.
- https://www.upwork.com/hiring/development/spring-security-framework/

#### Types of transactional management in spring
-   Spring supports two types of transaction management:

 Programmatic transaction management : This means that you have to manage the transaction with the help of programming. That gives you extreme flexibility, but it is difficult to maintain.

 Declarative transaction management: This means you separate transaction management from the business code. You only use annotations or XML based configuration to manage the transactions.
 - https://dzone.com/articles/spring-transaction-management


#### custom exception in java?
- class NoSuchProductException extends RuntimeException
