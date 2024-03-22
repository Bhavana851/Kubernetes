## Kubernetes: 

Kubernetes is an **Open source container Orchestration platform it automates the depolyment,scaling,**and management containerized applications.
Kubernetes can be traced back to googles internal container orchestration system

![Kubernetes k8s](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F879617e5-c870-4258-97b1-8dfac6e232e1_2796x3816.jpeg)

## Problem does kubernetes solve 

Kubernetes addresses several challenges associated with deploying and managing containerized applications in a 
distributed environment ,Here are some key problems that kubernetes

**1.Container Orchestration**

**2.Declarative configuration** 

**3.Scalability**

**4.Fault Tolerance and High Availability**

**5.Service discovery and Load Balancing** 

**6.Rooling updates and roolbacks**

## Kubernetes architecture 

Kubernetes architecture consist of two main components 

**1.Master Node (Control plane)**

**2.Worker Node**

**Feature of Master node** 

Manages the entire cluster and is crucial for cluster wide decisions

**Feature of worker Node** 

Receives instructions from the control plane and manages local execution of the workloads

**Master Node** 

* Centralized Control plane,Manages the entire cluster.

* Key components include the API server,control manager,Scheduler and etcd.

**Worker Node** 

Execute the actual workloads,Host the containers that run application 

components on worker Load that include the Kubelet,kube-proxy and container Runtime(eg:Docker)





