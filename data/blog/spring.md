---
title: "Some understanding of Spring Framework"
date: '2024/3/30'
lastmod: '2024/4/1'
tags: [Java, OOP]
draft: false
summary: "The two core technologies are Inversion of control and Aspect-oriented programming."
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
I shall explain all these concepts later in my words.


## What is Spring
The Spring Framework is divided into modules (**Spring is modular**). Applications can choose which modules they need. 
At the heart are the modules of the core container, including a configuration model and a dependency injection mechanism. 
Beyond that, the Spring Framework provides foundational support for different application architectures, 
including messaging, transactional data and persistence, and web. It also includes the Servlet-based Spring MVC web framework and, 
in parallel, the Spring WebFlux reactive web framework.

![iaa](/static/images/spring-overview.png)

## What is Spring Boot
We don't need to do the hell configuration XML Bean anymore! Or other configurations!
The fundamental idea of Spring Boot is **Convention over Configuration** (CoC).
This means Developers only need to specify the part that is not compliant. Spring Boot configures the convention.
It saves developers lots of time.


## Two Core technologies
  
- **Inversion of Control (IoC) container.**
- **AOP framework.**

IoC is a software engineering **design principle**.
The control over object creation and management is shifted from the application code to a framework or container.
This promotes decoupling, flexibility, and easier testing. 
In Spring Framework, IoC is achieved through techniques like dependency injection and is managed by the ApplicationContext container.

AOP is fantastic for decoupling and scalability. Coz I can add new features without changing the source code or function flow.
Its basic principle is **Dynamic proxy technology**, the same as **Proxy design pattern**. (check out my article about [Design Pattern]()).

### The IOC container

## Spring Boot




