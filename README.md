# # End-to-End CI/CD Pipeline on GCP (Portfolio Deployment)

## Overview

This repository demonstrates a complete CI/CD pipeline for deploying a static portfolio website to Google Kubernetes Engine (GKE) using Google Cloud Platform services.

The project was built as a hands-on learning exercise to understand how modern cloud-native deployment pipelines work, starting from source code pushed to GitHub and ending with an application running on Kubernetes.

The objective was not only to deploy the application but also to understand each stage of the pipeline, troubleshoot real deployment issues, and follow production-style deployment practices.

---

## Tech Stack

* Google Cloud Platform (GCP)
* Cloud Build
* Cloud Deploy
* Google Kubernetes Engine (GKE)
* Artifact Registry
* Cloud Storage
* Skaffold
* Kubernetes
* Docker
* GitHub

---

## Project Workflow

```
Developer
    │
    ▼
GitHub Repository
    │
    ▼
Cloud Build Trigger
    │
    ▼
Cloud Build
    ├── Build Docker Image
    ├── Push Image to Artifact Registry
    └── Create Cloud Deploy Release
                │
                ▼
Cloud Deploy
    │
    ▼
Skaffold Render
    │
    ▼
Deploy to GKE
    │
    ▼
Kubernetes Service
    │
    ▼
Portfolio Website
```

---

## Repository Structure

```
.
├── assets/
├── clouddeploy/
│   ├── delivery-pipeline.yaml
│   └── target.yaml
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
├── cloudbuild.yaml
├── skaffold.yaml
├── Dockerfile
├── index.html
├── style.css
├── script.js
└── README.md
```

---

## Components

### Dockerfile

Builds the Docker image for the portfolio website.

### cloudbuild.yaml

Defines the Cloud Build pipeline.

Responsibilities:

* Build Docker image
* Push image to Artifact Registry
* Create Cloud Deploy Release

### skaffold.yaml

Defines how Cloud Deploy renders Kubernetes manifests and injects the correct Docker image.

### k8s/

Contains Kubernetes deployment and service manifests.

### clouddeploy/

Contains Cloud Deploy configuration:

* Delivery Pipeline
* Target

---

## Prerequisites

Before using this project, create:

* GCP Project
* Artifact Registry Repository
* GKE Cluster
* Cloud Build Trigger
* Cloud Deploy Pipeline
* Cloud Deploy Target
* Required Service Accounts
* IAM Roles

Required APIs:

* Cloud Build API
* Cloud Deploy API
* Artifact Registry API
* Kubernetes Engine API

---

## Deployment Flow

1. Push code to GitHub.
2. Cloud Build Trigger starts automatically.
3. Cloud Build builds the Docker image.
4. Cloud Build pushes the image to Artifact Registry.
5. Cloud Build creates a Cloud Deploy Release.
6. Cloud Deploy downloads the source.
7. Skaffold renders Kubernetes manifests.
8. Cloud Deploy replaces the placeholder image with the newly built image.
9. Cloud Deploy deploys the application to GKE.
10. Kubernetes creates the Deployment and Pods.
11. The LoadBalancer exposes the application.

---

## Key Learning

This project helped in understanding:

* End-to-end CI/CD
* Docker image lifecycle
* Artifact Registry
* Cloud Deploy
* Skaffold image substitution
* Kubernetes Deployment and Service
* IAM permissions
* Cloud Build automation
* Troubleshooting production deployment issues

---

## Common Issues Encountered

Some major issues solved during development:

* Cloud Build logging permissions
* Artifact bucket configuration
* Cloud Deploy render failures
* ImagePullBackOff
* Skaffold image replacement
* Kubernetes deployment debugging

---

## Future Improvements

* Multi-environment deployment (Dev / QA / Prod)
* Manual approval before Production
* Helm Charts
* Terraform for infrastructure
* Automated testing
* Security scanning
* Rollback strategy
* Monitoring and alerting
* GitHub Actions implementation
* Jenkins implementation

---

## Purpose of this Repository

This repository is maintained as a personal learning project to understand production-style CI/CD using Google Cloud Platform.

The primary goal is educational rather than production usage. As I continue learning, more improvements and cloud-native best practices will be added.
