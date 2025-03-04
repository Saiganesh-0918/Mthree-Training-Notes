# Kubernetes Week-4 Day-2

## **Introduction to Kubernetes**
Kubernetes is an open-source container orchestration platform that automates **deployment, scaling, and management** of containerized applications.

### **Key Features of Kubernetes:**
1. **Scheduling** - Decides where to deploy the container.
2. **Auto Scaling** - Adjusts the number of instances based on workload.
3. **Service Discovery** - Ensures communication between containers.
4. **Self-Healing** - Automatically restarts failed containers.

## **Technical Phases of Kubernetes:**
1. **Deploy** - Ensures that containers are running successfully.
2. **Expose** - Assigns ports and IP addresses to make applications accessible.
3. **Manage** - Monitors applications, auto-scales as needed.
4. **Secure** - Uses config maps and secrets to ensure security.

### **Understanding Kubernetes Components**
1. **API Server** - Acts as the control center for Kubernetes.
2. **ETCD** - Stores configurations and pod details.
3. **Scheduler** - Decides where containers should be placed.
4. **Control Manager** - Ensures containers run as expected.

## **Kubernetes Terminology**
- **Kubelet** - Ensures all containers in a node are running properly.
- **Kube Proxy** - Manages network flow between containers.
- **Namespace** - Groups resources for isolation between projects.
- **Pods** - The smallest deployable unit in Kubernetes.

## **Important Kubernetes Commands**
```sh
kubectl apply -f filename.yaml  # Create or update resources
kubectl get pods                # List all running pods
kubectl describe pods           # View detailed pod information
kubectl logs pod-name           # View pod logs
kubectl scale deployment name --replicas=5  # Scale application instances
kubectl set image deployment name container=new-image  # Update container image
```

## **Summary**
- Learned about Kubernetes **orchestration and automation**.
- Explored key **components and phases of Kubernetes**.
- Practiced **Kubernetes commands for managing containers**.
