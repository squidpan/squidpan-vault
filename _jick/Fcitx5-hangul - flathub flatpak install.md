---
category:
  - "[[Lessons]]"
author: 
cover: 
genre: 
length: 
year: 2025-08-08
rating: 
topics: 
last: 2025-08-08
via: ""
tags:
  - references
  - lessons
created: 2025-08-08
---

## In A Nutshell: Kubernetes API

Kubernetes API is where everything in Kubernetes is defined.
Everything we'll be working with is gonna be a resource that's defined in the API (pods deployment, the role resources in the API.)
It is a RESTful API, that uses standard HTTP methods and verbs to perform CRUDE style 
It supports these six verbs, and they work the same across all resources.

## kubectl
These mapped operations that you perform with kubectl, like creating, watching and deleting objects. 
Speaking of which, for the most part, our interaction with the API, is gonna be through the kubectl command line utility.

## YAML and Declarative Configuration

So it works a bit like this. We'll define the different parts of our apps in YAML files.
And we'll use kubectl to post them to the API server, assuming we can authenticate in the likes, 'cause our back is a thing these days.

But assuming we can authenticate, that'll create a record of intent on the cluster in the store.
Yeah, that record of intent changes the overall desired state of the cluster which in turn, causes the other bits of the control plane to kick into action.

I wanna explain this notion, of a declarative configuration.
You see, the Kubernetes way of deploying and managing apps, is to define the various parts of those apps in YAML file, you post these to the API server is a record of intent, and this updates the overall desired state of the cluster.

## Current State vs Desired State

Now in the background, 
the control planes running a ton of watch loops that are constantly checking, that the current observed state of the cluster, matches the current desired state.

While posting a new YAML file, that changes the desired state.

So before long, the watch loops will notice,
and various parts of the control plane kick into life, to bring that observed state into line with the new desired state.

I don't know an example might be a cluster with let's say,
five running replicas of a service that compresses images.
If you post an updated YAML file to the cluster,
changing the desired state to be 10 replicas
instead of five.
Well, the current observed state is gonna be out of sync,
with this new desired state,
watch loops will notice,
and controllers will kick into reconcile.
And it's a beautiful thing.
I mean, those YAML files are your source of truth.


And they serve as get this living application documentation.
Sounds cheesy, right?
But it is the absolute business.
We all want decent documentation.
And this type of declarative model, it gives it to us for free, I love it.
You basically define your app and YAML files,
that are great documentation,
then you give those to the cluster and it deploys your apps.
NET NET, your documentation is always up to date.
Hallelujah!
Now, I mean, sure,
you can imperatively configure your apps,
with loads of kubectl commands and maybe some scripts,
but I mean, who the heck wants to do that?
That's the old way.
The cloud native way in the Kubernetes way is declaratively,
with the YAML files.

## API Groups

There's now a bunch of API groups, 

so like all the workload stuff, like deployments, and replica sets and demon sets, and the likes, these are all in the apps API group.
### Background

Anyway, the API itself it used to be a monolith.
So all resources were defined, in a guess what we now call the old core API group.
But monoliths are bad, right? 
And as Kubernetes grew, it was a nightmare trying to develop loads of individual resources, under an umbrella of a single monolithic API.

So they broke it apart. And you'll see as we crack on with the course, that yeah, okay, so all of the our back stuff that's under the authorization group.

## SIG

So lots of groups, each with their own resources.

And each of these API groups, is kind of looked after by a special interest group,
a SIG, which, rather than being linesof code in the cloud somewhere, this is actually a group of people, human beings here that are responsible
for feature development.

So for example, SIG apps, these guys own the apps API, and the pretty much free to do whatever they want in it at their own cadence. 
Any way resources live in API groups yeah?

## Versioning

And each API group is versioned.
New stuff comes in at alpha progresses through beta,
and ends up at GA.
The general rule is pretty much like this.
Alpha features are a bit hairy, right?
And they shouldn't be trusted.
I mean, the disabled by default, and you know what,
they can be dropped at any point.
So use with massive caution.
Beta features, yeah, definitely a step up.
For the most part they're stable-ish,
and they'll probably look the same and they go GA.
And then GA, it's just this confirmation that the feature,
set stable and it's considered ready for production.
And why that probably sounds simple.
Let me tell you it is anything but.

I mean, when you consider how big the Kubernetes API is,
and how fast it's growing,
it is not easy to keep track of things.
For your existing clusters, kubectl,
get API services might be helpful.
But I reckon yeah, that's the API.
Restful, CRUD style operations,
create, read, update, and delete.
We normally post stuff to the API server and YAML,
features are split out into their own API groups.
And new features go through alpha, beta and GA.
Love it, anyway next up,
we'll look at some of the major Kubernetes objects.