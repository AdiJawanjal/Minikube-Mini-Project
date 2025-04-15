#  Minikube Project

This project showcases how to deploy a web application on a **Minikube Kubernetes cluster** hosted on an **Amazon EC2 instance**.

---

## 📌 Tools Used

- **Amazon EC2** (Amazon Linux AMI)
- **Docker**
- **Minikube**
- **Kubernetes (kubectl)**
- **YAML (for Kubernetes manifests)**

---

## ⚙️ Setup Instructions

### 1. Launch EC2 Instance

- **Type**: t2.medium (recommended)
- **AMI**: Amazon Linux AMI
- **Storage**: 20 GB
- Allow inbound rules for:
  - Port `22` (SSH)
  - Port `30080` (for NodePort access)

---

### 2. Installation 

```bash
//Installing Dependencies
sudo yum update -y
sudo yum install -y docker curl conntrack

//Start Docker
sudo service docker start
sudo usermod -aG docker ec2-user
newgrp docker

//Install kubectl
curl -LO https://dl.k8s.io/release/v1.29.0/bin/linux/amd64/kubectl
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

//Install Minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube-linux-amd64
sudo mv minikube-linux-amd64 /usr/local/bin/minikube

//Start Minikube
minikube start --driver=docker


