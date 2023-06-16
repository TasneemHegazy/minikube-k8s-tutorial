# Minikube Tutorial

This tutorial will guide you through the process of setting up Minikube on your Ubuntu 18/20 or Mint system and deploying an application using Kubernetes.

## Prerequisites

Before we begin, make sure you have the necessary tools installed on your system: Docker, Minikube, kubectl, and Siege.

## Installation

To install Docker, execute the following commands:
```bash
# Ubuntu
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io

# Mint
sudo apt install -y docker.io
```

To install Minikube, run the following commands:
```bash
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 
chmod +x minikube
sudo mv minikube /usr/local/bin/
```

Next, install kubectl with these commands:
```bash
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

Finally, install Siege using the following command:
```bash
sudo apt install -y siege
```

## Starting Minikube

To start Minikube, run:
```bash
minikube start
```

## Deploying the App

Now let's deploy our application using Kubernetes. Run the following commands:
```bash
kubectl create -f kube/deployment.yaml
kubectl create -f kube/service.yaml
```

## Verifying the Deployment/Service

To check the status of the pods and services, use the following commands:
```bash
kubectl get pods
kubectl get services
```

## Removing the Deployment/Service

If you want to remove the deployment and service, execute:
```bash
kubectl delete -f kube/deployment.yaml
kubectl delete -f kube/service.yaml
```

## Accessing the App

To access the deployed application, you need to get the internal IP of the service. Run:
```bash
minikube service kube --url
```

Use the provided internal IP to access the application in your browser.

## Other Features

Minikube provides additional features that you can enable. Try them out!
```bash
minikube addons enable metrics-server
minikube addons enable dashboard
minikube addons enable ingress
```

## Conclusion

You have successfully completed the Minikube tutorial. Take this opportunity to explore more features and experiment with Kubernetes.