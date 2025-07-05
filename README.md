# DevOps Interview Assignment

## ✅ Project Overview

This project demonstrates how to use **Terraform**, **AWS EKS**, **ArgoCD**, and **Kubernetes** to deploy an NGINX web application using GitOps CI/CD.

---

## 📁 Folder Structure

devops-assignment/
├── terraform/ # Terraform code for VPC + EKS
├── manifests/ # Kubernetes deployment + service for NGINX
├── argocd/ # ArgoCD application YAML
└── README.md # Documentation


---

## ⚙️ Setup Instructions

### 1. Provision the EKS Cluster using Terraform

```bash
cd terraform
terraform init
terraform apply
Approve the changes by typing yes when prompted.

2. Configure kubectl to Access the Cluster

aws eks --region us-east-1 update-kubeconfig --name my-eks-cluster
3. Install ArgoCD on the EKS Cluster

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
4. Access ArgoCD UI

kubectl port-forward svc/argocd-server -n argocd 8080:443
Then open: http://localhost:8080

🔑 To get the ArgoCD admin password:


kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 --decode
5. Deploy the NGINX App via ArgoCD

kubectl apply -f argocd/nginx-app.yaml
ArgoCD will automatically sync the application from your GitHub repository.

6. Access the NGINX Application

kubectl get svc
Copy the LoadBalancer URL and open it in your browser.

Example:

http://a950e436ffedb4a3db3747d7f82530e2-1099551385.us-east-1.elb.amazonaws.com

✅ Project Status
Component	Status
EKS Cluster	✅ Created
ArgoCD  	✅ Installed
NGINX App	✅ Deployed
LoadBalancer	✅ Accessible

👤 Author
Rajesh Behera
GitHub: mrdrajesh
