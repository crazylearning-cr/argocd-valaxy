# guestbook-ui-workflow

## Prequisite
1. Cluster installation follow create-cluster.md

Steps 1: 
Create a repositry name argo-rollout-guestbook-blue-green and clone it into local


Step 2: create a pv for workflow
```
kubectl create namespace argo
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
```

Step 3: create a service account, the workflow needs to provision pod and other resources

```
kubectl apply -f sa-rbac.yaml
```

Step 4: create a docker secret
```
  kubectl create secret docker-registry dockerhub-secret \
  --docker-username=udemykcloud534 \
  --docker-password=Diehard_12 \
  --docker-email=ranjinimanjunath2025@gmail.com \
  -n argo
```
Step 5: Install argo rollout
```
kubectl apply -n argo -f https://github.com/argoproj/argo-workflows/releases/latest/download/install.yaml
```

Step 6: create a workflow

```
argo submit -n argo /Users/ranjiniganeshan/udemy/Argocd/guestbook-ui-app/worflow.yaml  --watch
```
```
argo-server-55479c8698-pcpjn           0/1     Running   0          10s
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Name:                guestbook-build-6ptvl
Namespace:           argo
ServiceAccount:      argo-workflow
Status:              Succeeded
Conditions:          
 PodRunning          False
 Completed           True
Created:             Mon Sep 01 16:59:31 +0530 (1 minute ago)
Started:             Mon Sep 01 16:59:31 +0530 (1 minute ago)
Finished:            Mon Sep 01 17:00:33 +0530 (now)
Duration:            1 minute 2 seconds
Progress:            3/3
ResourcesDuration:   2s*(1 cpu),41s*(100Mi memory)
Parameters:          
  repo-url:          https://github.com/udemykcloud/guestbook-ui-app.git
  docker-username:   udemykcloud534
  image-tag:         v1

STEP                      TEMPLATE         PODNAME                                           DURATION  MESSAGE
 ✔ guestbook-build-6ptvl  build-and-push                                                                 
 ├───✔ clean-workspace    clean-workspace  guestbook-build-6ptvl-clean-workspace-2531158719  11s         
 ├───✔ clone              git-clone        guestbook-build-6ptvl-git-clone-208639590         7s          
 └───✔ build              docker-build     guestbook-build-6ptvl-docker-build-2244932224     22ـــ
```

Step 7: verify if the workflow works

```
kubectl get pods -n argo
```

```
NAME                                   READY   STATUS    RESTARTS   AGE
argo-server-55479c8698-pcpjn           1/1     Running   0          64s
workflow-controller-6cb4558cbf-cdspg   1/1     Running   0          64s
```

Step 8: verify the workflow


```
argo logs -n argo @latest --follow  

```
