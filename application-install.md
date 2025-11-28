## Application installation

```
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d; echo

argocd login localhost:8080
Username: admin
Password: 

aws eks --region ap-south-1 update-kubeconfig --name argocd-cluster
kubectl config current-context



argocd cluster add arn:aws:eks:us-east-1:020930354342:cluster/argocd-cluster

```

