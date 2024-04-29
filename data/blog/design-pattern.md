---
title: "Design Patterns explained with code"
date: '2024/4/29'
lastmod: '2022/3/10'
tags: [Design pattern]
draft: false
summary: "Design patterns are typical solutions to commonly occurring problems in software design.
They are like pre-made blueprints that you can customize to solve a recurring design problem in your code."
images: [/static/images/design-pattern.png]
layout: PostLayout
---

## What is Design Pattern
Design patterns are typical solutions to commonly occurring problems in software design. 
They are like pre-made blueprints that you can customize to solve a recurring design problem in your code.
The pattern is not a specific piece of code, but a general concept for solving a particular problem.
A pattern is a more high-level description.  
(Dive Into Design Patterns, Alexander Shvets)


## Why it matters
- **Code Reusability**
  - it provides proven solutions to recurring design problems. don't need to reinvent the wheel. more efficient.
- **Scalability**
  - it provides structures and guidelines that can accommodate changes and growth in the system. Patterns such as the Factory Method or Abstract Factory allow for easy addition of new types of objects without modifying existing code.
- **Maintainability**
  - it's easier to understand and maintain.
- **Standardization**
  - it provides a common language and set of concepts that developers can use to communicate and collaborate effectively.
- **Quality Assurance**
  - it promotes best practices and architectural principles that lead to higher-quality software.


## Classification of patterns (by their intent)
- **Creational patterns**
  provide object creation mechanisms that increase flexibility and reuse of existing code.
  - `Singleton`  
    The Singleton pattern ensures that a class only have one instance, and provides a global point of access to that instance.  
    ```Java
    public class Singleton {
       private static Singleton instance;
       private Singleton(){}
       public static Singleton getInstance(){
           if(instance == null){
               instance = new Singleton();
           }
           return instance;
       }
    }
    ```
  - `Factory Method`  
    Factory Method provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created.
    ```Java
    interface Animal {
      void makeSound();
    }
  
    class Dog implements Animal {
      @Override
      public void makeSound(){
          System.out.println("Woof");
      }
    }
    class Cat implements Animal {
      @Override
      public void makeSound(){
          System.out.println("Meow");
      }
    }
    
    public class AnimalFactory {
      public static Animal createAnimal(String type){
          if("dog".equalsIgnoreCase(type)){
              return new Dog();
          } else if("cat".equalsIgnoreCase(type)){
              return new Cat();
          }
          return null;
          // this may cause nullPointerException, can replaced by throw an exception
      }
    }
    ```
  - `Abstract Factory`  
    

  - `Builder`
  - `Prototype`

- **Structural patterns**
  explain how to assemble objects and classes into larger structures, while keeping the structures flexible and efficient.
  - Adapter
  - Bridge
  - Composite
  - `Decorator`
    It lets you attach new behaviors to objects by placing these objects inside special wrapper objects that contain the behaviors.
  - Facade
  - Flyweight
  - `Proxy`  
    Proxy is a structural design pattern that lets you provide a substitute or placeholder for another object. A proxy controls access to the original object, allowing you to perform something either before or after the request gets through to the original object.
    Proxy pattern is wildly used in Spring Boot:
    - Dependency Injection (DI): Spring Boot uses the Proxy Pattern extensively for dependency injection. When you annotate a class with `@Component`, `@Service`, `@Repository`, or `@Controller`, Spring creates a proxy instance of that class to manage its lifecycle, handle dependencies, and provide additional features such as transaction management, aspect weaving, and caching.
    - Aspect-Oriented Programming (AOP): AOP is a key feature of Spring Boot, and proxies play a central role in implementing cross-cutting concerns such as logging, security, and transaction management. Spring Boot uses dynamic proxies or bytecode manipulation (with libraries like CGLIB) to create proxies for classes annotated with `@Aspect`. These proxies intercept method invocations and execute advice (e.g., before, after, around) defined in the aspect.
    - Transaction Management: Spring Boot uses proxies to manage transactions declaratively using annotations such as `@Transactional`. When you annotate a method with `@Transactional`, Spring creates a proxy around the bean containing that method. This proxy intercepts method calls and starts, commits, or rolls back transactions as necessary.
- **Behavioral patterns**
  take care of effective communication and the assignment of responsibilities between objects.
  - `Strategy`  
    Strategy is a behavioral design pattern that lets you define a family of algorithms, put each of them into a separate class, and make their objects interchangeable. It lets the algorithm vary independently from the clients that use it.
    ```Java
    interface PaymentStrategy {
        void pay(int amount);
    }
  
    class CreditCardPayment implements PaymentStrategy {
        @Override
        public void pay(int amount) {
            // pay by Credit card
        }
    }
  
    class PayPalPayment implements PaymentStrategy {
        @Override
        public void pay(int amount) {
            // pay by PayPal
        }
    }
  
    class ShoppingCart {
        private PaymentStrategy paymentStrategy;
  
        public void setPaymentStrategy(PaymentStrategy paymentStrategy) {
            this.paymentStrategy = paymentStrategy;
        }
  
        public void checkout(int amount) {
            paymentStrategy.pay(amount);
        }
    }
    ```
  - `Observer`  
    The Observer design pattern is a behavioral design pattern that defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically. 
    It is also known as the Publish-Subscribe pattern.
  
  - Chain of Responsibility
  - Command
  - Iterator
  - Mediator
  - Memento
  - State
  - Template Method
  - Visitor
