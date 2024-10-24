# demo-webapp Helm Chart
This Helm chart deploys a web application, completely with environment-based database configuration and secrets for Db credentials.

## Prerequisites
- Helm 3.x
- Kubernetes 1.25+ cluster
- NGINX Ingress Controller  # If the ingress resource is set to true in the values.yaml

## Helm Chart Installation

helm install demo-webapp ./demo-webapp --set env.environment=prod --set database.prod.username=myuser --set database.prod.password=mypassword

Note: 
1. Adjust the env.environment, and database credentials according to your environment (e.g. staging, prod)
2. This helm chart is for a image hosted on public repository, so i havent configured the image pull secrets

## Helm Chart Uninstallation
helm uninstall demo-webapp

# Modify values in the values.yaml file to customize as per the environment 
Image name and tag
Pod replicas
Service Port
Database host, name, port
Ingress settings
Resource requests and limits

## Objects created in the Kubernetes cluster 
When this chart is installed, the following Kubernetes objects will be created in your cluster:

Deployment: A Deployment object with a configurable number of replicas and resource limits.
Service: A ClusterIP service exposing the application to the cluster.
Secrets: Database Username and Password: These are stored securely in Kubernetes secrets and are environment-specific.
Ingress: An optional NGINX ingress that routes external traffic to the web application, if ingress is enabled.