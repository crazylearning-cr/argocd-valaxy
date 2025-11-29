## Application installation

```

kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d; echo

argocd login localhost:8080
Username: admin
Password: 

aws eks --region ap-south-1 update-kubeconfig --name argocd-cluster
kubectl config current-context



argocd cluster add arn:aws:eks:us-east-1:020930354342:cluster/argocd-cluster


argocd app create guestbook --repo https://github.com/argoproj/argocd-example-apps.git  --path guestbook --dest-server https://A62CA7263E52E0796D6E1872363F8B2F.gr7.us-east-1.eks.amazonaws.com --dest-namespace default


kubectl port-forward svc/guestbook-ui -n default 8081:80


```

