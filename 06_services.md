Services Exercise 

# Services - 1
Introduction: Let us start with Services! Given a service-definition.yml file. We are only getting started with it, so let's get it populated. 

Instruction: Add all the root level properties to it. Note: Only add the properties, not any values.

service-definition.yml
```
- apiVersion:
  kind:
  metadata:
  spec:

```
# Services - 2
Introduction: Let us now add values for Service. Service is under apiVersion v1 

Instruction: Update values for apiVersion and kind

```
- apiVersion: v1
  kind: Service
  metadata:
  spec:
```
# Services - 3
Introduction: Let us now add values for metadata. 

Instruction: Add a name for the service = frontend and a label = app=>myapp

```
- apiVersion: v1
  kind: Service
  metadata:
    name: frontend
    labels:
      app: myapp
  spec:

```
# Services - 4
Introduction: Let us now add values for spec section. The spec section for Services have type, selector and ports. 

Instruction: Add properties under spec section - type, selector and ports. Do not add any values for them.

```
- apiVersion: v1
  kind: Service
  metadata:
    name: frontend
    labels:
      app: myapp
  spec:
    type:
    selector:
    ports:
``` 
# Services - 5
Introduction: Let us now add values for ports. Ports is an Array/ List. Each item in the list has a set of properties - port and targetPort 

Instruction: Create an Array/List item under ports. Add a dictionary with properties port and targetPort. Set values for both to port 80. 

Note: We will not be providing a NodePort as we would like Kubernetes to assign one automatically for us.

```
- apiVersion: v1
  kind: Service
  metadata:
    name: frontend
    labels:
      app: myapp
  spec:
    type:
    ports:
      - port: 80
        targetPort: 80
    selector:
```
# Services - 6
Introduction: Let us now add values for type. Since we are creating a frontend service for enabling external access to users, we will set it to Node Port. 

Instruction: Set value for type to NodePort.


```
- apiVersion: v1
  kind: Service
  metadata:
    name: frontend
    labels:
      app: myapp
  spec:
    type: NodePort
    ports:
      - port: 80
        targetPort: 80
    selector:
```

# Services - 7
Introduction: Let us now add values for selector. We need to link the Service to the PODs created by the deployment. 

Instruction: Given the deployment-definition.yml file we created in the previous Section. Copy the appropriate labels and paste it under selector section of service-definition.yml file.

service-definition.yml
```
- apiVersion: v1
  kind: Service
  metadata:
    name: frontend
    labels:
      app: myapp
  spec:
    type: NodePort
    ports:
      - port: 80
        targetPort: 80
  selector:
    app: myapp

```
deployment-definition.yml

```
- apiVersion: apps/v1
  kind: Deployment
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
# Services - 8
Introduction: Let us now try to create a service-definition.yml file from scratch. This time all in one go. You are tasked to create a service to enable the frontend pods to access a backend set of Pods. 

Instruction: Use the information provided in the below table to create a backend service definition file. Refer to the provided deployment-definition file for information regarding the PODs. 

- Service Name: image-processing 
- labels: app=> myapp 
- type: ClusterIP 
- Port on the service: 80 
- Port exposed by image processing container: 8080

service-definition.yml
```
 - apiVersion: v1
   kind: Service
   metadata:
     name: image-processing
     labels:
       app: myapp
   spec:
     # type: ClusterIP
     ports:
      - port: 80
        targetPort: 8080
     selector:
       tier: backend
```
deployment-definition.yml

```
- apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: image-processing-deployment
    labels:
      tier: backend
  spec:
    replicas: 4
    template:
      metadata:
        name: image-processing-pod
        labels:
        tier: backend
      spec:
        containers:
          - name: mycustom-image-processing
            image: someorg/mycustom-image-processing
     selector:
       matchLabels:
         tier: backend

```









