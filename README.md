# Web App Deployment with Minikube and Kubernetes

This repository exemplifies the deployment of a web application using Minikube and Kubernetes. Follow the steps below to set up and access the application.

### Prerequisites

- Minikube installed
- kubectl installed

### Deployment Steps

1. Start Minikube and Enable the NGINX Ingress controller:
    
    
    
    ```shell
    minikube start
    ```
    
    
    
    ```shell
    minikube addons enable ingress
    ```
    
2. Apply the Kubernetes Deployment:
    
    
    
    ```shell
    kubectl apply -f web-app.yaml
    ```
    
3. Expose the Deployment using NodePort:
    
    
    
    ```shell
    kubectl expose deployment web-app --type=NodePort --port=80
    ```
    
4. Apply the Ingress configuration:
    
    
    
    ```shell
    kubectl apply -f web-ingress.yaml
    ```
    
5. Get Minikube IP:
    
    
    
    ```shell
    minikube ip
    ```
    
6. Update the hosts file:
    
    - On Linux/Mac:
        
        
        
        ```shell
        echo "<minikube-ip> webapp.local" | sudo tee -a /etc/hosts
        ```
        
    - On Windows (Run as Administrator):
        
        
        
        ```shell
        Add-Content C:\Windows\System32\drivers\etc\hosts "<minikube-ip> webapp.local"
        ```
        
7. Access the application:
    
    - Using curl:
        
        
        
        ```shell
        curl http://webapp.local
        ```
        
    - or open in a web browser:
        
        
        
        ```shell
        http://webapp.local
        ```
        

### Cleanup

Delete the resources when done:



```shell
kubectl delete ingress,service,deployment web-app
```

Stop Minikube:



```shell
minikube stop
```

Feel free to modify and enhance the deployment configurations based on your requirements.
