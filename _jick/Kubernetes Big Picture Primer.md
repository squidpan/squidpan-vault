---
category:
  - "[[Courses]]"
author:
  - Nigel Poulton
cover: 
genre:
  - "[[IT-Cloud]]"
length: 
year: 2024
rating: 7
topics:
  - "[[Cloud Computing]]"
  - "[[Kubernetes]]"
last: 2024-11-20
via: 
tags:
  - references
  - courses
created: 2024-11-20
---

## In A Nutshell: Kubernetes

- Kubernetes is an open-source platform for running **cloud-native apps**.
- Kubernetes is the layer above infrastructure (bare metal on premise or some infrastructure on a cloud platform) that runs your cloud-native apps.
- Kubernetes provides a rich API and an extensive set of primitives for running cloud-native apps
- Kubernetes is the platform of choice when it comes to running these cloud-native apps.
## What is Cloud-native app

Cloud-native apps are a collection of small, specialized components, usually containers that come together to form a meaningful application.

- Built from lots of small interacting services that come together to form a _useful_ app.
- Easy to scale and update because of small simple components and you can even do things like canaries and blue-greens.
- Opposite of the old monolithic apps, nightmare to scale or do updates on.
## Kubernetes Cluster

A Kubernetes cluster is made up of a bunch of Linux nodes (e.g. VMs or cloud instances)
But some of them form the control plane, and others, the worker nodes.

- Control plane: The brains of the cluster where all the magic happens.
- Workers: This is where your apps run.

### Control Plane

Control plane is pretty much the **API server**, the scheduler, a bunch of controllers, and _a persistent store_. So you want to make HA. so 3, 5, or 7 nodes maybe.

For now, the _store_ is **etcd**, and it's the **only stateful bit** of the entire **control plane**.

To deploy a separate etcd cluster with its own HA. That way, the rest of the control plane becomes stateless, and upgrades and the likes are going to be way easier.
you'll also get better performance and separation of concerns.

## API Server

The API server is the gateway into the cluster like the grand central station of the control plane.
All requests to create, update, delete, and even list things on the cluster, all go through the API server.

>[!info] So you as an admin or whatever, you're talking to the API server when you're deploying and managing your apps.

But also, all the nodes and the bits of the control plane are talking to it as well.

In fact, the vast majority of traffic on all Kubernetes clusters is system components that are talking to the API server.

but you've got your cluster, and you post requests to the API server to deploy and manage apps.

The scheduler and the controllers take care of the mechanics of making those requests happen, and your apps actually run on the worker nodes.

Rich set of primitives that make Kubernetes the best platform of choice for cloud-native apps.

you write your code in a cloud-native way - lots of small specialized microservices.
These all talk to each other over their own APIs.
You package them up in a way that will run on Kubernetes,
and you feed them to the API server,
and Kubernetes takes care of running them.
