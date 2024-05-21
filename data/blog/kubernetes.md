---
title: 'Learn Kubernetes by its key concepts'
date: '2024/5/18'
lastmod: '2022/3/10'
tags: [Kubernetes, DevOps]
draft: false
summary: 'K8S is an open-source platform to automate the deployment, scaling, and management of containerized applications across clusters of machines.'
images: [/static/images/kuber.webp]
layout: PostLayout
---
## What is Kubernetes?
K8S is an Application(containers) Orchestrator. 

## What does it do?
- K8S deploy and manage applications(containers).
- scale up and down according demand
- zero Downtime Deployments
- rollbacks
- and more...

## Key Concept
### Cluster
- Cluster is a set of nodes
- Node - Virtual(VM) or Physical Machine
  - Master node(the brain): where the decisions are made
  - Worker node: where all the heavy lifting work happens, such as running applications

![](/static/images/kuber-1.png)

![](/static/images/kuber-2.png)

![](/static/images/kuber-3.png)
