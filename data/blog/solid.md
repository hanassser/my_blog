---
title: "SOLID design principles"
date: '2024/3/31'
lastmod: '2022/3/10'
tags: [Design pattern]
draft: false
summary: ""
images: [/static/images/design-pattern.png]
layout: PostLayout
---

## What is Design Pattern



## Design Pattern matters a lot




with [Spring Boot](https://docs.spring.io/spring-boot/docs/current/reference/html/index.html) too.

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

## History
///

## Two Core technologies


  
- **Inversion of Control (IoC) container.**
- **AOP framework.**

IoC is a software engineering **design principle**.
The control over object creation and management is shifted from the application code to a framework or container.
This promotes decoupling, flexibility, and easier testing. 
In Spring Framework, IoC is achieved through techniques like dependency injection and is managed by the ApplicationContext container.

AOP is fantastic for decoupling and scalability. Coz I can add new features without changing the source code or function flow.
Its basic principle is **Dynamic proxy technology**, the same as **Proxy design pattern**.

### The IOC container

## Spring Boot




