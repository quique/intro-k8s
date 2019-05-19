# Kubernetes

## Introduction

In this chapter, we will explain what **Kubernetes** is, its features, and the reasons why one should use it. We will explore the evolution of Kubernetes from **Borg**, which is a cluster manager created by Google.

We will also talk about the **Cloud Native Computing Foundation (CNCF)**, which currently hosts the Kubernetes project, along with other cloud-native projects, like Prometheus, Fluentd, rkt, containerd, etc.

## Learning Objectives

By the end of this chapter, you should be able to:

- Define Kubernetes.
- Explain the reasons for using Kubernetes.
- Discuss the features of Kubernetes.
- Discuss the evolution of Kubernetes from Borg.
- Explain what the Cloud Native Computing Foundation does.

## What Is Kubernetes?

According to the Kubernetes website,

> "Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications."

**Kubernetes** comes from the Greek word <!-- **&kappa;&upsilon;&beta;&epsilon;&rho;&nu;ή&tau;&eta;&sigmaf;**:, --> which means _helmsman_ or _ship pilot_. With this analogy in mind, we can think of Kubernetes as the manager for shipping containers.

Kubernetes is also referred to as **k8s**, as there are 8 characters between _k_ and _s_.

Kubernetes is highly inspired by the Google Borg system, which we will explore in this chapter. It is an open source project written in the Go language, and licensed under the [Apache License Version 2.0](https://www.apache.org/licenses/LICENSE-2.0).

Kubernetes was started by Google and, with its v1.0 release in July 2015, Google donated it to the [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF). We will talk more about CNCF later in this chapter.

Generally, Kubernetes has new releases every three months. The current stable version is 1.9 (as of February 2018).

## From Borg to Kubernetes

According to the abstract of Google's [Borg paper](https://research.google.com/pubs/pub43438.html), published in 2015,

> "Google's Borg system is a cluster manager that runs hundreds of thousands of jobs, from many thousands of different applications, across a number of clusters each with up to tens of thousands of machines."

For more than a decade, Borg was Google's secret to run containerized workloads in production. Whatever services we use from Google, like Gmail, Drive, etc., they are all serviced using Borg.

Some of the initial authors of Kubernetes were Google employees who have used Borg and developed it in the past. They poured in their valuable knowledge and experience while designing Kubernetes. Some of the features/objects of Kubernetes that can be traced back to Borg, or to lessons learnt from it, are:

- API servers
- Pods
- IP-per-Pod
- Services
- Labels.

We will explore all of them, and more, in this course.

## Kubernetes Features

Kubernetes offers a very rich set of features for container orchestration. Some of its fully supported features are:

- **Automatic binpacking**  
  Kubernetes automatically schedules the containers based on resource usage and constraints, without sacrificing the availability.
- **Self-healing**  
  Kubernetes automatically replaces and reschedules the containers from failed nodes. It also kills and restarts the containers which do not respond to health checks, based on existing rules/policy.
- **Horizontal scaling**  
  Kubernetes can automatically scale applications based on resource usage like CPU and memory. In some cases, it also supports dynamic scaling based on customer metrics.
- **Service discovery and Load balancing**
  Kubernetes groups sets of containers and refers to them via a Domain Name System (DNS). This DNS is also called a Kubernetes **service**. Kubernetes can discover these services automatically, and load-balance requests between containers of a given service.

Some other fully supported Kubernetes features are:

- **Automated rollouts and rollbacks**  
  Kubernetes can roll out and roll back new versions/configurations of an application, without introducing any downtime.
- **Secrets and configuration management**  
  Kubernetes can manage secrets and configuration details for an application without re-building the respective images. With secrets, we can share confidential information to our application without exposing it to the stack configuration, like on GitHub.
- **Storage orchestration**  
  With Kubernetes and its plugins, we can automatically mount local, external, and storage solutions to the containers in a seamless manner, based on software-defined storage (SDS).
- **Batch execution**  
  Besides long running jobs, Kubernetes also supports batch execution.

There are many other features besides the ones we just mentioned, and they are currently in alpha/beta phase. They will add great value to any Kubernetes deployment once they become stable features. For example, support for role-based access control (RBAC) is stable as of the Kubernetes 1.8 release.

## Why Use Kubernetes?

We just looked at some of the fully-supported Kubernetes features. We should also mention that Kubernetes is very portable and extensible. Kubernetes can be deployed on the environment of our choice, be it VMs, bare metal, or public/private/hybrid/multi-cloud setups. Also, Kubernetes has a very modular and pluggable architecture. We can write custom APIs or plugins to extend its functionalities.

For a successful open source project, the community is as important as having great code. Kubernetes has a very thriving community across the world. It has more than 1600 contributors, who, over time, have done over 62,000 commits. There are meet-up groups in different cities which meet regularly to discuss Kubernetes and its ecosystem. There are _Special Interest Groups_ (SIGs), which focus on special interests, such as scaling, bare metal, networking, etc. We will talk more about them in our last chapter, _Kubernetes Communities_.

## Kubernetes Users

With just a few years since its debut, many companies are running workloads using Kubernetes. We can find numerous user case studies on the Kubernetes website:

- [Pearson](https://kubernetes.io/case-studies/pearson/)
- [Box](https://blog.box.com/blog/kubernetes-box-microservices-maximum-velocity/)
- [eBay](https://www.nextplatform.com/2015/11/12/inside-ebays-shift-to-kubernetes-and-containers-atop-openstack/)
- [Wikimedia](https://www.youtube.com/watch?v=6XGUTu3WhBw)
- [Huawei](https://kubernetes.io/case-studies/huawei/)
- [Haufe Group](https://kubernetes.io/case-studies/haufegroup/)
- [BlackRock](https://kubernetes.io/case-studies/blackrock/)
- [BlaBlaCar](https://kubernetes.io/case-studies/blablacar/)
- [And many more.

## Cloud Native Computing Foundation (CNCF)

The [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF) is one of the projects hosted by [The Linux Foundation](https://www.linuxfoundation.org/). CNCF aims to accelerate the adoption of containers, microservices, and cloud-native applications.

![CNCF logo](assets/02-logo_cncf.png)

CNCF hosts a set of projects, with more to be added in the future. CNCF provides resources to each of the projects, but, at the same time, each project continues to operate independently under its pre-existing governance structure and with its existing maintainers. At the time this course was created, the following projects were part of CNCF:

- [containerd](http://containerd.io/) for container runtime
- [rkt](https://github.com/rkt/rkt) for container runtime
- [Kubernetes](https://kubernetes.io/) for container orchestration
- [Linkerd](https://linkerd.io/) for service mesh
- [Envoy](https://github.com/envoyproxy/envoy) for service mesh
- [gRPC](http://www.grpc.io/) for remote procedure call (RPC)
- [Container Network Interface](https://github.com/containernetworking/cni) (CNI) for networking API
- [CoreDNS](https://coredns.io/) for service discovery
- [Rook](https://github.com/rook/rook) for cloud-native storage
- [Notary](https://github.com/theupdateframework/notary) for security
- [The Update Framework](https://github.com/theupdateframework/specification) (TUF) for software updates
- [Prometheus](https://prometheus.io/) for monitoring
- [OpenTracing](http://opentracing.io/) for tracing
- [Jaeger](https://github.com/jaegertracing/jaeger) for distributed tracing
- [Fluentd](http://www.fluentd.org/) for logging
- [Vitess](http://vitess.io/) for storage.

As we can see, this set of CNCF projects can cover the entire lifecycle of an application, from its execution using container runtimes, to its monitoring and logging. This is very important to meet the CNCF goal.

## CNCF and Kubernetes

For Kubernetes, the Cloud Native Computing Foundation:

- Provides a neutral home for the Kubernetes trademark and enforces proper usage
- Provides license scanning of core and vendored code
- Offers legal guidance on patent and copyright issues
- Creates open source [curriculum](https://github.com/cncf/curriculum), [training](https://training.linuxfoundation.org/linux-courses/system-administration-training/kubernetes-fundamentals), and [certification](https://www.cncf.io/certification/expert/)
- Manages a software conformance [working group](https://ponymail.cncf.io/thread.html/Zaw9xi4cg7fx9v6)
- Actively markets Kubernetes
- Hosts and funds developer marketing activities like [K8Sport](http://k8sport.org/)
- Supports ad hoc activities
- Funds conferences and meetup events.

## Learning Objectives (Review)

You should now be able to:

- Define Kubernetes.
- Explain the reasons for using Kubernetes.
- Discuss the features of Kubernetes.
- Discuss the evolution of Kubernetes from Borg.
- Explain what the Cloud Native Computing Foundation does.
