Helm Knowledge Base
----------------------------------
In a Helm chart's Chart.yaml file:

- version: This is the version of the Helm chart itself. It's used to track changes to the chart, and it's Mandatory.
- appVersion: This is the version of the application being deployed by the Helm chart. It's optional, but recommended if you want to track the version of the application separately from the chart version.

You can use these versions in various ways during upgrades:

- helm upgrade: You can specify the --set flag to update the appVersion or version values during an upgrade. For example: helm upgrade demo-webapp --set appVersion=1.1
- helm history: You can view the history of upgrades and see the versions of the chart and application that were deployed at each step.
- helm status: You can view the current status of the deployment, including the versions of the chart and application.

It's a good practice to increment the version field whenever you make changes to the Helm chart, and increment the appVersion field whenever you make changes to the application being deployed.

Here's an example of how you might use these versions in your Chart.yaml file:

apiVersion: v2
name: demo-webapp
description: A Helm chart for deploying a web application
version: 0.2.0
appVersion: "1.1"

In this example, the Helm chart version is 0.2.0, and the application version is 1.1. When you make changes to the chart, you would increment the version field, and when you make changes to the application, you would increment the appVersion field.



Commands
---------------------
-  Creating a Helm Chart, Initialize a new Helm chart directory:
helm create demo-webapp

- Edit the chart.yaml file to set the chart's name, version, and description:
apiVersion: v2
name: demo-webapp
description: A Helm chart for deploying a web application
version: 0.2.0

- Create a templates/deployment.yaml file and other required files to define the deployment:

- Package the chart:
helm package demo-webapp

- Install the chart:
helm install demo-webapp demo-webapp.tgz

- helm status: You can view the current status of the deployment, including the versions of the chart and application.

- Updating the chart and creating new chart archive
Increment the version number: Whenever you make changes to the Helm chart, increment the version number in the Chart.yaml file. For example, if you start with version: 0.1.0, you can increment it to version: 0.2.0 for the next release.

Use helm package to create a chart archive*: Run the below command to create a chart archive file (demo-webapp-0.2.0.tgz) that includes the updated chart.
helm package demo-webapp  # create a chart archive file (demo-webapp-0.2.0.tgz) that includes the updated chart.

- Helm Upgrade
Use helm upgrade to upgrade the chart*: To upgrade the chart in your Kubernetes cluster, run the command 
helm upgrade demo-webapp demo-webapp-0.2.0.tgz # This will upgrade the chart to the new version.

- Helm History
Use helm history to view the version history*: Run the command
helm history demo-webapp # to view the version history of the chart, including the current version and previous versions. 
 
- Helm Rollback 
Use helm rollback to rollback to a previous version*: If you need to rollback to a previous version, run the command 
helm rollback demo-webapp <previous-version>.

Some additional commands that might be helpful:
- helm lint: Validate the Helm chart for errors and warnings.
- helm template: Generate the Kubernetes manifest files from the Helm chart.
- helm dependency update: Update the dependencies of the Helm chart.
- helm show: Show information about a Helm chart, including its version and dependencies.
- helm diff: command to preview the changes before upgrading.