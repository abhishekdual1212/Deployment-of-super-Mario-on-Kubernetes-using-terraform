# **🚀 Deploying Super Mario on AWS EKS using Terraform**  

Super Mario is a legendary game we all cherish! In this project, we will deploy **Super Mario** on **Amazon EKS (Elastic Kubernetes Service)** using **Terraform** and manage infrastructure with AWS resources.  

![Super Mario](https://imgur.com/Njqsei9.gif)  

---

## 📌 **Project Overview**

This project provisions an **EKS cluster** on AWS and deploys the **Super Mario game** using **Terraform** and **Kubernetes manifests**. The deployment includes:

- ✅ Amazon EKS Cluster provisioning
- ✅ Terraform Infrastructure as Code (IaC)
- ✅ Kubernetes Deployment & Service for Super Mario
- ✅ AWS S3 Backend for Terraform state management
- ✅ IAM roles & policies for EKS & worker nodes

---

## **📁 Project Structure**  

```bash
📂 DEPLOYMENT-OF-SUPER-MARIO
│── 📂 EKS-TF               # Terraform configuration files for AWS EKS
│   ├── backend.tf          # S3 backend for Terraform state management
│   ├── main.tf             # AWS EKS Cluster and Node Group definition
│   ├── provider.tf         # AWS provider configuration
│   ├── deployment.yaml     # Kubernetes Deployment for Super Mario
│   ├── service.yaml        # Kubernetes Service for exposing Super Mario app
│── 📄 README.md            # Project documentation
```

---

## **📌 Prerequisites**  

Before proceeding, ensure you have the following installed:

- ✅ **Terraform** (>=1.3.0)  
- ✅ **AWS CLI** (Configured with proper credentials)  
- ✅ **kubectl** (For managing Kubernetes resources)  
- ✅ **Docker** (For containerization)  

---

## **🛠️ Setup & Deployment**  

### **1️⃣ Clone the Repository**  

```bash
git clone https://github.com/NotHarshhaa/Deployment-of-super-Mario-on-Kubernetes-using-terraform.git
cd Deployment-of-super-Mario-on-Kubernetes-using-terraform/EKS-TF
```

### **2️⃣ Initialize & Apply Terraform**  

```bash
terraform init      # Initialize Terraform backend
terraform plan      # Preview infrastructure changes
terraform apply -auto-approve  # Deploy to AWS
```

### **3️⃣ Configure Kubernetes Context**  

```bash
aws eks update-kubeconfig --name EKS_CLOUD --region ap-south-1
```

### **4️⃣ Deploy Super Mario Application**  

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

### **5️⃣ Access the Application**  

Once deployed, get the external LoadBalancer URL:  

```bash
kubectl get services mario-service
```

Access **Super Mario** in your browser using the displayed URL.

---

## **🎯 Project Highlights**

- **AWS EKS**: Managed Kubernetes cluster for scalable deployment.  
- **Terraform**: Infrastructure as Code (IaC) for automated provisioning.  
- **Kubernetes**: Ensures containerized deployment of the game.  
- **AWS S3 Backend**: Remote state management for Terraform.  

---

## **🔗 Resources**

- **Terraform Docs**: [https://developer.hashicorp.com/terraform/docs](https://developer.hashicorp.com/terraform/docs)  
- **AWS EKS Docs**: [https://docs.aws.amazon.com/eks/latest/userguide](https://docs.aws.amazon.com/eks/latest/userguide)  
- **Kubernetes Docs**: [https://kubernetes.io/docs/home/](https://kubernetes.io/docs/home/)  

---

## **📢 Credits & Acknowledgments**  

This project is inspired by the **Super Mario** game, and it demonstrates real-world **DevOps practices** using AWS, Terraform, and Kubernetes.  

👉 **Read the detailed blog here**: [Super Mario EKS Deployment](https://blog.prodevopsguy.xyz/deployment-of-super-mario-on-kubernetes-using-terraform)  

🚀 *Happy Gaming & DevOps-ing!* 🎮

---


