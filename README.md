
**PROJECT FLOW** 

**GitHub → Jenkins → Docker Hub → Helm → AWS EKS → ALB → Node.js Pods → Prometheus/Grafana → ELK Stack.**

**Jenkins server in AWS EC2 instance**

<img width="1917" height="927" alt="image" src="https://github.com/user-attachments/assets/f0b32cdd-ec7d-4d94-916a-235627cf55cb" />


**For Jenkins modified in the security group with port number 8080**

<img width="1912" height="977" alt="securitygroup" src="https://github.com/user-attachments/assets/be79457b-e604-46ea-b032-fe90fef85cb7" />


**Jenkins File for CI CD pipeline** 


<img width="1896" height="917" alt="image" src="https://github.com/user-attachments/assets/daa8b8b3-8ffe-4de4-ac00-5abf383d82f2" />



**Stage View for for this project**

<img width="1232" height="332" alt="image" src="https://github.com/user-attachments/assets/be895bd8-27c4-4776-ab37-a9058fb082d0" />


**NODE API project Tree structure image**

<img width="1286" height="670" alt="image" src="https://github.com/user-attachments/assets/82127149-af27-4c6c-84ff-01c98396b607" />

**Installation completed the EKS Cluster**

<img width="1915" height="1017" alt="eks" src="https://github.com/user-attachments/assets/ecaa87d2-d29a-4451-bd03-e2c658d0b4e6" />

**EKS CLUSTER IN AWS INSTANCE**

<img width="1902" height="1022" alt="ekscluster" src="https://github.com/user-attachments/assets/870d459a-9b06-4117-b05e-c87661a24316" />



**HELM INSTALLATION COMPLETED**

<img width="1917" height="1067" alt="helm" src="https://github.com/user-attachments/assets/99d41637-c5b7-44f1-a015-d7141b1444e0" />


**HELM Installation and Commands**

**1.  Go to Project Directory**

     cd nodejs-api-eks

**2. Validate the Helm Chart**

   helm lint ./node-api
**3. Preview the Generated Manifests**

   helm template node-api ./node-api

**4. Install the Chart**

   helm install node-api ./node-api \
   --namespace production \
--create-namespace


**5. Verify Helm Release**

   helm list -n production

 
**6.  Check Resources**

    kubectl get all -n production
    kubectl get ingress -n production
    kubectl get svc -n production
    kubectl get pods -n production

**7. Check Release Status**

   helm status node-api -n production
       
**8. View Release Values**

   helm get values node-api -n production

   **NODE-API OUTPUT SCREENSHOT**

<img width="1917" height="967" alt="image" src="https://github.com/user-attachments/assets/18f67146-e449-4d04-9af2-72d4f9163fce" />




**Install Prometheus and Grafana using Helm on Kubernetes/EKS**

   
     
    


    







