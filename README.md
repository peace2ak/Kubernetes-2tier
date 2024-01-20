# Web App Deployment with Minikube and Kubernetes

This repository demonstrates the deployment of a web application using Minikube and Kubernetes. Follow the steps below to set up and access the application.

### Prerequisites

- Minikube installed
- kubectl installed

### Deployment Steps

1. Start Minikube:
    
    bashCopy code
    
    `minikube start`
    
2. Apply the Kubernetes Deployment:
    
    bashCopy code
    
    `kubectl apply -f web-app.yaml`
    
3. Expose the Deployment using NodePort:
    
    bashCopy code
    
    `kubectl expose deployment web-app --type=NodePort --port=80`
    
4. Apply the Ingress configuration:
    
    bashCopy code
    
    `kubectl apply -f web-ingress.yaml`
    
5. Get Minikube IP:
    
    bashCopy code
    
    `minikube ip`
    
6. Update the hosts file:
    
    - On Linux/Mac:
        
        bashCopy code
        
        `echo "<minikube-ip> webapp.local" | sudo tee -a /etc/hosts`
        
    - On Windows (Run as Administrator):
        
        bashCopy code
        
        `Add-Content C:\Windows\System32\drivers\etc\hosts "<minikube-ip> webapp.local"`
        
7. Access the application:
    
    - Using curl:
        
        bashCopy code
        
        `curl http://webapp.local`
        
    - or open in a web browser:
        
        arduinoCopy code
        
        `http://webapp.local`
        

### Cleanup

Delete the resources when done:

bashCopy code

`kubectl delete ingress,service,deployment web-app`

Stop Minikube:

bashCopy code

`minikube stop`

Feel free to modify and enhance the deployment configurations based on your requirements.
