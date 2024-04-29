---
title: "Some understanding of Spring Framework"
date: '2024/4/2'
lastmod: '2024/4/1'
tags: [Java, OOP]
draft: false
summary: "The three core concepts are Dependency Injection, Inversion of control and Aspect-oriented programming."
images: [/static/images/spring.png]
layout: PostLayout
---


## Spring Framework
[All versions of Spring Framework documentation](https://docs.spring.io/spring-framework/docs/)  

I started with [4.0.x](https://docs.spring.io/spring-framework/docs/4.0.x/spring-framework-reference/html/index.html) coz I find its layout well-structured and easy to get on. 
Also, I've chosen [5.3.x](https://docs.spring.io/spring-framework/docs/5.3.x/reference/html/index.html) and the current version [6.1.5](https://docs.spring.io/spring-framework/reference/)
to gain some comparison perspectives. with [Spring Boot](https://docs.spring.io/spring-boot/docs/current/reference/html/index.html) too.

## My approach
This time, I remind myself, always treat the documentation as a tree structure. 
Each tree node is a concept, and each concept branch out into several sub-concepts.
No concept stands alone. **In nature, everything is connected.**  
So first, get the upper most tree nodes (the most abstract ones). Then, branch out the sub-concepts.

|| Before drawing this tree of concepts in my mind, get the 10 keywords of Spring Framework to get a first impression.  
**Dependency Injection, Aspect-Oriented Programming(AOP), Inversion of Control(IOC), Model-View-Controller(MVC), 
Application Context, Bean, Bean Container, Spring Core, Transaction Management, Spring Data JPA**  
They will be explained later.

## What is Spring Framework
The Spring Framework is divided into modules (**Spring is modular**). Applications can choose which modules they need. 
At the heart are the modules of the core container, including a configuration model and a dependency injection mechanism. 
Beyond that, the Spring Framework provides foundational support for different application architectures, 
including messaging, transactional data and persistence, and web. It also includes the Servlet-based Spring MVC web framework and, 
in parallel, the Spring WebFlux reactive web framework.

## What is Spring Boot
We don't need to do the hell configuration XML Bean anymore! Or other configurations!
The fundamental idea of Spring Boot is **Convention over Configuration** (CoC).
This means Developers only need to specify the part that is not compliant. Spring Boot configures the convention.
It saves developers lots of time.

![iaa](/static/images/spring-overview.png)

## What does Spring solve and how
**What**: Spring Framework is an open-source application framework for Java. It provides comprehensive infrastructure support for developing Java applications.
It solves various problems in Java development, like complexity in configuration, tight coupling between components, and difficulty in testing.  
**How**: 
   - `Complexity in configuration`: Instead of manually creating and managing objects and their dependencies, Spring Framework simplifies configuration by introducing `Dependency Injection` and `Inversion of Control`. This approach reduces the complexity of configuration. Developers can focus on writing business logic while letting Spring handle the object creation and wiring.
   - `Tight coupling between components`: Spring promotes loose coupling between components through Dependency Injection. By injecting dependencies into classes rather than instantiating them internally, Spring decouples components from their dependencies.
This loose coupling makes components more modular, reusable, and easier to maintain.
   - `Difficulty in testing`: Traditional Java applications suffer from difficulties in testing due to their tight coupling and complex configuration. Spring Framework makes testing easier by promoting `Dependency Injection` and providing support for integration testing and mocking frameworks.
With Dependency Injection, dependencies can be easily substituted with mock objects or stubs during testing, allowing developers to isolate and test individual components in isolation.

## Walk through the lifecycle of a Spring project 
using annotations, from application startup to the execution of a controller method.
1. **Bootstrap Process**  
    When I start a Spring application, the Spring container is initialized in the `main()` method. During startup, Spring Boot scans the application's classpath for components annotated with `@Components`, `@Controller`, `@Service`, `@Repository`, and other stereotype annotations. 
    ```Java
    import org.springframework.boot.SpringApplication;
    import org.springframework.boot.autoconfigure.SpringBootApplication;
    
    @SpringBootApplication
    public class MySpringApplication {
    
        public static void main(String[] args) {
            // Initialize the Spring container by running the main application class
            SpringApplication.run(MySpringApplication.class, args);
        }
    }
    ```
   The `@SpringBootApplication` meta-annotation combines 
   - `@Configuration` : indicates `MySpringApplication` class provides bean configurations, use `@Bean` in Java-based configuration classes.
   - `@ComponentSan` : configures component scanning for Spring beans. It tells Spring where to look for Spring-managed components, such as controllers, services, repositories, and other beans.
   - `@EnableAutoConfiguration` : enables Spring Boot's auto-configuration mechanism. It automatically configures the Spring application based on the classpath dependencies.
2. **Bean Registration**
   - Spring detects classes annotated with stereotype annotations like `@Component`, `@Service`, etc. and registers them as beans in the application context.
   - For classes annotated with `@Configuration`, Spring scans for `@Bean` methods and registers the beans defined by those methods.
   - Dependencies between beans are resolved, and beans are instantiated and initialized as needed.
3. **Dependency Injection**
   - Spring performs Dependency Injection to wire the beans together.
   - For beans with dependencies, Spring looks for matching beans in the application context and injects them into the dependent beans.
   - Injection can be done through constructor injection, setter injection, or field injection, depending on how I annotate my classes.
4. **Lifecycle Callbacks**
   - For beans that implement certain interfaces or use specific annotations, Spring provides lifecycle callbacks.
   - `@PostConstruct` annotation can be used on a method to indicate that it should be invoked after bean initialization.
   - `@PreDestory` annotation can be used on a method to indicate that it should be invoked before the bean is destroyed.
5. **Handling HTTP Requests**
   - In a Spring MVC application, when an HTTP request is received, it's routed to the appropriate controller method based on the request mapping annotations (`@RequestMapping`, `@GetMapping`, `@PostMapping`, etc.).
   - The controller method is invoked, and any method parameters annotated with `@RequestParam`, `@PathVariable`, or other parameter annotations are populated with the values from the HTTP request.
   - The controller method processes the request, interacts with services or repositories, and prepares a response.
6. **Generating HTTP Response**
   - If the controller method returns a view name (for server-side rendering) or a response body (for RESTful APIs), Spring MVC renders the appropriate response.
   - If the method returns a view name, Spring MVC resolves the view, applies any model attributes set in the controller method, and generates the HTML response.
   - If the method returns a response body, Spring MVC serializes the return value to JSON, XML, or another format specified by the `@ResponseBody` annotation, and sends it as the HTTP response body.
7. **Request Processing Lifecycle**
   - Throughout the request processing lifecycle, Spring manages the lifecycle of beans, handles exceptions, manages transactions (if configured), and provides other services needed for application development.
8. **Shutdown Process**
   - When the application shuts down (e.g., when the server is stopped), Spring destroys the beans in the application context.
   - For beans with a `@PreDestroy` annotated method, Spring invokes this method to perform any necessary cleanup before the bean is destroyed.

## Three core concepts of Spring Framework
  
- **Dependency Injection**
  - DI is a design pattern. The dependencies of a class are injected from the outside rather than created internally. 
  - It helps in decoupling components and make them easier to test, maintain and reuse.
  - DI can be achieved through 
    - **constructor injection**
      ```Java 
      public class MyClass {
          private final Dependency dependency;

          public MyClass(Dependency dependency) {
            this.dependency = dependency;
          }
      }
      ```

    - **setter injection**
      ```Java 
      public class MyClass {
          private Dependency dependency;

          public void setDependency(Dependency dependency) {
            this.dependency = dependency;
          }
      }
      ```
    - **field injection**
      ```Java 
      public class MyClass {
          @Autowired
          private Dependency dependency;
      }
      ```

- **Inversion of Control (IoC) container.**
  IoC is a software engineering **design principle**.
  The control over object creation and management is shifted from the application code to a framework or container.
  This promotes decoupling, flexibility, and easier testing.
  In Spring Framework, IoC is achieved through techniques like dependency injection and is managed by the ApplicationContext container.
- **AOP framework.**
  AOP is born for **decoupling** and scalability. It enables modularization of cross-cutting concerns such as logging, security and transaction management. AOP allows developers to separate these concerns from the business logic and add them declaratively to the application.
  Developers can add new aspect without changing the source code or function flow.
  Its basic principle is **Dynamic proxy technology**, the same as **Proxy design pattern**. (check out my article about [Design Pattern](https://www.hang-dong.work/blog/design-pattern)).
    - How to implement it?  
      - First annotate a class with `@Aspect` to mark it as an aspect. 
      - THen define `pointcut` expressions using annotations like `@Before`, `@After`, or `@Around` to specify where the aspect should be applied. 
      - Implement `advice methods` within the aspect class, containing the logic to be executed at the specified points. 
      - Configure the aspect and pointcut expressions in the Spring application context. 
      - Finally, ensure that the aspect is properly triggered at the designated join points during runtime to apply the desired behavior across the application.
    ```xml
    <aop:config>
        <aop:aspect ref="TransactionManager">
            <aop:pointcut id="pt" expression="execution(public void service.impl.UserServiceImpl.insert())"/>
            <aop:before method="begin" pointcut-ref="pt"/>
            <aop:after-returning method="commit" pointcut-ref="pt"/> <aop:after-throwing method="rollback" pointcut-ref="pt"/> <aop:after method="closeSession" pointcut-ref="pt"/>
        </aop:aspect>
    </aop:config>
    ```
    ```Java
    @Aspect
    @Component
    public class TransactionManagerHandler{
      @Pointcut("execution(public void service.imple.UserServiceImpl.insert())")
      public void pointcut(){}
    
      @Before("pointcut()")
      public void begin(){
      System.out.println("start transaction");
      }
    
      @AfterReturning("pointcut()")
      public void commit(){
      System.out.println("submitted transaction");
      }
    
      @AfterThrowing("pointcut()")
      public void rollback(){
      System.out.println("rollback transaction");
      }     
    }
    ```

## The lifecycle of a bean
- **Instantiation**: Beans are created by the Spring container.
- **Population of Properties**: Dependencies and properties are injected into the bean.
- **Bean Post-Processing**: Custom initialization logic can be applied.
- **Initialization**: Initialization callbacks are invoked.
- **Bean Ready for Use**: Beans is fully configured and available.
- **Destruction**: Beans are destroyed when the application context shuts down or explicitly destroyed.




