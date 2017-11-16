# splunk-kubernetes
This project describes how to deploy Splunk Enterprise using Kubernetes. It is based on the [Docker Store](https://store.docker.com/images/splunk) image.

## Prerequisites
### Kubernetes Version
These instructions are written for Kubernetes 1.8 and above.

## Instructions
### Create Docker Store registry key
```
kubectl create secret docker-registry docker-store-registry-key --docker-server="https://index.docker.io/v1/" --docker-username=DOCKER_USER --docker-password=DOCKER_PASSWORD --docker-email=DOCKER_EMAIL
```

### Create the deployment
```
 kubectl create -f manifest.yml
 ```
 
### Create the services
```
kubectl expose deployment splunk-deployment --type="LoadBalancer"
```
