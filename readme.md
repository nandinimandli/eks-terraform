# 🚀 EKS Infrastructure with Terraform

This project provisions a **highly available, production-ready Amazon EKS (Elastic Kubernetes Service) cluster** using **Terraform**.

It includes:
- VPC with public and private subnets across multiple Availability Zones
- Internet Gateway, NAT Gateways, and routing
- EKS control plane and managed node groups
- Remote Terraform backend using S3 and DynamoDB

---

## 📁 Project Structure

eks-terraform/
│
├── backend/                 → Creates S3 bucket and DynamoDB for remote state
├── modules/
│   ├── vpc/                 → VPC, Subnets, NAT, IGW, Routing
│   └── eks/                 → EKS Cluster, IAM Roles, Node Group
│
├── main.tf                 → Root module - invokes VPC and EKS
├── variables.tf            → Input variables
├── outputs.tf              → Output values
├── .gitignore              → Git ignored files
└── README.md               → Project overview and instructions



---

## 🔧 Prerequisites

- AWS CLI configured (`aws configure`)
- Terraform installed
- kubectl installed
- AWS account with permissions to create EKS & related resources

---

## 🚀 Getting Started

### 1. Setup Remote Backend (S3 + DynamoDB)

```bash
cd backend
terraform init
terraform apply

### 2. Deploy EKS Infrastructure
```bash
cd ..
terraform init
terraform plan
terraform apply

### 3. Connect to Kubernetes Cluster
```bash
aws eks update-kubeconfig --region <your-region> --name <cluster-name>
kubectl get nodes
🧹 Clean Up
To destroy all created AWS resources:

```bash
terraform destroy

✨ Note
Replace <your-region> and <cluster-name> with your actual values.

You can make region and name dynamic using input variables in variables.tf.

🙌 Contribution
Feel free to fork this repo, improve it, and submit PRs. Suggestions and improvements are welcome!

🙏 Thank You
Thank you for checking out this project!
If it helped you learn something or saved your time, consider giving it a ⭐️ on GitHub.
Happy Terraforming and EKS-ing! 🚀