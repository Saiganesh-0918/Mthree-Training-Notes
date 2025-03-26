# PROJECT (Week-7, Day-3)

After working on these scripts and the knowledge of our training, we are
working on our final project. Our team started the project a few days ago and
divided it into two teams.  

- One team is working on the issues in the **uber-app** which we are
  developing and diving deeper into it.  
- Another team is working on **Docker and Kubernetes** to deploy our
  application, and after that, we will work on implementing it on **SRE**.  

## **Progress So Far**
- We have **built the Docker images successfully** and loaded them into **Minikube**.
- We used a **cloud database URL** for our application.
- In the **morning session**, we **revised the Angular script** and performed a few queries, then moved to learning Docker and Kubernetes.
- We **revised Docker and Kubernetes concepts** in the morning session to help with our project.
- In the **afternoon session**, we developed **Docker files, .env files, and YAML files** required for our project.
- Next, we **created the containers, built the images**, and then applied the **deployment and secret YAML files** to our project.

![Linux Commands](../Images/Screenshot%202025-03-26%20170909.png)
![Linux Commands](../Images/Screenshot%202025-03-26%20170945.png)

## **Deployment Steps**

1. **Created the namespace `uber`**.
2. **Applied the secret YAML file** to ensure that our database is connected and updated.

![Linux Commands](../Images/Screenshot%202025-03-26%20171042.png)

### **Frontend Setup**
3. Navigate to the **frontend directory** and build the Docker image:
   ```sh
   docker build --no-cache -t frontend:latest .
   ```
![Linux Commands](../Images/Screenshot%202025-03-26%20171111.png)


4. Load the image into Minikube:
   ```sh
   minikube image load frontend:latest
   ```
5. Verify that the image is loaded into Minikube:
   ```sh
   minikube image list
   ```

### **Backend Setup**
6. Navigate to the **backend directory** and build the Docker image:
   ```sh
   docker build --no-cache -t backend:latest .
   ```
![Linux Commands](../Images/Screenshot%202025-03-26%20171210.png)

7. Load the image into Minikube:
   ```sh
   minikube image load backend:latest
   ```
8. Verify that the image is loaded into Minikube:
   ```sh
   minikube image list
   ```
![Linux Commands](../Images/Screenshot%202025-03-26%20171422.png)


## **Next Steps**
- Tomorrow, we will **develop an Nginx configuration file** to properly connect our services.
- This will help ensure that our **pods do not get `CrashLoopBackOff` or `ImagePullOff` errors**.

---

