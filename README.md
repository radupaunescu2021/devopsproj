Hello World App with Kubernetes and Ingress
This project demonstrates how to deploy a Node.js Hello World application to a local Kubernetes cluster running on Minikube and expose it to the outside world using an Ingress controller.

Prerequisites
Install Minikube: Follow the official Minikube installation instructions to set up Minikube on your system.
Steps
Start Minikube: Ensure Minikube is running by executing the following command in your terminal:
Bash
minikube start
Use code with caution. Learn more
Build the Docker image: If you haven't already, build the Docker image for your application using the following command:
Bash
docker build -t radufirst/hello-world-node:latest .
Use code with caution. Learn more
Create the Kubernetes manifests: Create the necessary Kubernetes manifests (hello-world-pod.yaml, hello-world-service.yaml, and hello-world-ingress.yaml) and save them in the same directory as this README file.

Apply the Kubernetes manifests to Minikube: Apply the Kubernetes manifests to your Minikube cluster using the following commands:

Bash
kubectl apply -f hello-world-pod.yaml
kubectl apply -f hello-world-service.yaml
kubectl apply -f hello-world-ingress.yaml
Use code with caution. Learn more
Get the external IP address of the Ingress controller: Once the manifests are applied, obtain the external IP address of the Ingress controller using the following command:
Bash
kubectl get ingress hello-world-ingress -o jsonpath="{.status.loadBalancer.ingress[0].ip}"
Use code with caution. Learn more
Access the application: Replace the <external-ip-address> placeholder with the actual external IP address obtained in the previous step and run the following command to access the application:
Bash
curl <external-ip-address>
Use code with caution. Learn more
You should see the following output:

Hello World
Cleanup
To delete the resources deployed to your Minikube cluster, run the following commands:

Bash
kubectl delete -f hello-world-pod.yaml
kubectl delete -f hello-world-service.yaml
kubectl delete -f hello-world-ingress.yaml
minikube stop
