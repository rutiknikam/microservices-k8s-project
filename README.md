Microservices Kubernetes Project

This project demonstrates a Microservices-based Web Application deployed using Docker and Kubernetes.

Features
✅ Containerized using Docker
✅ Deployed on Kubernetes (Minikube/AWS EKS)
✅ Auto-Scaling with Horizontal Pod Autoscaler
✅ Traffic Management via LoadBalancer
✅ Monitoring with Prometheus & Grafana

Installation

1️⃣ Clone the Repository

sh
Copy
Edit
git clone https://github.com/YOUR_USERNAME/microservices-k8s-project.git
cd microservices-k8s-project
2️⃣ Build and Run Docker Container

sh
Copy
Edit
docker build -t microservice-app .
docker run -p 3000:3000 microservice-app
3️⃣ Deploy on Kubernetes

sh
Copy
Edit
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
4️⃣ Enable Auto-Scaling

sh
Copy
Edit
kubectl autoscale deployment microservice-app --cpu-percent=50 --min=1 --max=5
Monitoring with Grafana

1️⃣ Install Prometheus using Helm

sh
Copy
Edit
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install prometheus prometheus-community/prometheus
2️⃣ Access Grafana Dashboard

sh
Copy
Edit
kubectl port-forward svc/prometheus-grafana 3000:80
Open http://localhost:3000 and login with admin/admin.

Contributing
Pull requests are welcome! 😊

License
MIT License