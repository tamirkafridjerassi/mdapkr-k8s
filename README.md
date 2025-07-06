# mdapkr-k8s — Kubernetes Helm Charts

## 🧭 Overview

This repository contains the Helm chart definitions for deploying the **mdapkr** microservice and its dependencies (MongoDB) to a Kubernetes cluster (EKS).

It follows a **parent-child Helm chart** structure:
- `mdapkr/` — Parent chart
- `charts/mongodb` — Subchart
- `charts/fastapi` — Subchart

## 📁 Structure

helm/
└── mdapkr/
└── mdapkr/
├── Chart.yaml # Parent chart
├── values.yaml # Default values
├── charts/
│ ├── fastapi/ # FastAPI subchart
│ └── mongodb/ # MongoDB subchart
└── templates/ # Custom Kubernetes templates

bash
Copy
Edit

## 🚀 Usage

### Install/Upgrade

```bash
helm dependency update ./helm/mdapkr/mdapkr
helm upgrade --install mdapkr ./helm/mdapkr/mdapkr \
  --set fastapi.image.repository=<your-ecr-url> \
  --set fastapi.image.tag=<your-tag>
📌 Replace <your-ecr-url> and <your-tag> accordingly.

💡 Notes
Ensure MongoDB is healthy before FastAPI is initialized.

All values can be overridden via --set flags or custom-values.yaml.

