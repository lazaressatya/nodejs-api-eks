# nodejs-api-eks +------------------+
                    |     Developer    |
                    +--------+---------+
                             |
                             v
                    +------------------+
                    |      GitHub      |
                    +--------+---------+
                             |
                             v
                    +------------------+
                    |     Jenkins      |
                    |   CI/CD Pipeline |
                    +--------+---------+
                             |
                +------------+------------+
                |                         |
                v                         v
        +---------------+        +----------------+
        | Docker Build  |        | Unit Testing   |
        +-------+-------+        +----------------+
                |
                v
        +---------------+
        | Docker Hub    |
        | Container     |
        | Registry      |
        +-------+-------+
                |
                v
        +---------------+
        | Helm Deploy   |
        +-------+-------+
                |
                v
   +------------------------------------+
   |          AWS EKS Cluster           |
   +------------------------------------+
                |
      +---------+---------+
      |                   |
      v                   v
+-------------+    +-------------+
| Deployment  |    |   Service   |
| Node.js API |    |  ClusterIP  |
+------+------+    +------+------+ 
       |                  |
       +---------+--------+
                 |
                 v
          +-------------+
          |   Ingress   |
          | AWS ALB     |
          +------+------+ 
                 |
                 v
          +-------------+
          | End Users   |
          +-------------+


Monitoring Architecture
Node.js Application
        |
        v
+----------------+
|  Prometheus    |
| Metrics Scrape |
+--------+-------+
         |
         v
+----------------+
|    Grafana     |
| Dashboards     |
+----------------+
Metrics Collected
CPU Usage
Memory Usage
Pod Health
Request Rate
Error Rate
Response Time
Application Availability
Logging Architecture
Node.js Application
        |
        v
+----------------+
|   Fluent Bit   |
+--------+-------+
         |
         v
+----------------+
| Elasticsearch  |
+--------+-------+
         |
         v
+----------------+
|    Kibana      |
+----------------+
Log Flow

Application Logs → Fluent Bit → Elasticsearch → Kibana

Kubernetes Components
Deployment
Runs Node.js application pods.
Replica count ensures high availability.
Liveness and readiness probes improve reliability.
Service
Internal communication layer.
Exposes application using Kubernetes Service.
Ingress
AWS Application Load Balancer (ALB).
Internet-facing endpoint.
Routes external traffic to the application.
Horizontal Pod Autoscaler
Automatically scales pods based on CPU utilization.
Namespace
Production environment isolation.
ServiceMonitor
Enables Prometheus metrics scraping.