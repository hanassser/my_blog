---
title: "Exploring software architecture: A comprehensive overview"
date: '2024/4/4'
lastmod: '2022/3/10'
tags: [software architecture]
draft: false
summary: ""
images: [/static/images/architecture.jpg]
layout: PostLayout
---

## What is software architecture
It's the fundamental structure of a software.
It also refers to the high-level design and organization of a software system, 
including how components are structured, how they interact, 
and how the system meets its functional and non-functional requirements.
It encompasses decisions about component composition, communication, quality attributes, deployment, evolution, and documentation. 
A well-designed architecture ensures that the software system is scalable, maintainable, and adaptable to changes over time.

## Importance of software architecture
Software architecture plays a crucial role in the success of software projects. It's like the bones of your body.
It defines the system's structure and behavior, facilitating communication among components. A well-designed architecture ensures alignment with business goals,
scalability to handle increasing demands, and adaptability to evolving requirements.

## Key principles of software architecture
- Modularity
- Abstraction
- Separation of concerns
- Scalability
- Maintainability
- Flexibility

## Common software architecture patterns
- **Microservice**  
  The application is composed of loosely coupled, independently deployable services. 
  Each service is focused on a single business capability and communicates with other services through well-defined APIs, 
  often using lightweight protocols like HTTP or messaging queues.
    - `Advantages`
      - **Scalability**: the service can be scaled independently rather than the whole application.
      - **Flexibility and agility**: since each service is independent, teams can work on and deploy services independently. This allows for faster iteration and easier update.
      - **Resilience and faute isolation**: failure of one service doesn't necessarily bring down the entire application, other services can continue to operate.
    - `Disadvantages`
      - **Complexity of distributed systems**: managing communication between services, handling distributed data, ensuring consistency, and dealing with issues like network latency and failures.
      - **Operational overhead**: managing and deploying multiple services requires additional operational effort. This includes monitoring, logging, debugging, and managing the infrastructure for each service.
      - **Increased resource consumption**: each service requires its own runtime environment and resources.
- **Event-driven architecture (EDA)**  
    The flow of the application's logic is determined by events. The application components(or services) communicate with each other by producing or consuming events.
    In other words, actions or events trigger responses or actions within the system. Components communicate indirectly through events.
- **Layered architecture**  
    The software system is divided into multiple layers, each responsible for a specific aspect of functionality. Common layers include presentation, business logic, persistence, and database layer.
    This pattern promotes separation of concerns and modularity, making it easier to understand, develop, and maintain the system.
- **Model-View-Controller (MVC)**  
  the model (data and business logic), the view (presentation layer), and the controller (handles user input and updates the model and view accordingly). 
  MVC promotes separation of concerns and facilitates modular and maintainable UI development.
- **Service-Oriented Architecture (SOA)**  
  SOA is an architectural style that structures the application as a collection of loosely coupled services, which can be independently deployed and orchestrated to fulfill business requirements. Services in SOA are typically accessed via standardized interfaces (e.g., web services) and promote reusability, interoperability, and flexibility.

## Evolution of software architecture
Software architecture has evolved over time in response to changing technology trends, development methodologies, and business needs. 
From `monolithic` architectures to `distributed systems` and `cloud-native` architectures, the evolution of software architecture reflects advancements in computing paradigms and industry practices.
  
## Case studies and real-world examples
I'll write another blog about this in details.

  



