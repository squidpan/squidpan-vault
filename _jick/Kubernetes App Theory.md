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
  - "[[Kubernetes]]"
last: 2024-11-20
via: ""
tags:
  - references
  - courses
created: 2024-11-20
---

## Business Requirements - a bunch

- [ ] web service to handle incoming requests
- [ ] a back-end store for persistent data
- [ ] front the web tier with a load balancer.
- [ ] on the back end - need some persistence storage.
And of course, if we want these two microservices,
that I'm gonna call 'em here.
- [ ] If we want them to talk to each other, we need some secrets, 
	- [ ] like a password to the database.
	- [ ] Or maybe we even want the name and the port of the database in the secret, as well.
Now, I'm just thinking out loud here.
- [ ] Maybe we need to back it up,
- [ ] we wanna be able to scale the web tier.

we start coding.
And before you know it, we've got some code that's 

- [ ] running a web service that's talking to a database on the back end.
But we're all about cloud native and microservices, yeah?

So how do we get that code and all of these requirements
onto our cloud-native platform?

- [ ] we need a Kubernetes cluster, obviously.
- [ ] running these services here as containers.

You've got a cluster.
your code and 
your front-end web service
the back-end database.
two container images.

For the load balancer here,

Kubernetes Service object: a resource in the API.
if you're running on a cloud platform, you can build one of these that actually spins up an internet-facing load balancer on your cloud.

That's the load balancer sorted.


Accepting requests, and you wanna 
- balance them across the web tier here
- which over time you expect to scale up and down as demand ebbs and flows.

Deployment
a k8s construct that wraps containers

Containers 

Containers get wrapped in pods, and it's actually the pods
that get wrapped in the Deployment.

But for now, right, like a Service,

a Deployment is a resource in the Kubernetes API - great for scaling things up and down.
the database back end.
So wrap those containers in pods and then in a 
Deployment or a stateful set for easy management.

Then we add in some secrets
to get them all talking to each other.

Now, we're big picture for now, yeah?
But to tick off 
the persistent storage requirement, - we throw 
in a persistent volume and 
a persistent volume claim.

they are resources in the API.

And a bit like the Service object up here,

these can hook into external storage systems outside of the cluster.



So like how I said for Service up here
spins on one of the cloud's own load balancers?
Well, the persistent volume down here,
that can create storage volumes on the cloud
or outside of the cluster, wherever, yeah?
And you know what?
That right there,
that is the makings of an app.
So a microservices-type app
with a front and a back end,
both independently scalable,
though you know what?
Yeah, the back end's probably gonna be a bit clunkier,
depending on the database technology.
But at the front here,
it is fronted by a cloud load balancer
defined as an object in Kubernetes.
While that's balancing across one or more web services
that are inside Kubernetes pods
managed by a Kubernetes Deployment.
And they're talking to the database back end,
backed by some persistent storage,
all secured by secrets,
which you've probably guessed, again,
are also objects on the Kubernetes cluster.
So despite some of the actual tech
being external to the cluster,
and I'm especially thinking here and here,
we still define those as objects in the cluster.
And Kubernetes just does the rest.
Fabuloso.
And that, Cloud Gurus, is a very simple
cloud-native microservices app.
Only, well, it's not, is it?
It's just a picture I made in PowerPoint.
And you know what?
I totally know that if you're new to this,
it's gonna be megafuzzy,
and you probably got brain fried.
Fear not, though.
Over the rest of this course,
we will cover this stuff off
again and again.
Speaking of which,
let's crack on and see what it might actually look like.
