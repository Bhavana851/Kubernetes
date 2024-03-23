# Basics of Pod

- The containers are encapsulated into a Kubernetes objectknown as PODs. A POD is a single instance of an application. 
- A POD is the smallest object, that you can create in kubernetes.

![P](https://res.cloudinary.com/practicaldev/image/fetch/s--nAI7sn-8--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/uq0dizyr4ohbo7cs5k5h.png)

Let's see a situation:
- here is a Single node kubernetes cluster with a pod inside it. The container is encapsulated by the pod.


![PC](https://res.cloudinary.com/practicaldev/image/fetch/s--Qwk4gqMM--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5ib8k10cy8vasmmhvfa5.png)

- When we have more people and need additional applications , we need to increase our containers.

[KC](https://res.cloudinary.com/practicaldev/image/fetch/s--6iYFq9BN--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9ozi23w4fyfnh9qdrnn9.png)

![Kc](https://res.cloudinary.com/practicaldev/image/fetch/s--hXH_kTk8--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/pa7zsyh8byr1aveabnnn.png)

- We will node create containers within a pod, rather we will create a new pod with the same application (container)

- If your node does not have sufficient capacity, you can add new node with a pod

![](https://res.cloudinary.com/practicaldev/image/fetch/s--HkeXeX-5--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ha48s3mbg3dywa20qvzn.png)

- There can be multiple containers in a pod:
- A single POD CAN have multiple containers, except for the fact that they are usually not multiple containers of the same kind.








