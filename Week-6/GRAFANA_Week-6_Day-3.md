Firstly, we started revising the grafana dashboards and moved to the SRE 
concepts in grafana. 

1. Latency – How long it takes to serve a customer 

●  Example: A customer orders a burger. The time from placing the order to 

receiving the burger is latency. 

●  In tech: It's the time it takes for a user to get a response after making a 

request. 
 → If latency is high, customers (users) will get frustrated. 

2. Traffic – How many customers are coming in per hour 

●  Example: A counter at the restaurant door clicks every time a customer 

walks in. 

●  In tech: Counting how many requests the system gets per second or 

minute. 
 → If traffic is too high, the system might struggle to keep up. 

3. Errors – How many orders are wrong or complaints received 

●  Example: If customers send food back because it’s cold or incorrect, 

that’s an error. 

●  In tech: Tracking HTTP errors like 500 (server error) means something’s 

wrong with the system. 
 → More errors mean a bad user experience. 

4. Saturation – How close the restaurant is to full capacity 

●  Example: If the restaurant has 50 tables and 49 are occupied, it's almost 

full — that’s high saturation. 

●  In tech: Tracking how many requests are being processed at the same 

time. 
 → If the system is saturated, performance will drop. 

 
 
 
 
 
Observability 

1. Metrics – Tracking key numbers 

●  Example: A pilot monitors altitude, speed, and fuel level. 
●  In tech: Metrics track system performance — like how long requests take 

and how many are successful. 

2. Logs – Recording detailed events 

●  Example: A flight recorder (black box) logs everything that happens on 

the plane. 

●  In tech: Logs record every request, error, and system event — useful for 

debugging. 

3. Visualization – Easy-to-read dashboard 

●  Example: The cockpit dashboard shows altitude, speed, and warnings in 

one place. 

●  In tech: Dashboards make it easy to see how the system is performing. 

4. Instrumentation – Adding sensors to track performance 

●  Example: Sensors on the plane track fuel level and engine temperature. 
●  In tech: Adding code to measure how the app behaves under different 

loads. 

Health Monitoring  

1. Liveness Probes – Checking if the patient is alive 

●  Example: A pulse check — is the patient breathing? 
●  In tech: A simple check to see if the app is running at all. 

2. Readiness Probes – Checking if the patient can perform activities 

●  Example: Can the patient walk and talk? 
●  In tech: A check to see if the app is ready to handle requests. 

 
 
3. Health Endpoints – Checking specific health stats 

●  Example: Checking blood pressure, temperature, and oxygen levels. 
●  In tech: Different health checks for different parts of the app (like 

memory and database). 

4. Dependency Checks – Are all organs working together? 

●  Example: Heart, lungs, and brain need to work together. 
●  In tech: The app needs to connect to the database and other services to 

work properly. 

Service Level Objectives 

1. Error Rate Tracking – How many pizzas are wrong 

●  Example: Out of 100 pizzas, 5 are wrong — that’s a 5% error rate. 
●  In tech: Tracking how many requests fail or result in errors. 

2. Latency Histograms – How long deliveries take 

●  Example: 70% of pizzas arrive in under 20 minutes, 25% take 30 

minutes, and 5% take an hour. 

●  In tech: A histogram shows how fast most requests are processed. 

3. Request Success Rate – Percentage of successful deliveries 

●  Example: 95% of pizzas were delivered correctly and on time. 
●  In tech: Measures how many requests are processed successfully. 

 
 
 
 
 
 
 
 
 
●  Next we ran the script and tried to create the dashboards and panels. 
●  Run the script by using the command 
./lightweight-sre-monitoring.sh 

●  If we get any error regarding docker permissions. Run the below 

command 

sudo dockerd 

●  Open the new terminal and run the script again. If you get permission 

error, modify the permission for the file 

Chmod 777 lightweight-sre-monitoring.sh 

●  Run the script again and i got the error as 

Kubernetes version: 
           error: unknown flag: --short 

●  Open script and remove the --short from the code after kubectl and then 

run the script. 

●  I got another error timedout. So I increased the time from 120 -200 in the 

script and then ran the script. 

●  Finally it worked and opened the grafana dashboard from the URL 

http://localhost:3000 

![Linux Commands](../Images/Screenshot%202025-03-19%20162537.png)

●  Next we started to create the dashboards using the md file that was 

mentioned in the script. 

 
●  The steps are the same to create a dashboard. Go to dashboards click on 

add new dashboard and add visualization. 

●  Select prometheus as the data source, select stat in visualization and in 

standard options select time and then seconds and enter the below query  

sum by(endpoint) (rate(app_request_count_total{namespace="sre-demo"}[24h])) 

The query returns The rate of incoming requests (in requests per second) for 
each endpoint over the last 24 hours. 

Output 

 
 
 ![Linux Commands](../Images/Screenshot%202025-03-19%20164501.png)
 
 

 
 
●  Next created another panel as selecting prometheus server, stat as 

visualization and executed the query 

sum(rate(app_request_count{namespace="sre-demo", 

http_status=~"5.."}[1m])) / 

sum(rate(app_request_count{namespace="sre-demo"}[1m])) * 100 

This query will return the percentage of total requests that resulted in HTTP 5xx 
errors over the last 1 minute. But in my case it is returning nothing and 
mentioning no data. Because there is no error hitting. 

Output 


 
 ![Linux Commands](../Images/Screenshot%202025-03-19%20171227.png)
 
 
 
 
 
●  Next created another panel as selecting prometheus server, stat as 

visualization and executed the query 

app_active_requests{namespace="sre-demo"} 

This query will return the current number of active requests being handled by 
the app in the sre-demo namespace. But in my case it is returning nothing 
because there are no active requests. 

Output 

![Linux Commands](../Images/Screenshot%202025-03-19%20171605.png)

●  Next created another panel as selecting prometheus server, Time series as 

visualization and executed the query 
histogram_quantile(0.95, 

sum(rate(app_request_latency_seconds_bucket{namespace="sre-demo"}

[5m])) by (le, endpoint)) 

This query returns the 95th percentile of request latency. It is a 
histogram+quantile query. The use case of this query is measuring how long 
requests are taking at the 95th percentile. 

 
Output 

![Linux Commands](../Images/Screenshot%202025-03-19%20172043.png)


●  As of my interest I have created a panel as selecting prometheus server, 

stat as visualization and executed the query 
app_request_latency_seconds_count{namespace="sre-demo"} 

This query directly returns the total number of requests that have been observed 
for the app_request_latency_seconds metric in the sre-demo namespace. It does 
NOT measure latency — it only counts how many times latency has been 
measured. 
Output 

 ![Linux Commands](../Images/Screenshot%202025-03-19%20172327.png)
 
 
●  As of my interest I have created another panel as selecting prometheus 

server, bar chart as visualization and executed the query 
rate(apiserver_cache_list_total{job="kubernetes-apiservers"}[5m]) 

This query returns the average rate of cache list operations handled by the 
Kubernetes API server per second over the last 5 minutes. 

Output 

![Linux Commands](../Images/Screenshot%202025-03-19%20172610.png)

●  As of my interest I have created another panel as selecting prometheus 

server, Gauge as visualization and executed the query 
sum(apiserver_cache_list_total{job="kubernetes-apiservers"}) 

This query returns the total number of cache list operations handled by all API 
servers since the server started. The difference between the above and this query 
is  

●  sum(apiserver_cache_list_total) → Total number of cache list 

operations since startup. 

●  rate(apiserver_cache_list_total[5m]) → Current rate of cache list 

operations per second over the last 5 minutes. 

 
 
 
Output 

![Linux Commands](../Images/Screenshot%202025-03-19%20173037.png)

●  After all this click on save dashboard and give the name as SRE Basic 

Dashboard. The final dashboard with all panels 

 
 ![Linux Commands](../Images/Screenshot%202025-03-19%20173221.png)

 ![Linux Commands](../Images/Screenshot%202025-03-19%20173308.png)
 
 
 
 
 
●  Next created another dashboard with few panels as the same steps. Go to 

dashboards click on add new dashboard and add visualization. 

●  All the above panels are worked on prometheus and now we are working 

on LOKI as a data source. 

●  Select LOKI as the data source, select logs in visualization and in that 

enable time and enter the below query  

{namespace="sre-demo"} 

This query returns filter logs from Loki to only show entries belonging to the 
sre-demo namespace. It’s useful for troubleshooting and monitoring specific 
environments. 

Output 
 
![Linux Commands](../Images/Screenshot%202025-03-19%20174041.png)
 
 
 
 
 
●  Next created another panel as selecting LOKI as a data source, stat as 

visualization and executed the query 

{namespace="sre-demo"} |= `Error` 

This query filters logs from the sre-demo namespace and shows only logs that 
contain the word "Error". If there is no Error it shows nothing just simply says 
no data as happened in my case. 

Output 

 
![Linux Commands](../Images/Screenshot%202025-03-19%20174507.png)
 
 
 
 
 
●  Next created another panel as selecting LOKI as a data source, stat as 

visualization and executed the query 
sum(count_over_time({namespace="sre-demo"}[1m])) 

This query counts the total number of logs generated in the sre-demo namespace 
over the last 1 minute. 

Output 

![Linux Commands](../Images/Screenshot%202025-03-19%20174719.png)

●  After all this click on save dashboard and give the name as Log Analysis. 

The final dashboard with all panels 

![Linux Commands](../Images/Screenshot%202025-03-19%20174851.png)

●  In the afternoon session we have brushed up on all the topics revised in 
the morning session and prepared for the python exam with the help of 
LMS. 

