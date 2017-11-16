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
Check the status of the service using:
```
kubectl get service splunk-deployment
```
You will see this output:
```
NAME                TYPE           CLUSTER-IP     EXTERNAL-IP     PORT(S)          AGE
splunk-deployment   LoadBalancer   10.39.249.89   <pending>       8000:30301/TCP   1m
```
Once you have an external IP, open this url in your browser:
```
http://EXTERNAL_IP:8000
```
Log into your Splunk instance with user `admin` and password `changeme`.

Voilà!
