### **Helm Project (`helmchart-to-deploy-webapp-main`)**

# Helm Chart for Deploying a Web Application

This Helm chart deploys a web application with customizable environment-based database configurations and secrets for database credentials.

## Overview
This Helm chart is designed to deploy a web application into a Kubernetes cluster, with the ability to configure database settings per environment (e.g., staging, production). The application is exposed through an optional NGINX ingress controller.

## Prerequisites
- Helm 3.x
- Kubernetes 1.25+ cluster
- NGINX Ingress Controller (optional, if `ingress.enabled` is set to true)

## Installation
To install the Helm chart, use the following command:
```bash
helm install demo-webapp ./demo-webapp --set env.environment=prod --set database.prod.username=myuser --set database.prod.password=mypassword
```

- Make sure to update the env.environment, database.username, and database.password based on your environment (e.g., staging or production). For private images, configure image pull secrets.

## Uninstallation
To uninstall the chart, run:
```bash
helm uninstall demo-webapp
```

## Customization
Modify the values.yaml file to customize the following:

- Image details: Name, tag, and image pull policy
- Pod settings: Number of replicas, resource requests, and limits
- Database settings: Hostname, name, port, username, and password
- Ingress configuration: Enable or disable ingress, configure hosts, and TLS settings
- Service configuration: Type, ports, and selectors

## Objects Created
- Deployment: A deployment object with configurable replicas and resource limits.
- Service: A ClusterIP service that exposes the application within the cluster.
- Secrets: Stores the database username and password securely as environment-specific Kubernetes secrets.
- Ingress: An optional NGINX ingress to route external traffic to the application (if enabled).

## Testing
To test the deployment:
```bash
kubectl get pods,services,ingress,secrets
```

## Troubleshooting
If ingress is not working, ensure that the NGINX ingress controller is installed.
Verify that all required secrets are correctly configured in Kubernetes.




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
