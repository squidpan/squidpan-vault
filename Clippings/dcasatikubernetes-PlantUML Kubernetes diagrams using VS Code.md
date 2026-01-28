---
title: "dcasati/kubernetes-PlantUML: Kubernetes diagrams using VS Code"
source: https://github.com/dcasati/kubernetes-PlantUML
author:
  - "[[dcasati]]"
published:
created: 2025-10-12
description: Kubernetes diagrams using VS Code. Contribute to dcasati/kubernetes-PlantUML development by creating an account on GitHub.
tags:
  - clippings
categories:
  - "[[Clippings]]"
---
**[kubernetes-PlantUML](https://github.com/dcasati/kubernetes-PlantUML)** Public

Kubernetes diagrams using VS Code

[MIT license](https://github.com/dcasati/kubernetes-PlantUML/blob/master/LICENSE)

[Open in github.dev](https://github.dev/) [Open in a new github.dev tab](https://github.dev/) [Open in codespace](https://github.com/codespaces/new/dcasati/kubernetes-PlantUML?resume=1)

<table><thead><tr><th colspan="2"><span>Name</span></th><th colspan="1"><span>Name</span></th><th><p><span>Last commit message</span></p></th><th colspan="1"><p><span>Last commit date</span></p></th></tr></thead><tbody><tr><td colspan="3"><p><span><a href="https://github.com/dcasati/kubernetes-PlantUML/commit/dee6e17448ddc348a8e5a739419e5b1946f8db53">Update microservices-azure-aks.puml</a></span></p><p><span><a href="https://github.com/dcasati/kubernetes-PlantUML/commit/dee6e17448ddc348a8e5a739419e5b1946f8db53">dee6e17</a> ·</span></p><p><a href="https://github.com/dcasati/kubernetes-PlantUML/commits/master/"><span><span><span>30 Commits</span></span></span></a></p></td></tr><tr><td colspan="2"><p><a href="https://github.com/dcasati/kubernetes-PlantUML/tree/master/dist">dist</a></p></td><td colspan="1"><p><a href="https://github.com/dcasati/kubernetes-PlantUML/tree/master/dist">dist</a></p></td><td><p><a href="https://github.com/dcasati/kubernetes-PlantUML/commit/2ef5ca8768cd26c1b088fe67bda7f2bee5415e1e">s/AZURE/KUBERNETES/g</a></p></td><td></td></tr><tr><td colspan="2"><p><a href="https://github.com/dcasati/kubernetes-PlantUML/tree/master/media">media</a></p></td><td colspan="1"><p><a href="https://github.com/dcasati/kubernetes-PlantUML/tree/master/media">media</a></p></td><td><p><a href="https://github.com/dcasati/kubernetes-PlantUML/commit/6c55dbf53ac5e0bda1fae56ad337114cb9328617">README.md: Synchronize images with included code</a></p></td><td></td></tr><tr><td colspan="2"><p><a href="https://github.com/dcasati/kubernetes-PlantUML/tree/master/samples">samples</a></p></td><td colspan="1"><p><a href="https://github.com/dcasati/kubernetes-PlantUML/tree/master/samples">samples</a></p></td><td><p><a href="https://github.com/dcasati/kubernetes-PlantUML/commit/dee6e17448ddc348a8e5a739419e5b1946f8db53">Update microservices-azure-aks.puml</a></p></td><td></td></tr><tr><td colspan="2"><p><a href="https://github.com/dcasati/kubernetes-PlantUML/blob/master/LICENSE">LICENSE</a></p></td><td colspan="1"><p><a href="https://github.com/dcasati/kubernetes-PlantUML/blob/master/LICENSE">LICENSE</a></p></td><td><p><a href="https://github.com/dcasati/kubernetes-PlantUML/commit/4c0d21ed1655442c6b75205427abf78ea1a9bec8">add reference to Ricardo Niepel, the master of Azure-PlantUML</a></p></td><td></td></tr><tr><td colspan="2"><p><a href="https://github.com/dcasati/kubernetes-PlantUML/blob/master/README.md">README.md</a></p></td><td colspan="1"><p><a href="https://github.com/dcasati/kubernetes-PlantUML/blob/master/README.md">README.md</a></p></td><td><p><a href="https://github.com/dcasati/kubernetes-PlantUML/commit/6c55dbf53ac5e0bda1fae56ad337114cb9328617">README.md: Synchronize images with included code</a></p></td><td></td></tr><tr><td colspan="3"></td></tr></tbody></table>

## Kubernetes-PlantUML

These are the PlantUML sprites, macros and stereotypes for creating PlantUML diagrams with the Kubernetes components. The official Kubernetes Icons Set (where this work is based) can be found [here](https://github.com/kubernetes/community/tree/master/icons)

This repo is heavily influenced by the awesome work from Ricardo Niepel on [Azure-PlantUML](https://github.com/RicardoNiepel/Azure-PlantUML)

[![vscode](https://github.com/dcasati/kubernetes-PlantUML/raw/master/media/vscode.gif)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/media/vscode.gif)

**Table of Contents**

- [Kubernetes-PlantUML](https://github.com/dcasati/#kubernetes-plantuml)
	- [Getting Started](https://github.com/dcasati/#getting-started)
	- [Examples](https://github.com/dcasati/#examples)
	- [Using kubernetes-PlantUML with other PlantUML files](https://github.com/dcasati/#using-kubernetes-plantuml-with-other-plantuml-files)
	- [List of Supported Symbols](https://github.com/dcasati/#list-of-supported-symbols)
	- [Contributing](https://github.com/dcasati/#contributing)
	- [Reference](https://github.com/dcasati/#reference)

## Getting Started

TL;DR - If you're familiar with PlantUML this is what you need:

```
' Kubernetes
!define KubernetesPuml https://raw.githubusercontent.com/dcasati/kubernetes-PlantUML/master/dist

' global definition
!includeurl KubernetesPuml/kubernetes_Common.puml
!includeurl KubernetesPuml/kubernetes_Context.puml
!includeurl KubernetesPuml/kubernetes_Simplified.puml

' k8s specific components
!includeurl KubernetesPuml/OSS/KubernetesPod.puml
!includeurl KubernetesPuml/OSS/KubernetesPsp.puml
!includeurl KubernetesPuml/OSS/KubernetesPv.puml
!includeurl KubernetesPuml/OSS/KubernetesPvc.puml

[...]
```

If you're starting with PlantUML, here's what you need:

1. VS Code with the PlantUML extension [![PlantUML](https://github.com/dcasati/better-diagrams/raw/master/images/plantUML.png)](https://github.com/dcasati/better-diagrams/blob/master/images/plantUML.png)
2. [Graphviz](https://graphviz.gitlab.io/)
3. Copy one of the examples from: [https://github.com/dcasati/kubernetes-PlantUML/tree/master/samples](https://github.com/dcasati/kubernetes-PlantUML/tree/master/samples)

I also have an introduction to PlantUML [here](https://github.com/dcasati/better-diagrams)

## Examples

A basic `hello world` example could look like this:

[![kubernetes](https://github.com/dcasati/kubernetes-PlantUML/raw/master/media/hello-world.png)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/media/hello-world.png)

This picture was rendered with the following code:

A more complete example would look like this picture:

[![more complete example](https://github.com/dcasati/kubernetes-PlantUML/raw/master/media/kubernetes.png)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/media/kubernetes.png)

and the accompaining code:

```
@startuml kubernetes

footer Kubernetes Plant-UML
scale max 1024 width

skinparam nodesep 10
skinparam ranksep 10

' Kubernetes
!define KubernetesPuml https://raw.githubusercontent.com/dcasati/kubernetes-PlantUML/master/dist

!includeurl KubernetesPuml/kubernetes_Common.puml
!includeurl KubernetesPuml/kubernetes_Context.puml
!includeurl KubernetesPuml/kubernetes_Simplified.puml

!includeurl KubernetesPuml/OSS/KubernetesSvc.puml
!includeurl KubernetesPuml/OSS/KubernetesIng.puml
!includeurl KubernetesPuml/OSS/KubernetesPod.puml
!includeurl KubernetesPuml/OSS/KubernetesRs.puml
!includeurl KubernetesPuml/OSS/KubernetesDeploy.puml
!includeurl KubernetesPuml/OSS/KubernetesHpa.puml

actor "User" as userAlias
left to right direction

' Kubernetes Components
Cluster_Boundary(cluster, "Kubernetes Cluster") {
    Namespace_Boundary(ns, "Back End") {
        KubernetesIng(ingress, "your.domain.com", "")
        KubernetesSvc(svc, "service", "")
        KubernetesPod(pod1, "pod1", "")
        KubernetesPod(pod2, "pod2", "")
        KubernetesPod(pod3, "pod3", "")

        KubernetesRs(rs,"","")
        KubernetesDeploy(deploy,"deployment","")
        KubernetesHpa(hpa, "HPA", "")
    }
}

Rel(userAlias,ingress," ")
Rel(ingress,svc," ")

Rel(svc,pod1," ")
Rel(svc,pod2," ")
Rel(svc,pod3," ")

Rel_U(rs,pod1," ")
Rel_U(rs,pod2," ")
Rel_U(rs,pod3," ")

Rel_U(deploy,rs, " ")
Rel_U(hpa,deploy, " ")

@enduml
```

You can certainly mix and match the stencils from kubernetes-PlantUML with other PlantUML files. For instance, here is an example of using it with the Azure-PlantUML files to ilustrate this reference architecture

[![microsoervices-diagram](https://camo.githubusercontent.com/205b2844616c6c923ef6da2a1390fe872ca050153b4dab0d3ecbaf26e599b586/68747470733a2f2f646f63732e6d6963726f736f66742e636f6d2f656e2d75732f617a7572652f6172636869746563747572652f7265666572656e63652d617263686974656374757265732f6d6963726f73657276696365732f5f696d616765732f616b732e706e67)](https://camo.githubusercontent.com/205b2844616c6c923ef6da2a1390fe872ca050153b4dab0d3ecbaf26e599b586/68747470733a2f2f646f63732e6d6963726f736f66742e636f6d2f656e2d75732f617a7572652f6172636869746563747572652f7265666572656e63652d617263686974656374757265732f6d6963726f73657276696365732f5f696d616765732f616b732e706e67)

The equivalent of that in PlantUML would look like this:

[![microservices-plantuml](https://github.com/dcasati/kubernetes-PlantUML/raw/master/media/microservices-azure-aks.png)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/media/microservices-azure-aks.png)

```
@startuml kubernetes

footer Kubernetes Plant-UML
scale max 1024 width

skinparam nodesep 10
skinparam ranksep 10

' Azure
!define AzurePuml https://raw.githubusercontent.com/RicardoNiepel/Azure-PlantUML/release/2-1/dist

!includeurl AzurePuml/AzureCommon.puml
!includeurl AzurePuml/AzureSimplified.puml

!includeurl AzurePuml/Containers/AzureContainerRegistry.puml
!includeurl AzurePuml/Databases/AzureCosmosDb.puml
!includeurl AzurePuml/Databases/AzureSqlDatabase.puml
!includeurl AzurePuml/DevOps/AzurePipelines.puml
!includeurl AzurePuml/Identity/AzureActiveDirectory.puml
!includeurl AzurePuml/Networking/AzureLoadBalancer.puml
!includeurl AzurePuml/Security/AzureKeyVault.puml

' Kubernetes
!define KubernetesPuml https://raw.githubusercontent.com/dcasati/kubernetes-PlantUML/master/dist

!includeurl KubernetesPuml/kubernetes_Common.puml
!includeurl KubernetesPuml/kubernetes_Context.puml
!includeurl KubernetesPuml/kubernetes_Simplified.puml

!includeurl KubernetesPuml/OSS/KubernetesApi.puml
!includeurl KubernetesPuml/OSS/KubernetesIng.puml
!includeurl KubernetesPuml/OSS/KubernetesPod.puml

actor "DevOps" as devopsAlias
collections "Client Apps" as clientalias
collections "Helm Charts" as helmalias

left to right direction

' Azure Components
AzureActiveDirectory(aad, "\nAzure\nActive Directory", "Global")
AzureContainerRegistry(acr, "ACR", "Canada Central")
AzureCosmosDb(cosmos, "\nCosmos DB", "Global")
AzureKeyVault(keyvault, "\nAzure\nKey Vault", "Global")
AzureLoadBalancer(alb, "\nLoad\nBalancer", "Canada Central")
AzureSqlDatabase(sql, "\nExternal\ndata stores", "Canada Central")
AzurePipelines(ado, "CI/CD\nAzure Pipelines", "Global")

' Kubernetes Components
Cluster_Boundary(cluster, "Kubernetes Cluster") {
    KubernetesApi(KubernetesApi, "Kubernetes API", "")

    Namespace_Boundary(nsFrontEnd, "Front End") {
        KubernetesIng(ingress, "API Gateway", "")
    }

    Namespace_Boundary(nsBackEnd, "Back End") {
        KubernetesPod(KubernetesBE1, "", "")
        KubernetesPod(KubernetesBE2, "", "")
        KubernetesPod(KubernetesBE3, "", "")
    }

    Namespace_Boundary(nsUtil, "Utiliy Services") {
        KubernetesPod(KubernetesUtil1, "", "")
        KubernetesPod(KubernetesUtil2, "","")
    }
}

Rel(devopsAlias, aad, "AUTH")
Rel(helmalias, KubernetesApi, "helm upgrade")

Rel(aad, keyvault, " ")
Rel(KubernetesApi, aad, "RBAC", "ASYNC")

Rel(clientalias, alb, "HTTP", "ASYNC")
Rel(alb, ingress, "HTTP", "ASYNC")

Rel(ingress, KubernetesBE1, " ")
Rel(KubernetesBE1, KubernetesBE2, " ")
Rel(KubernetesBE1, KubernetesBE3, " ")

Rel(KubernetesBE2, sql, " ")
Rel(KubernetesBE3, keyvault, "Pod Identity")
Rel(KubernetesBE3, cosmos, " ")

Rel(ado, acr, "docker push")
Rel_U(KubernetesApi, acr, "docker pull")
@enduml
```

| Category | Macro (Name) | ``` Mono ``` | Url |
| --- | --- | --- | --- |
| **OSS** |  |  |  |
| OSS | KubernetesCronjob   (Kubernetes Cronjob) | [![KubernetesCronjob](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesCronjob(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesCronjob\(m\).png?raw=true) | OSS/KubernetesCronjob.puml |
| OSS | KubernetesGroup   (Kubernetes Group) | [![KubernetesGroup](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesGroup(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesGroup\(m\).png?raw=true) | OSS/KubernetesGroup.puml |
| OSS | KubernetesPsp   (Kubernetes Psp) | [![KubernetesPsp](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesPsp(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesPsp\(m\).png?raw=true) | OSS/KubernetesPsp.puml |
| OSS | KubernetesRole   (Kubernetes Role) | [![KubernetesRole](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesRole(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesRole\(m\).png?raw=true) | OSS/KubernetesRole.puml |
| OSS | KubernetesApi   (Kubernetes Api) | [![KubernetesApi](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesApi(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesApi\(m\).png?raw=true) | OSS/KubernetesApi.puml |
| OSS | KubernetesJob   (Kubernetes Job) | [![KubernetesJob](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesJob(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesJob\(m\).png?raw=true) | OSS/KubernetesJob.puml |
| OSS | KubernetesCm   (Kubernetes Cm) | [![KubernetesCm](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesCm(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesCm\(m\).png?raw=true) | OSS/KubernetesCm.puml |
| OSS | KubernetesMaster   (Kubernetes Master) | [![KubernetesMaster](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesMaster(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesMaster\(m\).png?raw=true) | OSS/KubernetesMaster.puml |
| OSS | KubernetesKproxy   (Kubernetes Kproxy) | [![KubernetesKproxy](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesKproxy(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesKproxy\(m\).png?raw=true) | OSS/KubernetesKproxy.puml |
| OSS | KubernetesCrd   (Kubernetes Crd) | [![KubernetesCrd](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesCrd(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesCrd\(m\).png?raw=true) | OSS/KubernetesCrd.puml |
| OSS | KubernetesDs   (Kubernetes Ds) | [![KubernetesDs](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesDs(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesDs\(m\).png?raw=true) | OSS/KubernetesDs.puml |
| OSS | KubernetesSc   (Kubernetes Sc) | [![KubernetesSc](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesSc(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesSc\(m\).png?raw=true) | OSS/KubernetesSc.puml |
| OSS | KubernetesCrb   (Kubernetes Crb) | [![KubernetesCrb](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesCrb(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesCrb\(m\).png?raw=true) | OSS/KubernetesCrb.puml |
| OSS | KubernetesSched   (Kubernetes Sched) | [![KubernetesSched](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesSched(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesSched\(m\).png?raw=true) | OSS/KubernetesSched.puml |
| OSS | KubernetesLimits   (Kubernetes Limits) | [![KubernetesLimits](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesLimits(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesLimits\(m\).png?raw=true) | OSS/KubernetesLimits.puml |
| OSS | KubernetesQuota   (Kubernetes Quota) | [![KubernetesQuota](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesQuota(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesQuota\(m\).png?raw=true) | OSS/KubernetesQuota.puml |
| OSS | KubernetesVol   (Kubernetes Vol) | [![KubernetesVol](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesVol(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesVol\(m\).png?raw=true) | OSS/KubernetesVol.puml |
| OSS | KubernetesSa   (Kubernetes Sa) | [![KubernetesSa](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesSa(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesSa\(m\).png?raw=true) | OSS/KubernetesSa.puml |
| OSS | KubernetesKubelet   (Kubernetes Kubelet) | [![KubernetesKubelet](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesKubelet(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesKubelet\(m\).png?raw=true) | OSS/KubernetesKubelet.puml |
| OSS | KubernetesPvc   (Kubernetes Pvc) | [![KubernetesPvc](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesPvc(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesPvc\(m\).png?raw=true) | OSS/KubernetesPvc.puml |
| OSS | KubernetesCcm   (Kubernetes Ccm) | [![KubernetesCcm](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesCcm(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesCcm\(m\).png?raw=true) | OSS/KubernetesCcm.puml |
| OSS | KubernetesSts   (Kubernetes Sts) | [![KubernetesSts](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesSts(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesSts\(m\).png?raw=true) | OSS/KubernetesSts.puml |
| OSS | KubernetesNetpol   (Kubernetes Netpol) | [![KubernetesNetpol](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesNetpol(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesNetpol\(m\).png?raw=true) | OSS/KubernetesNetpol.puml |
| OSS | KubernetesCrole   (Kubernetes Crole) | [![KubernetesCrole](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesCrole(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesCrole\(m\).png?raw=true) | OSS/KubernetesCrole.puml |
| OSS | KubernetesRs   (Kubernetes Rs) | [![KubernetesRs](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesRs(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesRs\(m\).png?raw=true) | OSS/KubernetesRs.puml |
| OSS | KubernetesNode   (Kubernetes Node) | [![KubernetesNode](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesNode(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesNode\(m\).png?raw=true) | OSS/KubernetesNode.puml |
| OSS | KubernetesSecret   (Kubernetes Secret) | [![KubernetesSecret](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesSecret(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesSecret\(m\).png?raw=true) | OSS/KubernetesSecret.puml |
| OSS | KubernetesNs   (Kubernetes Ns) | [![KubernetesNs](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesNs(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesNs\(m\).png?raw=true) | OSS/KubernetesNs.puml |
| OSS | KubernetesDeploy   (Kubernetes Deploy) | [![KubernetesDeploy](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesDeploy(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesDeploy\(m\).png?raw=true) | OSS/KubernetesDeploy.puml |
| OSS | KubernetesUser   (Kubernetes User) | [![KubernetesUser](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesUser(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesUser\(m\).png?raw=true) | OSS/KubernetesUser.puml |
| OSS | KubernetesPv   (Kubernetes Pv) | [![KubernetesPv](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesPv(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesPv\(m\).png?raw=true) | OSS/KubernetesPv.puml |
| OSS | KubernetesEp   (Kubernetes Ep) | [![KubernetesEp](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesEp(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesEp\(m\).png?raw=true) | OSS/KubernetesEp.puml |
| OSS | KubernetesSvc   (Kubernetes Svc) | [![KubernetesSvc](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesSvc(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesSvc\(m\).png?raw=true) | OSS/KubernetesSvc.puml |
| OSS | KubernetesRb   (Kubernetes Rb) | [![KubernetesRb](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesRb(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesRb\(m\).png?raw=true) | OSS/KubernetesRb.puml |
| OSS | KubernetesEtcd   (Kubernetes Etcd) | [![KubernetesEtcd](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesEtcd(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesEtcd\(m\).png?raw=true) | OSS/KubernetesEtcd.puml |
| OSS | KubernetesIng   (Kubernetes Ing) | [![KubernetesIng](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesIng(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesIng\(m\).png?raw=true) | OSS/KubernetesIng.puml |
| OSS | KubernetesHpa   (Kubernetes Hpa) | [![KubernetesHpa](https://github.com/dcasati/kubernetes-PlantUML/raw/master/dist/OSS/KubernetesHpa(m).png?raw=true)](https://github.com/dcasati/kubernetes-PlantUML/blob/master/dist/OSS/KubernetesHpa\(m\).png?raw=true) | OSS/KubernetesHpa.puml |

## Contributing

I've built this on a necessity that I have for making better diagrams when Kubernetes is part of the solution. This is based on a community effort and as such this should belong to the Kubernetes community. Feel free to fork and to submit PRs.

## Reference

None of the work here would be possible without the foundation from Ricardo Niepel, PlantUML and the C4 Model

- Ricardo Niepel - [Azure-PlantUML](https://github.com/RicardoNiepel/Azure-PlantUML)
- C4 Model - [https://c4model.com](https://c4model.com/)

## Releases

No releases published

## Packages

No packages published