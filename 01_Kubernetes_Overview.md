# Kubernetes_Overview

 # 1. Container, what is a container and why is it needed?

- In the past, when multiple apps were uploaded to a server, 
- there were many issues because the OS or library versions compatible with each app were different.

  ![Containers](https://blog.kakaocdn.net/dn/rvShh/btrgDVjjzkN/XPDalI32LknwSdP6QD50fk/img.png)


# 2. what is Orchestration?

- Assume that you have placed apps in a container. But how do we implement this?

- What if a specific app (ex. messaging app, DB, backend service..) needs to depend on another container?

- And what should I do if I need to increase or decrease containers? 

 - Resources and platform are required to enable these functions. 
 - This platform must orchestrate connectivity and scale up/down between containers, and the overall process of managing and 
     automatically deploying containers is Container Orchestration .

 # Kubernetics (K8s) is a container orchestration technology,  

   - Supports all public cloud services (ex. GCP, Azure, AWS, etc.).

# Container orchestration has various advantages.

- Apps become highly avalable. 

  why? Because apps run on different nodes (because they have multiple instances),

  hw dependency disappears.

- Load balance is also possible (since it is a cluster configuration),

- Nodes can be scaled in/out automatically depending on the load of the nodes. 

# 3. Kubernetes Architecture

![KA](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdiaXoj%2FbtrgDVwWDsA%2FMXkFIpcCP6TLkLoRGg1OZk%2Fimg.png)

# 1) Node (=minion): 

- The physical or virtual machine itself where K8s is installed.

- A node is a worker machine, and a container is installed by k8s. In the past, it was also called Minion. 

Here, what happens if the Node where our app is installed dies? If there is only 1 node, it will die.

 

# 2) Cluster: 

- Composition between nodes

- What if there are multiple Nodes as shown in the picture?

Even if one app dies, it can still be accessible through other nodes. This also allows load balancing

![M](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fsbotl%2FbtrgDT0bXnF%2FrRj2jVwTn8InvVv83FQrA0%2Fimg.png)

But, where do we manage these nodes?

# 3) Master: 
- Manages clusters, stores information, monitors, load balances, and performs fail-over operations. 


# 4. Other various components

![C](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbDhS7a%2FbtrgRM5Ohg0%2FIrVLkJg9jXTjPf1kWXJNK1%2Fimg.png)

# - API server
-  acts as the front-end for kubernetes.
-  The users, management devices, Command line interfaces all talk to the API server to interact with the Kubernetes cluster.
-   => FE of k8s, the entrance to communicate with the cluster.

# - ETCD
- is a distributed reliable key-value store used by kubernetes to store all data used to manage the cluster.
- Think of it this way, when you have multiple nodes and multiple masters in your cluster, etcd stores all that information on all the nodes in the cluster in a distributed manner.
-  ETCD is responsible for implementing locks within the cluster to ensure there are no conflicts between the Masters.
-   => Entire data store

# - scheduler
- is responsible for distributing work or containers across multiple nodes.
- It looks for newly created containers and assigns them to Nodes.
- => load balancing

# - controllers 
- are the brain behind orchestration.
- They are responsible for notifying and responding when nodes, containers or endpoints go down.
- The controllers make decisions to bring up new containers in such cases.
-  => Brain. This is where you are notified when a container or end stage goes down and decide whether to launch a new container.

# - container 
- runtime is the underlying software that is used to run containers.
- In our case it happens to be Docker. And finally kubelet is the agent that runs on each node in the cluster.
- The agent is responsible for making sure that the containers are running on the nodes as expected
- => SW is for launching the container, and kubelet is the agent for launching each node.









