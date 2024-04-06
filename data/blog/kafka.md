---
title: 'A short introduction of Apache Kafka'
date: '2024/4/3'
lastmod: '2022/3/10'
tags: [Kafka]
draft: false
summary: 'As the name indicated, Kafka is about writing. Writing data. Consume and produce data. '
images: [/static/images/kafka.png]
layout: PostLayout
---

## Topic
A topic is just an ordered collection of events that are stored in a durable way, durable meaning that they're written to disk, and they are replicated.
They're stored on more than one disk, more than one server, so no data failure. Topics can store data in a short period of time like hours or years or infinite.
Topics are a persistent record of events. Each one of these represents a thing happening in the business, like a user updating her shipping address or a train unloads cargo.
Kafka encourages you to think events first and things second.
Since monolith program becomes bigger and harder to think about, now the trend is to write lots of small program. They are easy to think about and evolve by themselves. 
They are talk to each other through Kafka topics. Each small program can consume a message from a Kafka topic, do some computation on its own, and produce that message off to another Kafka topic. 
With all these data live in persistent real-time streams, now it's possible to build new services that perform real-time analysis of that data.

- events
- topics
- services talk to each other through topics
- real-time analytics

distributive log thing


- OOP: OOP approach is about mapping the elements in the problem space into the objects in the solution space.
- SOLID
- Design Patterns
- Clean Code
- How to optimize code
- DevOps
- Docker
- System Design
- ML

///

- A collection of misunderstandings


///
- Javascript Frameworks: React, Next.js, Vue.js
