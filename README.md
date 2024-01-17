

# Hello World App with Kubernetes and Ingress

This project demonstrates how to deploy a Node.js Hello World application to a local Kubernetes cluster running on Minikube and expose it to the outside world using an Ingress controller.

## Prerequisites

- **Install Minikube:** Follow the official Minikube installation instructions to set up Minikube on your system.
- **Install Docker:**
- **Install Kubectl** 

## Getting Started

1. **Start Minikube:**

   Ensure Minikube is running by executing the following command in your terminal:

   ```bash
   minikube start


## Create the Kubernetes manifests

Create the necessary Kubernetes manifests (`hello-world-pod.yaml`, `hello-world-service.yaml`, and `hello-world-ingress.yaml`) and save them in the same directory as this README file.

## Apply the Kubernetes manifests to Minikube

Apply the Kubernetes manifests to your Minikube cluster using the following commands:

```bash
kubectl apply -f hello-world-pod.yaml
kubectl apply -f hello-world-service.yaml
kubectl apply -f hello-world-ingress.yaml
```
## Get the Minikube IP

To obtain the Minikube IP, run the following command:

```
minikube ip
```
Then, you can access your service by simply visiting `http://[Minikube-IP]`. You don't need to specify a port since Ingress operates at the HTTP level and by default uses port 80

## Troubleshooting:

**If you're not getting the expected response, ensure your Node.js application is running correctly within the pod. Check the logs using**
```
kubectl logs hello-world
```

**Ensure that the Ingress resource is correctly configured and points to your service.
Use** ```kubectl get ingress```

**to check the status of the Ingress.**
If you encounter any issues, check the Ingress controller's logs for more details.


**Use ** ```kubectl get pods```  **to check the status of the hello-world pod. It should be in Running state.**


**Double-check that your NodePort service is correctly configured and running.** 

Run ```kubectl get svc hello-world-service```




