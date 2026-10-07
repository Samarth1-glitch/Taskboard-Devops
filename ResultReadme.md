# TaskBoard DevOps Capstone Project

## Overview

TaskBoard is a full-stack project management application developed to demonstrate a complete DevOps workflow, from local development to automated deployment in a Kubernetes environment.

The project integrates modern development and DevOps tools including React, FastAPI, PostgreSQL, Docker, GitHub Actions, Terraform, Kubernetes, Helm, Prometheus, and Grafana. :contentReference[oaicite:0]{index=0}

---

## Tech Stack

### Frontend
- React
- Vite
- HTML/CSS

### Backend
- FastAPI
- SQLAlchemy
- Alembic
- PostgreSQL

### DevOps & Infrastructure
- Docker
- Docker Compose
- GitHub Actions
- Trivy
- GitHub Container Registry (GHCR)
- Terraform
- AWS EKS
- Kubernetes
- Helm

### Monitoring
- Prometheus
- Grafana

---

## Project Architecture

```text
Developer
   │
   ▼
GitHub Repository
   │
   ▼
GitHub Actions Pipeline
   │
   ├── Run Tests
   ├── Build Docker Images
   ├── Security Scan (Trivy)
   └── Push Images to GHCR
            │
            ▼
      Kubernetes Cluster
            │
            ▼
      Helm Deployment
            │
            ▼
   Frontend + Backend + Database
            │
            ▼
   Prometheus + Grafana
```

---

## Features

### Application Features

- Task Management Dashboard
- REST APIs
- PostgreSQL Database Integration
- Health Checks
- Readiness Checks
- Responsive UI

### DevOps Features

- Dockerized Application
- Automated CI/CD Pipeline
- Container Security Scanning
- Container Registry Integration
- Infrastructure as Code
- Kubernetes Deployment
- Helm-Based Releases

### Monitoring Features

- Metrics Collection
- Dashboard Visualization
- Application Monitoring
- Resource Monitoring

---

## Repository Structure

```text
taskboard/

├── frontend/
├── backend/
├── terraform/
├── helm/
├── monitoring/
├── k8s/
├── troubleshooting/
├── .github/workflows/
├── docker-compose.yml
└── README.md
```

---

## Running the Application Locally

### Clone the Repository

```bash
git clone <repository-url>
cd taskboard
```

### Start the Application

```bash
docker compose up --build
```

### Access the Application

Frontend:

```text
http://localhost:3000
```

Backend Swagger UI:

```text
http://localhost:8000/docs
```

Health Endpoint:

```text
http://localhost:8000/health
```

Metrics Endpoint:

```text
http://localhost:8000/metrics
```

### Stop the Application

```bash
docker compose down
```

---

## CI/CD Pipeline

The GitHub Actions workflow automates the entire software delivery process.

### Stage 1 – Testing

- Checkout source code
- Install dependencies
- Run Pytest
- Validate frontend build

### Stage 2 – Build

- Build Backend Docker Image
- Build Frontend Docker Image

### Stage 3 – Security Scan

- Scan images using Trivy
- Detect HIGH and CRITICAL vulnerabilities

### Stage 4 – Registry

- Push Docker images to GitHub Container Registry (GHCR)

### Stage 5 – Deployment

- Deploy application using Helm
- Update Kubernetes resources

---

## Docker Commands

### Build Backend Image

```bash
docker build -t taskboard-backend:local ./backend
```

### Build Frontend Image

```bash
docker build -t taskboard-frontend:local ./frontend
```

### Verify Images

```bash
docker images
```

---

## Terraform Infrastructure

Terraform is used to provision cloud infrastructure.

### Resources Created

- VPC
- Public Subnets
- Private Subnets
- NAT Gateway
- EKS Cluster
- Worker Nodes

### Commands

```bash
cd terraform

terraform init

terraform plan

terraform apply
```

### Destroy Infrastructure

```bash
terraform destroy
```

---

## Kubernetes Deployment

### Create Namespace

```bash
kubectl apply -f k8s/namespace.yaml
```

### Deploy Using Helm

```bash
helm upgrade --install taskboard ./helm/taskboard \
  --namespace taskboard \
  --create-namespace
```

### Verify Deployment

```bash
kubectl get pods -n taskboard
```

```bash
kubectl get svc -n taskboard
```

```bash
kubectl get deployments -n taskboard
```

---

## Horizontal Pod Autoscaler (HPA)

Check autoscaler status:

```bash
kubectl get hpa -n taskboard
```

The HPA automatically scales backend pods based on CPU utilization.

---

## Monitoring

### Prometheus

Prometheus collects application metrics from the backend.

Metrics include:

- Request Count
- Response Time
- Error Rates
- Application Health

### Grafana

Grafana visualizes metrics using dashboards.

Useful Monitoring Metrics:

- HTTP Requests
- Error Percentage
- CPU Usage
- Memory Usage
- Pod Scaling Activity

---

## Security

Trivy is integrated into the CI/CD pipeline to perform vulnerability scanning.

Security checks include:

- Container Image Scanning
- Dependency Analysis
- Vulnerability Detection

This ensures that only verified images are deployed.

---

## Verification Commands

### Kubernetes Resources

```bash
kubectl get all -n taskboard
```

### Pods

```bash
kubectl get pods -n taskboard
```

### Services

```bash
kubectl get svc -n taskboard
```

### Helm Releases

```bash
helm list -n taskboard
```

### HPA

```bash
kubectl get hpa -n taskboard
```

---

## Project Outcomes

Successfully implemented:

- Full-Stack Web Application
- Docker Containerization
- Automated Testing
- GitHub Actions CI/CD
- Security Scanning
- Container Registry Integration
- Infrastructure as Code
- Kubernetes Deployment
- Helm Package Management
- Autoscaling
- Monitoring and Observability

---

## CI/CD Pipeline Result

The pipeline completed successfully with:

✅ Tests Passed

✅ Docker Images Built Successfully

✅ Security Scan Completed

✅ Images Pushed to Registry

✅ Deployment Completed Successfully

---

## Pipeline Screenshot

> Add the screenshot of the successful GitHub Actions pipeline execution below.

![Successful Pipeline](images/pipeline-success.png)

---

## Author

**Samarth Patil**
**24BCS10171**



**Samarth Patil**
**24BCS10171**

**Samarth Patil**

BITS Pilani
