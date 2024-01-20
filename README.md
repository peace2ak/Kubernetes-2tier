# Web App Deployment with Minikube and Kubernetes

This repository exemplifies the deployment of a web application using Minikube and Kubernetes. Follow the steps below to set up and access the application.

### Prerequisites

- Minikube installed
- kubectl installed

### Deployment Steps

1. Start Minikube and Enable the NGINX Ingress controller:
    
    
    
    ```minikube start```
    
    
    
    ```minikube addons enable ingress```
    
2. Apply the Kubernetes Deployment:
    
    
    
    ```kubectl apply -f web-app.yaml```
    
3. Expose the Deployment using NodePort:
    
    
    
    ```kubectl expose deployment web-app --type=NodePort --port=80```
    
4. Apply the Ingress configuration:
    
    
    
    ```kubectl apply -f web-ingress.yaml```
    
5. Get Minikube IP:
    
    
    
    ```minikube ip```
    
6. Update the hosts file:
    
    - On Linux/Mac:
        
        
        
        ```echo "<minikube-ip> webapp.local" | sudo tee -a /etc/hosts```
        
    - On Windows (Run as Administrator):
        
        
        
        ```Add-Content C:\Windows\System32\drivers\etc\hosts "<minikube-ip> webapp.local"```
        
7. Access the application:
    
    - Using curl:
        
        
        
        ```curl http://webapp.local```
        
    - or open in a web browser:
        
        
        
        ```http://webapp.local```
        

### Cleanup

Delete the resources when done:



```kubectl delete ingress,service,deployment web-app```

Stop Minikube:



```minikube stop```

Feel free to modify and enhance the deployment configurations based on your requirements.
