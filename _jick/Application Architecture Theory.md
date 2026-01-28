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
via: ""
tags:
  - references
  - courses
created: 2024-11-20
---

## Requirements

so we might need 
- a web service to handle incoming requests
- and a back-end store for persistent data.
- front the web tier with a load balancer.
- And then on the back end,  need some persistence storage.

If we want these two microservices to talk to each other, 
- maybe we need some secrets,
- like a password to the database.
	- Or maybe we even want the name and the port of the database in the secret, as well.
	-

Maybe we need to back it up,
and we wanna be able to scale the web tier.
Now there's a million things to plan and think about,
and this is by no means a complete list.
But we've got a bunch of requirements
that might look something like this.
And then we start coding.
And before you know it,
we've got some code that's running a web service
that's talking to a database on the back end.
But we're all about cloud native
and microservices, yeah?
So how do we get that code and all of these requirements
onto our cloud-native platform?
Kubernetes, yeah?
Well, we need a Kubernetes cluster, obviously.
And then for argument's sake,
I'm gonna say we're running
these services here as containers.
Now that's not to say that you can't use
serverless or VMs if you think they're better suited.
But you get the picture.
You've got a cluster.
Then you take your code and your front-end web service
and you build it as a darker image.
Same goes for the back-end database.
And you end up with two container images.
And then, well,
I'm just gonna start from the top and work down.
For the load balancer here,
and we'll see all the detail later in the course,
but Kubernetes has this Service object,
capital S Service,
and it's a resource in the API.
And if you're running on a cloud platform,
you can build one of these that actually spins up
an internet-facing load balancer on your cloud.
Well, bingo.
That's the load balancer sorted.
Now you're accepting requests,
and you wanna balance them across the web tier here,
which over time you expect to scale up and down
as demand ebbs and flows.
So you wrap your web containers
in a Kubernetes construct called a Deployment.
Well, actually, you know what?
Containers get wrapped in pods,
and it's actually the pods
that get wrapped in the Deployment.
But for now, right, like a Service,
a Deployment is a resource in the Kubernetes API,
and it is magic for scaling things up and down.
All right, well, we'd probably do the same
for the database back end.
So wrap those containers in pods
and then in a Deployment
or a stateful set for easy management.
Then we add in some secrets
to get them all talking to each other.
And so far, so good.
Now, we're big picture for now, yeah?
But to tick off the persistent storage requirement,
we throw in a persistent volume
and a persistent volume claim.
Again, and we're getting a bit into the weeds here,
but we'll see all of these later in the course.
For now, though, it is enough to know
that they are resources in the API.
And a bit like the Service object up here,
these can hook into external storage systems
outside of the cluster.
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
