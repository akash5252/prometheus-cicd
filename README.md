# Prometheus CI/CD using Jenkins + Helm + Kubernetes

## Overview
This project demonstrates automated deployment of Prometheus monitoring stack using Jenkins CI/CD pipeline and Helm charts.

## Architecture
GitHub → Jenkins Pipeline → Kubernetes Cluster → Prometheus Helm Chart

## Tools Used
- Jenkins
- Helm
- Kubernetes
- Prometheus
- GitHub

## How it works
1. Jenkins pulls code from GitHub repository
2. Jenkins installs Prometheus using Helm chart
3. Custom configuration is applied using values.yaml
4. Prometheus is deployed in Kubernetes cluster

## Deployment command (automated via Jenkins)
helm upgrade --install prometheus prometheus-community/kube-prometheus-stack -n monitoring --create-namespace -f values.yaml
