
# Grafana (Week-6, Day-2)

We created the dashboard in Grafana and panels yesterday. If we want that dashboard back, we need to import the dashboard from our user to the local machine by following commands:

### 1. Get the list of pods:
```bash
kubectl get pods -n monitoring
```
![Linux Commands](../Images/Screenshot%202025-03-18%20130241.png)
This lists the pods that are running in the Kubernetes cluster.

---

### 2. Check if Grafana, Prometheus, and Loki are running.

---

### 3. Go to the Grafana pod and see the dashboards (which are JSON files) and then copy them to the user.

![Linux Commands](../Images/Screenshot%202025-03-18%20130647.png)

You will see two JSON files in the Grafana dashboards:

- **k8s-pod-logs.json**  
- **k8s-simple-dashboard.json**  

---

### 4. Copy the JSON files to the local machine using:
```bash
kubectl cp grafana-5bfb6885b5-28zwj:/var/lib/grafana/dashboards/default/k8s-pod-logs.json ./k8s-pod-logs.json -n monitoring
kubectl cp grafana-5bfb6885b5-28zwj:/var/lib/grafana/dashboards/default/k8s-simple-dashboard.json ./k8s-simple-dashboard.json -n monitoring
```
These `kubectl cp` commands copy files from the running Grafana pod to the local machine.

---

### 5. Check if the files were downloaded:
```bash
ls k8s-pod-logs.json k8s-simple-dashboard.json
```

---

### 6. If the script doesn't work, do port forwarding:
```bash
kubectl port-forward svc/grafana -n monitoring 3000:80
```
This maps your local machine's `localhost:3000` to the Grafana service’s internal port `80`.

---


### 7. Access Grafana:
- Open `http://localhost:3000` in the browser.
- Login with your username and password.
- Go to the dashboard and click on **"Import Dashboard"**.

![Linux Commands](../Images/Screenshot%202025-03-18%20153153.png)

- Upload your JSON file, change the UID, and click on **"Create"**.
- Finally, you can see your dashboard in the list.

---


### 8. Example:
In this case, **Mydashboard** is the imported dashboard. If you go into it, you can see your panels.

---
![Linux Commands](../Images/Screenshot%20(110).png)

![Linux Commands](../Images/Screenshot%20(111).png)

![Linux Commands](../Images/Screenshot%20(112).png)

![Linux Commands](../Images/Screenshot%20(113).png)

![Linux Commands](../Images/Screenshot%20(114).png)

![Linux Commands](../Images/Screenshot%20(115).png)

### 9. Afternoon session:
- Brushed up on Grafana, Prometheus, Loki, and worked on the project.
