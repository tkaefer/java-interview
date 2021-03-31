## What are microservices?
Microservices - also known as the microservice architecture - is an architectural style that structures an application as a collection of services that are

 - Highly maintainable and testable - enables rapid and frequent development and deployment
 - Loosely coupled with other services - enables a team to work independently the majority of time on their service(s) without being impacted by changes to other services and      without affecting other services
 - Independently deployable - enables a team to deploy their service without having to coordinate with other teams
 - Capable of being developed by a small team - essential for high productivity by avoiding the high communication head of large teams

Services communicate using either synchronous protocols such as HTTP/REST or asynchronous protocols such as AMQP. Services can be developed and deployed independently of one another. Each service has its own database in order to be decoupled from other services. Data consistency between services is maintained using the Saga pattern

