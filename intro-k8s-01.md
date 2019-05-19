# Container Orchestration

## Introduction

With container images, we confine the application code, its runtime, and all of its dependencies in a pre-defined format. And, with container runtimes like **runC**, **containerd**, or **rkt** we can use those pre-packaged images, to create one or more containers. All of these runtimes are good at running containers on a single host. But, in practice, we would like to have a fault-tolerant and scalable solution, which can be achieved by creating a single *controller/management unit*, after connecting multiple nodes together. This controller/management unit is generally referred to as a *container orchestrator*.

In this chapter, we will explore why we should use container orchestrators, different implementations of container orchestrators, and where to deploy them.

## Learning Objectives

By the end of this chapter, you should be able to:

- Define the concept of container orchestration.
- Explain the reasons for doing container orchestration.
- Discuss different container orchestration options.
- Discuss different container orchestration deployment options.

## What Are Containers?

Before we dive into container orchestration, let's review first what containers are.

**Containers** are an application-centric way to deliver high-performing, scalable applications on the infrastructure of your choice.

[What are containers?](assets/01-Containers_Updated.png "Containers"){width=608 height=211px}

With a *container image*, we bundle the application along with its runtime and dependencies. We use that image to create an isolated executable environment, also known as container. We can deploy containers from a given image on the platform of our choice, such as desktops, VMs, cloud, etc.

## What Is Container Orchestration?

In the **quality assurance (QA) environments**, we can get away with running containers on a single host to develop and test applications. However, when we go to production, we do not have the same liberty, as we need to ensure that our applications:

- Are fault-tolerant
- Can scale, and do this on-demand
- Use resources optimally
- Can discover other applications automatically, and communicate with each other
- Are accessible from the external world 
- Can update/rollback without any downtime. 

**Container orchestrators** are the tools which group hosts together to form a cluster, and help us fulfill the requirements mentioned above.

## Container Orchestrators

Nowadays, there are many container orchestrators available, such as:

- **Docker Swarm**  
  [Docker Swarm](https://docs.docker.com/engine/swarm/) is a container orchestrator provided by [Docker, Inc](https://www.docker.com/). It is part of [Docker Engine](https://docs.docker.com/engine/).
- **Kubernetes**  
  [Kubernetes](https://kubernetes.io/) was started by Google, but now, it is a part of the [Cloud Native Computing Foundation](https://www.cncf.io/) project.
- **Mesos Marathon**  
  Marathon is one of the frameworks to run containers at scale on [Apache Mesos](http://mesos.apache.org/).
- **Amazon ECS**  
  [Amazon EC2 Container Service](https://aws.amazon.com/ecs/) (ECS) is a hosted service provided by AWS to run Docker containers at scale on its infrastructrue.
- **Hashicorp Nomad**  
  [Nomad](https://www.nomadproject.io/) is the container orchestrator provided by [HashiCorp](https://www.hashicorp.com/).

We have explored different Container Orchestrators in another edX MOOC, _[Introduction to Cloud Infrastructure Technologies](https://www.edx.org/course/introduction-cloud-infrastructure-linuxfoundationx-lfs151-x)_ (LFS151x). We highly recommend that you take LFS151x.

## Why Use Container Orchestrators?

Though we can argue that containers at scale can be maintained manually, or with the help of some scripts, container orchestrators can make things easy for operators.

Container orchestrators can:

- Bring multiple hosts together and make them part of a cluster
- Schedule containers to run on different hosts
- Help containers running on one host reach out to containers running on other hosts in the cluster
- Bind containers and storage
- Bind containers of similar type to a higher-level construct, like services, so we don't have to deal with individual containers
- Keep resource usage in-check, and optimize it when necessary
- Allow secure access to applications running inside containers.

With all these built-in benefits, it makes sense to use container orchestrators to manage containers. In this course, we will explore **Kubernetes**.

## Where to Deploy Container Orchestrators?

Most container orchestrators can be deployed on the infrastructure of our choice. We can deploy them on bare metal, VMs, on-premise, or on a cloud of our choice. For example, Kubernetes can be deployed on our laptop/workstation, inside a company's datacenter, on AWS, on OpenStack, etc. There are even one-click installers available to set up Kubernetes on the cloud, like Google Kubernetes Engine on Google Cloud, or Azure Container Service on Microsoft Azure. Similar solutions are available for other container orchestrators, as well.

There are companies that offer managed Container Orchestration as a Service. We will explore them for Kubernetes in one of the later chapters.

## Learning Objectives (Review)

You should now be able to:

- Define the concept of container orchestration.
- Explain the reasons for doing container orchestration.
- Discuss different container orchestration options.
- Discuss different container orchestration deployment options.
