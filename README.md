# Kubernetes deployment on minikube

The repository you're in currently contains files written in YAML format that can be used to set up and run a MongoDB database on a local Kubernetes cluster using Minikube. Minikube allows you to test and experiment with Kubernetes without the need for a remote cluster. The YAML files in the repository contains the instructions and parameters that are needed to create the resources required to run a MongoDB database on Minikube. These files will be used to create and configure the MongoDB pod and its services.

requirements:
1. Minikube must be installed on your system.
2. kubectl must be installed on your system.
3. A hypervisor, such as VirtualBox, hyperkit, KVM, etc. must be installed on your system.

we will be using hyperkit as hypervisor in this example

### Steps to deploy mongodb on minikube:

1. Create a secret for the MongoDB database.
2. Create a MongoDB pod.
3. Create an internal service to connect the pod to the MongoDB database.
4. Create a configmap to store the MongoDB URL.
5. Create a Mongo Express pod, which is a web-based tool to interact with MongoDB.
6. Create an external service for the Mongo Express to make it accessible from outside the cluster.

### Note
Before proceeding to the next step in the process of deploying a MongoDB database on Minikube, it is important to ensure that there are no errors in the previous command. This means that you should verify that the previous command has completed successfully before moving on to the next one, to avoid any potential issues or errors.

### Commands to deploy mongodb on minikube:
1. Start minikube
Only to start and for stopping you will use minikube at start and all for other works you will use kubectl

```
minikube start --vm-driver=hyperkit
```

2. Create a secret for mongodb
You are creating some secret variable to store the mongodb username and password
```
kubectl apply -f secret.yaml
```

3. Create mongodb deployment
This file contains the deployment configuration for mongodb and it's services configuration

```
kubectl apply -f mongo.yaml
```

4. Create configmap for mongodb url
This file contains the configuration for mongodb url

```
kubectl apply -f mongo-configmap.yaml
```

5. Create mongo express deployment
This file contains the deployment configuration for mongo express and it external service configuration to make it accessible from outside

```
kubectl apply -f mongo-express.yaml
```

7. Get the external ip of the mongo express service
In usual case, you can get the external ip of the service creating just by creating it but in minikube you have to do it manually

```
minikube service mongo-express-service
```

🎉 Congratulation you have successfully deployed mongodb on minikube