**Jenkins File for CI CD pipeline** 


<img width="1896" height="917" alt="image" src="https://github.com/user-attachments/assets/daa8b8b3-8ffe-4de4-ac00-5abf383d82f2" />


**Stage View for for this project **

<img width="1232" height="332" alt="image" src="https://github.com/user-attachments/assets/be895bd8-27c4-4776-ab37-a9058fb082d0" />



**NODE API project Tree structure image**

<img width="1286" height="670" alt="image" src="https://github.com/user-attachments/assets/82127149-af27-4c6c-84ff-01c98396b607" />

**HELM Installation and Commands **

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


**Install Prometheus and Grafana using Helm on Kubernetes/EKS**

   
     
    


    







