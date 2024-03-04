What is ArgoCD?
Argo CD is a Kubernetes-native continuous deployment (CD) tool. Unlike external CD tools that only enable push-based deployments, Argo CD can pull updated code from Git repositories and deploy it directly to Kubernetes resources.

What is GitOps?
GitOps is a way of implementing Continuous Deployment for cloud-native applications. It focuses on a developer-centric experience when operating infrastructure, by using tools developers are already familiar with, including Git and Continuous Deployment tools.

The core idea of GitOps is to have a Git repository that always contains declarative descriptions of the infrastructure currently desired in the production environment and an automated process to make the production environment match the described state in the repository. If you want to deploy a new application or update an existing one, you only need to update the repository — the automated process handles everything else. It’s like having cruise control for managing your applications in production.

Create the namespace for argoCD
kubectl create namespace argocd

Install ArgoCD using the below command
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl get all -n argocd

Now in order to access the UI of ArgoCD, you need to run the below command
kubectl port-forward --address 0.0.0.0 svc/argocd-server -n argocd 8080:443

user name: admin
You get the password by typing

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

create application.yaml

kubectl apply -f application.yaml

