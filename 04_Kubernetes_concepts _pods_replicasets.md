
# YAML Exercise 

# Pods - 1
Introduction: Let us start simple! Given a pod-definition.yml file. We are only getting started with it. I have added two root level properties - apiVersion and kind

```
- apiVersion: 
  kind: 
  metadata:
  spec:

```

# Pods - 2
Introduction: Let us now populate values for each property. Start with apiVersion. 
Instruction: Update value of apiVersion to v1. Remember to add a space between colon (:) and the value (v1)

```
  - apiVersion: v1 
    kind:
    metadata:
    spec:
```

# Pods - 3
Instruction: Update value of kind to Pod.

```
   - apiVersion: v1
     kind: Pod  
     metadata:
     spec:
```

# Pods - 4

Introduction: Let us now get to the metadata section. 

Instruction: Add a property "name" under metadata with value "myapp-pod". Remember to add a space before 'name' to make it a child of metadata


```
- apiVersion: v1
  kind: Pod
  metadata: 
    name: myapp-pod
  spec:
```

# Pods - 5
Introduction: Let us add some labels to our Pod 

Instruction: Add a property "labels" under metadata with a child property "app" with a value "myapp". Remember to have equal number of spaces before "name" and "labels" so they are siblings

```
- apiVersion: v1
  kind: Pod
  metadata:
    name: myapp-pod
    labels:
      app: myapp
  spec:

```
# Pods - 6
Introduction: We now need to provide information regarding the docker image we plan to use. 

Instruction: Add a property containers under spec section. Do not add anything under it yet.

```
 - apiVersion: v1
   kind: Pod
   metadata:
     name: myapp-pod
     labels:
       app: myapp
   spec:
     containers:

```
# Pods - 7
Instruction: Containers is an array/list. So create the first element/item in the array/list and add the following properties to it: name - nginx and image - nginx

```
- apiVersion: v1
  kind: Pod
  metadata:
    name: myapp-pod
    labels:
      app: myapp
  spec:
    containers:
      - name: nginx
        image: nginx

```

# Pods - 8
Introduction: Perfect! You have successfully created a Kubernetes-Definition file. Let us try it one more time, this time all on your own! 

Instruction: Create a Kubernetes Pod definition file using values below: 

- Name: postgres 
- Labels: tier => db-tier
- Container name: postgres
- Image: postgres


```
- apiVersion: v1
  kind: Pod
  metadata:
    name: postgres
    labels: 
      tier: db-tier
  spec:
    containers:
      - name: postgres
        image: postgres

```

# Pods - 9
Introduction: Postgres Docker image requires an environment variable to be set for password.  

Instruction: Set an environment variable for the docker container. POSTGRES_PASSWORD with a value mysecretpassword. I know we haven't discussed this in the lecture, but it is easy. To pass in an environment variable add a new property 'env' to the container object. It is a sibling of image and name. env is an array/list. So add a new item under it. The item will have properties name and value. name should be the name of the environment variable - POSTGRES_PASSWORD. And value should be the password - mysecretpassword

```

-  apiVersion: v1
   kind: Pod
   metadata:
     name: postgres
     labels:
       tier: db-tier
   spec:
     containers:
       - name: postgres
         image: postgres
         env:
           - name: POSTGRES_PASSWORD
             value: mysecretpassword
```

# Replication Controllers and ReplicaSets Exercise 


# ReplicaSet - 1

Introduction: Let us start with ReplicaSets! Given a blank replicaset-definition.yml file. We are only getting started with it, so let's get it populated. 

Instruction: Add all the root level properties to it. 

Note: Only add the properties, not any values yet.

```
- apiVersion:
  kind:
  metadata:
  spec:

```

# ReplicaSet - 2
Introduction: Let us now add values for ReplicaSet. ReplicaSet is under apiVersion - apps/v1 

Instruction: Update values for apiVersion and kind

```
- apiVersion: apps/v1
  kind: ReplicaSet
  metadata:
  spec:
```

# ReplicaSet - 3
Introduction: Let us now add values for metadata 

Instruction: Name the ReplicaSet - frontend. And add labels app=>mywebsite and tier=> frontend

```
- apiVersion: apps/v1
  kind: ReplicaSet
  metadata:
    name: frontend
    labels:
      app: mywebsite
      tier: frontend
   spec:
```

# ReplicaSet - 4
Introduction: Let us now get to the specification 

Instruction: The spec section for ReplicaSet has 3 fields: replicas, template and selector. Simply add these properties. Do not add any values yet.

```
- apiVersion: apps/v1
  kind: ReplicaSet
  metadata:
    name: frontend
    labels:
      app: mywebsite
      tier: frontend
  spec:
    replicas:
    template:
    selector:
```
# ReplicaSet - 5
Instruction: Let us update the number of replicas to 4.

```
- apiVersion: apps/v1
  kind: ReplicaSet
  metadata:
    name: frontend
    labels:
      app: mywebsite
      tier: frontend
  spec:
    replicas: 4
    template:
    selector:

```

# ReplicaSet - 6
Introduction: The template section expects a Pod definition. Luckily, we have the one we created in the previous set of exercises. Next to the replicaset-definition.yml you will now find the same pod-definition.yml file that you created before. 

Instruction: Let us now copy the contents of the pod-definition.yml file, except for the apiVersion and kind and place it under the template section. Take extra care on moving the contents to the right so it falls under template.

replicaset-definition.yml

```
- apiVersion: apps/v1
  kind: ReplicaSet
  metadata:
    name: frontend
    labels:
      app: mywebsite
      tier: frontend
  spec:
    replicas: 4
    template:
      metadata:
        name: myapp-pod
        labels:
          app: myapp
      spec:
        containers:
          - name: nginx
            image: nginx
    selector:


```

pod-definition.ymal

```
- apiVersion: v1
  kind: Pod
  metadata:
    name: myapp-pod
    labels:
      app: myapp
  spec:
    containers:
      - name: nginx
        image: nginx
```

# ReplicaSet - 7
Introduction: Let us now link the pods to the ReplicaSet by updating selectors. 

Instruction: Add a property "matchLabels" under selector and copy the labels defined in the pod-definition under it. 

Note: This may not work in play-with-k8s as it runs on 1.8 version of kubernetes. ReplicaSets moved to apps/v1 in 1.9 version of Kubernetes.

replicaset-definition-yml
```
- apiVersion: apps/v1
  kind: ReplicaSet
  metadata:
    name: frontend
    labels:
      app: mywebsite
      tier: frontend
  spec:
    replicas: 4
    template:
   metadata:
      name: myapp-pod
      labels:
        app: myapp
    spec:
      containers:
        - name: nginx
          image: nginx
    selector:
       matchLabels:
       app: myapp
```
pod-definition-yml

```
- apiVersion: v1
  kind: Pod
  metadata:
    name: myapp-pod
    labels:
      app: myapp
   spec:
     containers:
       - name: nginx
         image: nginx

```









