🚀 EKS GitOps & Monitoring Project
ArgoCD + Prometheus + Grafana on AWS EKS

This repository demonstrates a production-aligned DevOps setup on AWS EKS using GitOps and Monitoring best practices.

You will learn how to:

Deploy GitOps using ArgoCD

Monitor Kubernetes using Prometheus & Grafana

Use Helm for managing monitoring stacks

Work with real-world EKS workflows

✅ Interview-ready
✅ Beginner-friendly
✅ Industry-standard DevOps practices

🧰 Tech Stack

AWS EKS – Kubernetes cluster

eksctl – EKS cluster creation

kubectl – Kubernetes CLI

ArgoCD – GitOps Continuous Delivery

Prometheus – Metrics collection

Grafana – Visualization & dashboards

Helm – Kubernetes package manager

Docker

Ubuntu (EC2)

🧱 Architecture Overview
GitHub Repository
        |
        v
     ArgoCD
        |
        v
 AWS EKS Cluster
 ├── Application Pods
 ├── Prometheus (Metrics)
 ├── Alertmanager
 └── Grafana (Dashboards)

📌 Prerequisites

AWS Account

Ubuntu EC2 Instance

IAM Role attached to EC2 with:

AmazonEKSFullAccess

IAMFullAccess

EC2FullAccess

🔧 Install Required Tools (Ubuntu)

Verify installations:

aws --version
kubectl version --client
eksctl version
docker --version
helm version


📌 Installation scripts are included in the repository.

☸️ Create EKS Cluster
eksctl create cluster \
--name my-cluster \
--region ap-south-1 \
--nodegroup-name ng-1 \
--node-type t3.medium \
--nodes 2

Verify Cluster
kubectl get nodes

🔄 Install ArgoCD
Create Namespace & Install
kubectl create namespace argocd

kubectl apply -n argocd \
-f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

Access ArgoCD UI
kubectl port-forward svc/argocd-server -n argocd 8080:443

Get Admin Password
kubectl get secret argocd-initial-admin-secret -n argocd \
-o jsonpath="{.data.password}" | base64 -d


Login

Username: admin

Password: (output from above command)

📊 Install Monitoring (Prometheus + Grafana)
Add Helm Repo
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

Install Monitoring Stack
kubectl create namespace monitoring

helm install prometheus prometheus-community/kube-prometheus-stack \
-n monitoring

Verify Pods
kubectl get pods -n monitoring

📈 Access Grafana
kubectl port-forward svc/prometheus-grafana -n monitoring 3000:80


URL: http://localhost:3000

Username: admin

Get Grafana Password
kubectl get secret prometheus-grafana -n monitoring \
-o jsonpath="{.data.admin-password}" | base64 -d

📊 ArgoCD Monitoring in Grafana
Steps Performed

Enabled ArgoCD metrics

Created ServiceMonitor for ArgoCD

Verified Prometheus targets

Imported Grafana dashboards

Recommended Dashboard IDs

ArgoCD Dashboard → 14584

Kubernetes Cluster → 7249

Node Metrics → 1860

✅ Verification
kubectl get pods -n argocd
kubectl get pods -n monitoring


Prometheus targets should show:

Status: UP

🧹 Cleanup (Delete Cluster)
eksctl delete cluster --name my-cluster --region ap-south-1

🎯 Key Learnings

GitOps workflow using ArgoCD

Kubernetes monitoring using Prometheus & Grafana

ServiceMonitor & metrics scraping

AWS EKS lifecycle management

Real-world DevOps practices
