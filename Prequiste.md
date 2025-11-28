## Pod

# create a file called pod.yaml with the below contents
```
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80

```
```
kubectl apply -f pod.yaml
kubectl get pods

```
# create a file called deployment.yaml with the below contents

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
        - name: nginx
          image: nginx
          ports:
            - containerPort: 80

```
```
kubectl apply -f deployment.yaml
kubectl get deployments
```

# Namespace
```
kubectl create namespace demo
kubectl get ns
```
# GIT Basics
```
git init
git status
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main
```
