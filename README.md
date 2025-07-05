Run the following in your terminal:

bash
Copy
Edit
cat > README.md << 'EOF'
# DevOps Interview Assignment

## ✅ Project Overview
This project provisions an EKS cluster using Terraform, installs ArgoCD for GitOps, and deploys an NGINX application to the cluster.

---

## 📁 Folder Structure

devops-assignment/
├── terraform/ # Terraform for VPC + EKS setup
├── manifests/ # Kubernetes Deployment & Service for NGINX
├── argocd/ # ArgoCD Application YAML
└── README.md # Documentation

---

## ⚙️ Setup Instructions

### 1. Provision the EKS Cluster using Terraform

```bash
cd terraform
terraform init
terraform apply
# Approve with "yes"
2. Configure kubectl to Access the Cluster
aws eks --region us-east-1 update-kubeconfig --name my-eks-cluster
3. Install ArgoCD on the EKS Cluster
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
4. Access the ArgoCD UI
kubectl port-forward svc/argocd-server -n argocd 8080:443
# Then open: http://localhost:8080
🔑 Get the ArgoCD Admin Password
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 --decode
5. Deploy the NGINX Application via ArgoCD
kubectl apply -f argocd/nginx-app.yaml
6. Access the NGINX Application
kubectl get svc
# Copy the LoadBalancer EXTERNAL-IP and open it in your browser
✅ Project Status
Component	Status
EKS Cluster	✅ Created
ArgoCD  	✅ Installed
NGINX App	✅ Deployed
LoadBalancer	✅ Accessible

👤 Author
Name: Rajesh Behera
GitHub: mrdrajesh
