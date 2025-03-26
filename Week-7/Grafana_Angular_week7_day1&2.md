# Angular & Grafana (Week-7, Day-1&2)

Firstly, as we completed the script and worked with React by creating a backend
and exposed the metrics to Prometheus and Grafana, we created the
dashboards and performed the queries.

Next, we moved to another script with Angular, connected the
backend, displayed the dashboard, and then worked on Grafana by creating
dashboards and performing queries.

## Setup Steps

### 1. Run the Master Script
First, run the script `master-script.sh` which creates all the required files
to run the script and build the dashboard.

![Linux Commands](../Images/Screenshot%202025-03-25%20190910.png)


### 2. Create Required Folders
This will create the necessary folders. Next, run all setup
files to configure the required scripts.

### 3. Set Up Minikube
Run the script `set-up-wsl-minikube.sh` to create a Minikube setup. This script installs Docker, Kubernetes & Minikube. If they exist, it will update them.

![Linux Commands](../Images/Screenshot%202025-03-25%20193025.png)


```sh
cd wsl-setup/
./setup-wsl-minikube.sh
```

![Linux Commands](../Images/Screenshot%202025-03-25%20210250.png)
![Linux Commands](../Images/Screenshot%202025-03-25%20210340.png)


If you encounter an error with Docker, use:
```sh
sudo dockerd
```
and rerun the script.

### 4. Install Prometheus
Run the Prometheus setup file:
```sh
cd prometheus
chmod +x setup-prometheus.sh
./setup-prometheus.sh
```
![Linux Commands](../Images/Screenshot%202025-03-26%20175006.png)



### 5. Install Grafana
```sh
cd grafana
chmod +x setup-grafana.sh
./setup-grafana.sh
```
![Linux Commands](../Images/Screenshot%202025-03-26%20175159.png)


### 6. Modify Angular App Files
To ensure our Angular app runs correctly, we added the following files:

#### a. `ts.config.app.json`
```json
{
    "extends": "./tsconfig.json",
    "compilerOptions": {
        "outDir": "./out-tsc/app",
        "types": ["node"]
    },
    "files": ["src/main.ts"],
    "include": ["src/**/*.d.ts"]
}
```

#### b. `tsconfig.json`
```json
{
    "compileOnSave": false,
    "compilerOptions": {
        "outDir": "./dist/out-tsc",
        "strict": true,
        "strictNullChecks": false,
        "moduleResolution": "bundler",
        "target": "ES2022"
    },
    "angularCompilerOptions": {
        "strictInjectionParameters": true,
        "strictTemplates": true
    }
}
```

#### c. `index.html`
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>Test</title>
    <base href="/">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="icon" type="image/x-icon" href="favicon.ico">
</head>
<body>
    <app-root></app-root>
</body>
</html>
```

#### d. `main.ts`
```ts
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { AppModule } from './app/app.module';
platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));
```

![Linux Commands](../Images/Screenshot%202025-03-26%20180318.png)


### 7. Run Setup Script
Check running pods using:
```sh
kubectl get pods -n sre-monitoring
```
![Linux Commands](../Images/Screenshot%202025-03-26%20180444.png)



Then, run the setup script:
```sh
./setup.sh
```

![Linux Commands](../Images/Screenshot%202025-03-26%20180659.png)
![Linux Commands](../Images/Screenshot%202025-03-26%20180626.png)


This script:
- Sets up required files
- Builds Docker images for frontend and backend
- Loads them into Minikube
- Applies deployment files
- Sets up Prometheus and Grafana

![Linux Commands](../Images/Screenshot%202025-03-26%20193128.png)


### 8. Accessing the Applications
- **Prometheus:** Accessible via displayed links after setup.

![Linux Commands](../Images/Screenshot%202025-03-26%20193251.png)
![Linux Commands](../Images/Screenshot%202025-03-26%20193424.png)



To fix Angular UI access issues, use port forwarding:
```sh
kubectl port-forward svc/angular-ui-service 8080:80 -n sre-monitoring
```
![Linux Commands](../Images/Screenshot%202025-03-26%20193946.png)
![Linux Commands](../Images/Screenshot%202025-03-26%20194034.png)


- **Grafana:** Login credentials are displayed in the terminal:
  - **Username:** `admin`
  - **Password:** `admin`

![Linux Commands](../Images/Screenshot%202025-03-26%20193547.png)



## Grafana Dashboard Setup

### 1. Create Dashboard
Go to **Create Dashboard** → **Add a New Panel** → **Select Prometheus as Data Source**.

### 2. Add Visualizations and Queries

#### **a. Total HTTP Requests** (Gauge Visualization)
```promql
http_requests_total{endpoint="/api/alerts"}
```
![Linux Commands](../Images/Screenshot%202025-03-26%20194641.png)



Retrieves the total count of HTTP requests received for `/api/alerts`.

#### **b. Request Duration Count** (Bar Chart)
```promql
http_request_duration_seconds_count{endpoint="/metrics"}
```

![Linux Commands](../Images/Screenshot%202025-03-26%20195400.png)

Returns the number of requests measured for duration on `/metrics`.

#### **c. CPU Usage** (Histogram)
```promql
process_cpu_seconds_total{job="flask-app"}
```

![Linux Commands](../Images/Screenshot%202025-03-26%20195853.png)

Tracks the total CPU time consumed by the Flask app.

#### **d. CPU Utilization Rate** (Heatmap)
```promql
rate(process_cpu_seconds_total{job="flask-app"}[5m])
```

![Linux Commands](../Images/Screenshot%202025-03-26%20200709.png)

Shows CPU utilization rate over the last 5 minutes.

Save the dashboard as **SRE Dashboard for Angular**.

![Linux Commands](../Images/Screenshot%202025-03-26%20201102.png)

![Linux Commands](../Images/Screenshot%202025-03-26%20201354.png)



### 3. Additional Queries in Prometheus

#### **a. Memory Usage**
```promql
process_resident_memory_bytes{job="flask-app"}
```

![Linux Commands](../Images/Screenshot%202025-03-26%20201820.png)

Tracks real-time RAM usage of the Flask app.

#### **b. Flask App Uptime**
```promql
time() - process_start_time_seconds{job="flask-app"}
```
![Linux Commands](../Images/Screenshot%202025-03-26%20202814.png)


Shows how long the Flask app has been running (useful for detecting restarts).

---

## 🎯 Conclusion
- Successfully set up **Prometheus & Grafana**.
- Created **Angular UI and Backend Integration**.
- Implemented **custom dashboards & queries**.
- Verified application accessibility via **Minikube**.

🚀 **Next Steps:** Experiment with advanced **alerting and monitoring!**

