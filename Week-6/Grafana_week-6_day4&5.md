# GRAFANA (Week-6, Day-4 & 5)

## **Revision and Initial Errors**
Firstly, we revised all the queries from the previous session and observed all dashboards.

Then, we attempted to run the script and encountered a few errors, which we resolved:

1. **WSL-related error:**
   - Fixed by modifying the script using:
     ```sh
     if ! grep -qEi "(microsoft|wsl)" /proc/version
     ```
2. **Docker error:**
   - Fixed by running:
     ```sh
     sudo dockerd
     ```
3. **Script Execution:**
   - Ran the script again:
     ```sh
     ./complete-react-sre-script.sh
     ```
4. **NPM-related error:**
   - Fixed by running:
     ```sh
     npm uninstall react react-dom
     npm install react@18 react-dom@18
     sudo apt update
     sudo apt upgrade
     ```
5. **Script Execution after Fixes:**
   - Ran the script again successfully.

   ![Linux Commands](../Images/Screenshot%202025-03-20%20173201.png)

## **Deploying the React SRE Application**
1. Moved to the project directory and executed:
   ```sh
   cd react-sre-project
   ./deploy_sre_app.sh
   ```
2. Encountered an error:
   ```sh
   [ERROR] - This script must be run within WSL
   ```
   - Fixed by modifying the script (as mentioned in step 1).
3. Encountered another issue with Docker and Minikube.
   - Checked Minikube status:
     ```sh
     minikube status
     ```
   - Fixed Docker issues by running:
     ```sh
     sudo dockerd
     ```
   - Executed the script in another terminal.

![Linux Commands](../Images/Screenshot%202025-03-20%20183712.png)

## **Backend Development and Exposing Metrics**
1. Created a **Flask backend** with three API calls:
   - **Main route**
   - **Health check API** (`/api/health`)
   - **Metrics API** (`/api/metrics` for Prometheus scraping)
2. Created the following additional files:
   - **Dockerfile**
   - **Deployment YAML**
   - **Service YAML**
   - **requirements.txt**

![Linux Commands](../Images/Screenshot%202025-03-24%20104645.png)
![Linux Commands](../Images/Screenshot%202025-03-24%20104716.png)
3. Running the Flask API:
   ```sh
   python3 health-api.py
   ```
![Linux Commands](../Images/Screenshot%202025-03-24%20105205.png)

4. **API Calls and Responses:**
![Linux Commands](../Images/Screenshot%202025-03-24%20104928.png)
   - **`/api/health`** → Returns health status of the application.

![Linux Commands](../Images/Screenshot%202025-03-24%20105013.png)
   - **`/api/metrics`** → Displays collected application metrics.

![Linux Commands](../Images/Screenshot%202025-03-24%20105058.png)
   - **`/metrics`** → Shows function call metrics increasing over time.
![Linux Commands](../Images/Screenshot%20(143).png)



## **Frontend Deployment**
1. Ran the script to build the frontend.
2. Built the Docker image:
   ```sh
   docker rmi -f <image-id>  # Remove old image
   docker build --no-cache -t react-sre-app:latest .  # Build new image
   ```
3. Loaded the image into Minikube:
   ```sh
   minikube image load react-sre-app:latest
   ```
   - Verified with:
     ```sh
     minikube images
     ```
4. Applied Kubernetes configurations:
   ```sh
   cd kubectl/overlays
   kubectl apply -k dev
   ```
   ```sh
   cd ../base
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   ```
5. Started the frontend:
   ```sh
   npm start
   ```
![Linux Commands](../Images/Screenshot%202025-03-24%20110612.png)
![Linux Commands](../Images/Screenshot%202025-03-24%20110657.png)

6. Verified backend metrics:
   ```sh
   curl http://localhost:5000/api/metrics
   ```
![Linux Commands](../Images/Screenshot%202025-03-24%20110832.png)
![Linux Commands](../Images/Screenshot%202025-03-24%20110853.png)

## **Monitoring and Dashboard Setup in Grafana**
1. Verified Minikube and monitoring setup:
   ```sh
   minikube status
   ```
2. Enabled port-forwarding for Grafana:
   ```sh
   kubectl port-forward svc/grafana 8080:3000 -n monitoring
   ```
![Linux Commands](../Images/Screenshot%202025-03-24%20111725.png)
3. Opened Grafana in the browser and logged in.
4. Created a **SRE Overview Dashboard**:
   - Added tags: `sre`, `overview`, `production`
   - Under **Variables**, added:
     - **Name:** `service`
     - **Label:** `service`
     - **Type:** `query`
     - **Datasource:** `prometheus`
     - **Query:** `label_values(up, service)`
     - **Sort:** Alphabetical (asc)

### **Creating Panels in Grafana**
#### **Panel 1: Service Uptime**
- **Visualization:** Stat
- **Query:**
  ```promql
  up{service=~"$service"}
  ```
- **Threshold Values:** Configured based on uptime expectations.

![Linux Commands](../Images/Screenshot%202025-03-24%20115534.png)
#### **Panel 2: Service Availability (SLO: 99.9%)**
- **Visualization:** Gauge
- **Query:**
  ```promql
  sum(rate(http_requests_total_count{service=~"$service", status!~"5.."}[30m]))
  / sum(rate(http_requests_total_count{service=~"$service"}[30m])) * 100
  ```
- **Unit:** Percent (0-100)

![Linux Commands](../Images/Screenshot%202025-03-24%20120834.png)
#### **Panel 3: Monitoring Successful Requests in Prometheus**
- **Visualization:** Gauge
- **Query:**
  ```promql
  prometheus_http_requests_total{code="200"}
  ```
- **Unit:** Percent (0-100)
![Linux Commands](../Images/Screenshot%202025-03-24%20121620.png)

#### **Panel 4: Prometheus Alertmanager Discovery Status**
- **Visualization:** Table
- **Query:**
  ```promql
  prometheus_notifications_alertmanagers_discovered{job="prometheus"}
  ```
![Linux Commands](../Images/Screenshot%202025-03-24%20122617.png)
- **Description:** Displays the number of Alertmanager instances discovered by Prometheus.

![Linux Commands](../Images/Screenshot%202025-03-24%20122831.png)

## **Final Steps**
1. **Completed Minikube setup**, backend and frontend deployment.
2. **Built Docker images** and deployed monitoring components.
3. **Created a Grafana dashboard with key monitoring panels.**
4. If **port-forwarding fails**, ensure Minikube is running and retry:
   ```sh
   kubectl port-forward svc/grafana 8080:3000 -n monitoring
   ```
5. Verified dashboard metrics and confirmed successful data collection.

---
This document outlines the **setup, deployment, monitoring, and troubleshooting** of the SRE application with **Prometheus & Grafana**. 🚀

