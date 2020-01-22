
# Spring Framework

## Table of Contents

* [Spring Boot](#spring-boot) 
* [Spring Core](#spring-core)
* [Spring Security](#spring-security)
* [Spring Data](#spring-data)
* [Spring Cloud](#spring-cloud)
* [Spring Actuator](#spring-actuator)



### Spring Boot ###
- RAD (Rapid Application Development) feature to the Spring framework.
- Highly dependent on the **starter templates** feature which is very powerful and works flawlessly.
- Starters are templates that contain a collection of all the relevant transitive dependencies.
- **Parent pom is mandatory to control versions of child dependencies**
- No need to provide version information into child dependencies.
- **Spring boot = Spring Framework + Some Embedded HTTP Servers (Tomcat/Jetty etc.) – XML or Annotations Configurations.**
- **@EnableAutoConfiguration** - scans the classpath, finds the libraries in the classpath and then attempt to guess the best configuration for them, and finally configure all such beans.
- Spring boot applications always include tomcat as embedded server dependency. It can be excluded also using exclusion in pom.
-  **@SpringBootApplication = @Configuration + @EnableAutoConfiguration + @ComponentScan.**

### Advantages of Spring boot ###
- Resolving dependency conflict. It identifies required dependencies and import them for you.
- Information of compatible version for all dependencies. It minimizes the runtime classloader issues.
- It’s “opinionated defaults configuration” approach helps you in configuring most important pieces behind the scene. Override them only when you need. Otherwise everything just works, perfectly. It helps in avoiding boilerplate code, annotations and XML configurations.
- Provides embedded HTTP server Tomcat so that you can develop and test quickly.
- Excellent integration with IDEs like eclipse and intelliJ idea.

### Disadvantages of Spring Boot ###
- Include dependencies that are not used thereby causing huge deployment file size. 
- Turning legacy spring applications into Spring boot requires a lot of effort and a time-consuming process. 
- Limited control of your application.

### Spring Boot Annotations ###
-  spring boot annotations are mostly placed in org.springframework.boot.autoconfigure and org.springframework.boot.autoconfigure.condition packages. 
- @SpringBootApplication : The java class annotated with @SpringBootApplication is the main class of a Spring Boot application and application starts from here.
- @EnableAutoConfiguration : enable auto-configuration mechanism. SpringFactoriesLoader mechanism. Are @Conditional beans.
- @ComponentScan : enable @Component scan.
- @SpringBootConfiguration : register extra beans in the context. Automatically located. Alternative to @Configuration. 
- @ImportAutoConfiguration : only runs the configuration classes that we provide in the annotation. unlike EnableAutoConfiguration.
- @AutoConfigureBefore, @AutoConfigureAfter : Configuration needs to be applied in a specific order (before of after).
- @AutoConfigureOrder : Order certain auto-configurations that should not have any direct knowledge of each other.
- @Conditional : register a bean only when the condition meets.
- @ConditionalOnBean, @ConditionalOnMissingBean : bean included on presence or absence of specific beans. accepts by type or by name.
- @ConditionalOnClass, @ConditionalOnMissingClass : Configuration classes be included based on the presence or absence of specific classes. 

