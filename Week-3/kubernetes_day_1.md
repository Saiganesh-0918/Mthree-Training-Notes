# Kubernetes Day 1

## **Introduction to Kubernetes**
Kubernetes (K8s) is an open-source system for managing, scaling, and deploying containerized applications.

### **Why Kubernetes?**
- Automates deployment and scaling of applications.
- Manages multiple containers efficiently.
- Provides fault tolerance and high availability.

## **Installing Kubernetes on Ubuntu**
```sh
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common gnupg2 conntrack
```

### **Install Docker for Kubernetes**
```sh
sudo apt-get remove -y docker docker-engine docker.io containerd runc || true
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io
sudo usermod -aG docker $USER
```

### **Install kubectl (Kubernetes CLI)**
```sh
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
rm kubectl
kubectl version --client
```

### **Install Minikube (Local Kubernetes Cluster)**
```sh
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
rm minikube-linux-amd64
```

### **Install Helm (Kubernetes Package Manager)**
```sh
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

## **Configuring Kubernetes**
```sh
mkdir -p ~/.kube
alias k="kubectl"
alias kgp="kubectl get pods"
alias kgs="kubectl get services"
alias kgd="kubectl get deployments"
alias kgn="kubectl get nodes"
alias kga="kubectl get all"
```

## **Executing Kubernetes Scripts**
```sh
./simplified-k8s-demo.sh
```
After execution, follow the **URL displayed in the terminal** to see the output in the browser.

### **Useful Kubernetes Commands**
```sh
kubectl get deployments -n mini-demo    # List all deployments
kubectl get pods -n mini-demo           # List all running pods
kubectl get pods -n mini-demo -o wide   # List pods with IP addresses
kubectl -n mini-demo logs -l app=flask-app  # View logs
```

## **Summary**
- Installed **Kubernetes, Minikube, and Helm**.
- Configured **kubectl** CLI for cluster management.
- Ran **a sample Kubernetes script** and viewed logs.
- Learned key **Kubernetes commands** for managing deployments.
