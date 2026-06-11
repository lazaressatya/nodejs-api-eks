
**PROJECT FLOW** 

**GitHub → Jenkins → Docker Hub → Kubernetes Manifest Files → AWS EKS → ALB → Node.js Pods → Prometheus/Grafana → ELK Stack.**

**Jenkins server in AWS EC2 instance**

<img width="1917" height="927" alt="image" src="https://github.com/user-attachments/assets/f0b32cdd-ec7d-4d94-916a-235627cf55cb" />


**For Jenkins modified in the security group with port number 8080 , 9090, 3000**

<img width="1912" height="1015" alt="image" src="https://github.com/user-attachments/assets/449a9ce5-850f-4f2f-89c9-a9869230f5ff" />



**Jenkins File for CI CD pipeline** 


<img width="1896" height="917" alt="image" src="https://github.com/user-attachments/assets/daa8b8b3-8ffe-4de4-ac00-5abf383d82f2" />



**Stage View for for this project**

<img width="1232" height="332" alt="image" src="https://github.com/user-attachments/assets/be895bd8-27c4-4776-ab37-a9058fb082d0" />




**Installation completed the EKS Cluster**

<img width="1915" height="1017" alt="eks" src="https://github.com/user-attachments/assets/ecaa87d2-d29a-4451-bd03-e2c658d0b4e6" />

**EKS CLUSTER IN AWS INSTANCE**

<img width="1911" height="1025" alt="image" src="https://github.com/user-attachments/assets/393fcf32-4faa-46e8-b9bd-df0f7d1134f3" />





   **NODE-API OUTPUT SCREENSHOT**

<img width="1912" height="1017" alt="image" src="https://github.com/user-attachments/assets/b7481da4-6e5f-405d-bfc8-30c122952e17" />





**Install Prometheus and Grafana using Helm on Kubernetes/EKS**

**Prometheus Dashboard fetching the targets **

URL: http://a20b33e7408cf46128c1a4da9f81cdc0-1993384439.ap-south-1.elb.amazonaws.com/targets

<img width="1917" height="1001" alt="image" src="https://github.com/user-attachments/assets/3f245635-b00c-47dc-8846-3cf62a34d35d" />

**Grafana Dashboard fetching the data from via prometheus**

URL : http://afe4021228a274791a8975e4ea7e4ce7-1964621081.ap-south-1.elb.amazonaws.com/


<img width="1907" height="1020" alt="image" src="https://github.com/user-attachments/assets/3e89ae59-7cd3-486c-8fec-44efc59ade3d" />


<img width="1887" height="1012" alt="image" src="https://github.com/user-attachments/assets/1bcec6fa-8f73-4d66-81f6-387e5a67e850" />



   
     
    


    







