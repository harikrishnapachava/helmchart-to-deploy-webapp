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
