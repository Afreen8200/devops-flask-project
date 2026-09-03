# DevOps CI/CD & Kubernetes Deployment Pipeline

A hands-on DevOps project demonstrating an automated CI/CD workflow for a Python Flask application using Jenkins, Docker, AWS ECR, Kubernetes, Prometheus, and Grafana.

## Architecture

```text
Developer
   ↓
GitHub
   ↓
Jenkins
   ├── Install Dependencies
   ├── Run Pytest
   ├── Build Docker Image
   └── Push Image to AWS ECR
              ↓
         AWS ECR
              
Kubernetes (Docker Desktop)
   ├── Deployment
   ├── Pod
   └── NodePort Service
              ↓
        Flask Application

Prometheus
   ↓
Collects Kubernetes Metrics
   ↓
Grafana
   ↓
Monitoring Dashboards
```

## Technologies Used

- Python & Flask
- Git & GitHub
- Jenkins
- Pytest
- Docker
- AWS ECR
- Kubernetes
- Helm
- Prometheus
- Grafana

## CI/CD Pipeline

The Jenkins pipeline automates the following workflow:

1. Pulls the latest source code from GitHub.
2. Creates an isolated Python virtual environment.
3. Installs application dependencies.
4. Runs automated tests using Pytest.
5. Builds the Flask application as a Docker image.
6. Authenticates with Amazon ECR.
7. Tags and pushes the Docker image to the ECR repository.

## Kubernetes Deployment

The application is deployed to a local Kubernetes cluster using Docker Desktop.

The Kubernetes configuration includes:

- **Deployment** – manages the Flask application pod.
- **Pod** – runs the containerized Flask application.
- **Service (NodePort)** – exposes the application outside the cluster.

Kubernetes also provides automatic workload recovery if the application pod stops.

## Monitoring

The `kube-prometheus-stack` was installed using Helm.

The monitoring stack includes:

- **Prometheus** for collecting Kubernetes metrics.
- **Grafana** for visualizing metrics through dashboards.
- **Alertmanager** for alert management.
- **Node Exporter** and **kube-state-metrics** for infrastructure and Kubernetes metrics.

Grafana dashboards are used to observe pod CPU, memory, and other Kubernetes workload metrics.

## Project Structure

```text
devops-flask-project/
├── app.py
├── test_app.py
├── requirements.txt
├── Dockerfile
├── Jenkinsfile
├── deployment.yaml
├── service.yaml
├── .gitignore
└── README.md
```

## Pipeline Flow

```text
Code Change
    ↓
Git Push
    ↓
Jenkins Pipeline
    ↓
Automated Testing
    ↓
Docker Build
    ↓
Push Image to AWS ECR
    ↓
Kubernetes Deployment
    ↓
Prometheus Monitoring
    ↓
Grafana Visualization
```

## Key Learning Outcomes

This project provided hands-on experience with:

- Building and troubleshooting CI/CD pipelines with Jenkins.
- Automating application testing before container builds.
- Containerizing applications using Docker.
- Managing container images using Amazon ECR.
- Deploying and exposing containerized applications with Kubernetes.
- Working with Kubernetes Deployments, Pods, and Services.
- Installing Kubernetes applications using Helm.
- Monitoring Kubernetes workloads using Prometheus and Grafana.

## Current Scope

Amazon ECR is used as the cloud container registry, while Kubernetes runs locally through Docker Desktop. The project focuses on demonstrating the DevOps workflow and core CI/CD, containerization, orchestration, and monitoring concepts.