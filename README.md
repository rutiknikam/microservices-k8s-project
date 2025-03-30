# microservices-k8s-project
 
### **📌 Microservices Kubernetes Project**  

This project demonstrates a **Microservices-based Web Application** deployed using **Docker** and **Kubernetes**. It includes **auto-scaling, traffic management, and monitoring** with **Prometheus & Grafana**.  

---

## **📖 Table of Contents**
1. [Project Overview](#-project-overview)  
2. [Tech Stack](#-tech-stack)  
3. [Features](#-features)  
4. [Architecture](#-architecture)  
5. [Installation & Setup](#-installation--setup)  
6. [Deploying to Kubernetes](#-deploying-to-kubernetes)  
7. [Enabling Auto-Scaling](#-enabling-auto-scaling)  
8. [Monitoring with Grafana](#-monitoring-with-grafana)  
9. [Contributing](#-contributing)  
10. [License](#-license)  

---

## **📌 Project Overview**  
This microservices project uses **Docker** to containerize applications and **Kubernetes** for orchestration. It supports **auto-scaling**, **traffic management**, and **real-time monitoring** with **Prometheus and Grafana**.  

---

## **🛠️ Tech Stack**  
✔ **Docker** – Containerization  
✔ **Kubernetes** – Container orchestration  
✔ **Helm** – Package management for Kubernetes  
✔ **Prometheus** – Metrics collection & monitoring  
✔ **Grafana** – Data visualization  

---

## **🚀 Features**  
✅ **Containerized Application** – Easily deployable with Docker  
✅ **Auto-Scaling** – Adjusts resources dynamically  
✅ **Traffic Management** – Load balancer ensures smooth traffic flow  
✅ **Monitoring** – Real-time tracking using Prometheus & Grafana  

---

## **🛠️ Architecture**  
Here’s a **simplified architecture diagram** of the project:  

```
┌──────────────┐       ┌──────────────┐
│  User        │ ----> │  LoadBalancer│
└──────────────┘       └──────────────┘
                              │
                              ▼
                      ┌─────────────┐
                      │   Service   │
                      └─────────────┘
                              │
              ┌───────────────┴───────────────┐
              ▼                               ▼
      ┌──────────────┐                  ┌──────────────┐
      │  Pod 1       │                  │  Pod 2       │
      └──────────────┘                  └──────────────┘
              │                               │
              ▼                               ▼
      ┌──────────────┐                  ┌──────────────┐
      │  Database    │                  │  Cache       │
      └──────────────┘                  └──────────────┘
```

---

## **🛠️ Installation & Setup**  

### **1️⃣ Clone the Repository**  
```sh
git clone https://github.com/YOUR_USERNAME/microservices-k8s-project.git
cd microservices-k8s-project
```  

### **2️⃣ Build and Run Docker Container**  
```sh
docker build -t microservice-app .
docker run -p 3000:3000 microservice-app
```  
📌 **Explanation**:  
- The `docker build` command creates an image named `microservice-app`.  
- The `docker run` command starts a container and exposes it on port **3000**.  

---

## **🚀 Deploying to Kubernetes**  

### **3️⃣ Deploy on Kubernetes**  
```sh
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```  
📌 **Explanation**:  
- `deployment.yaml` defines **how many replicas** of the microservice should run.  
- `service.yaml` creates a **LoadBalancer** to expose the application.  

✅ **Verify the deployment:**  
```sh
kubectl get pods
kubectl get svc
```  

---

## **📈 Enabling Auto-Scaling**  

### **4️⃣ Configure Horizontal Pod Autoscaler (HPA)**  
```sh
kubectl autoscale deployment microservice-app --cpu-percent=50 --min=1 --max=5
```  
📌 **Explanation**:  
- `--cpu-percent=50` → If CPU usage exceeds 50%, Kubernetes **creates more pods**.  
- `--min=1 --max=5` → The number of pods will **scale between 1 to 5**.  

✅ **Check autoscaler status:**  
```sh
kubectl get hpa
```

---

## **📊 Monitoring with Grafana**  

### **5️⃣ Install Prometheus using Helm**  
```sh
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install prometheus prometheus-community/kube-prometheus-stack
```  

### **6️⃣ Access Grafana Dashboard**  
```sh
kubectl port-forward svc/prometheus-grafana 3000:80
```  
✅ Open **http://localhost:3000** in your browser.  

📌 **Login Credentials**:  
- **Username**: `admin`  
- **Password**: *(Retrieve with the command below)*  
```sh
kubectl get secret --namespace default prometheus-grafana -o jsonpath="{.data.admin-password}" | base64 --decode
```  

✅ **Add Prometheus as a Data Source** in Grafana:  
1. Open **Grafana → Configuration → Data Sources**  
2. Select **Prometheus**  
3. Set **URL** as `http://prometheus-kube-prometheus-stack.default.svc:9090`  
4. Click **Save & Test**  

---

## **📢 Contributing**  
Pull requests are welcome! If you’d like to contribute, please fork the repository and submit a PR.  

---

## **📜 License**  
This project is licensed under the **MIT License**.  

---

## **🎯 Summary**  
✔ **Cloned the project** and built the Docker image  
✔ **Deployed the app on Kubernetes** with a LoadBalancer  
✔ **Enabled auto-scaling** for efficient resource usage  
✔ **Monitored the application** using Prometheus & Grafana  


