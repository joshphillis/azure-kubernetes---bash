# azure-kubernetes---bash

# 🚀 Azure Kubernetes Deployment Using Bash

This project demonstrates the setup and deployment of a scalable web application using **Azure Kubernetes Service (AKS)** and **Azure Cloud Shell (Bash)**. It includes cluster provisioning, secure access, app deployment, and performance monitoring.

---

## 📘 Problem Statement

Deploy a scalable, containerized web application via Microsoft Azure-managed Kubernetes infrastructure. Ensure public exposure, secure access, and performance visibility.

---

## 🛠️ Technologies Used

- Azure Portal & Cloud Shell (Bash)
- Azure Kubernetes Service (AKS)
- NGINX container
- `kubectl` CLI
- NGINX Ingress Controller
- cert-manager & Let’s Encrypt
- Azure Monitor & Insights

---

## 📂 Setup Workflow

### 1. Log in to Azure
Use Microsoft Authenticator for secure access.

### 2. Create Resource Group
```bash
az group create --name kubernetesjlp --location eastus
```

### 3. Provision AKS Cluster
```bash
az aks create \
  --resource-group kubernetesjlp \
  --name myAKSCluster \
  --node-count 3 \
  --enable-addons monitoring \
  --generate-ssh-keys
```

### 4. Connect to Cluster
```bash
az aks get-credentials --resource-group kubernetesjlp --name myAKSCluster
kubectl get nodes
```

### 5. Deploy NGINX Application
```bash
kubectl create deployment myapp --image=nginx
kubectl expose deployment myapp --port=80 --type=LoadBalancer
```

### 6. Secure with HTTPS
- Configure **DNS** to route traffic to AKS ingress IP
- Install **NGINX Ingress Controller**
- Enable **cert-manager** for automatic TLS provisioning with Let’s Encrypt

### 7. Monitor Performance
- Use Azure Monitor > Insights for cluster metrics and logs
- Validate SSL, resource usage, and app health

---

## ✅ Outcomes

- AKS cluster deployed with 3 nodes and SSH access
- NGINX app publicly exposed via Load Balancer on port 80
- HTTPS enabled via automated TLS issuance
- Full visibility into cluster health through Azure Insights

---

## 📌 Notes

This is a sanitized version safe for public GitHub sharing. No credentials or private domain data included. For automation or Helm-based upgrades, consider separating cert-manager and ingress config into Kubernetes YAML manifests.

## 🧠 Author

**Joshua**  
Kaizen-certified | Cloud Enablement Enthusiast | Security-first Infrastructure Designer  
