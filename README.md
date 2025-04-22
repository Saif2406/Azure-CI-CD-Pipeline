# Azure-CI-CD-Pipeline
The Azure CI/CD pipeline automates the build, test, and deployment of a multi-microservice application (Python, .NET, Node.js) using Azure DevOps, ACR, AKS, and GitOps (Argo CD)
![Azure CICD Architecture](https://github.com/user-attachments/assets/5a3d0b8b-eb90-4e7f-ae46-1e1516ad2d19)

**Summary of Azure CI/CD Pipeline**

The Azure CI/CD pipeline automates the build, test, and deployment of a multi-microservice application (Python, .NET, Node.js) using Azure DevOps, ACR, AKS, and GitOps (Argo CD). Here’s the workflow:

**Architecture Overview**
1.	Components:
   o	Azure Repos: Hosts source code for microservices (voting app, worker, results).
   o	CI Pipeline: Builds Docker images for each microservice and pushes them to Azure Container Registry (ACR).
   o	AKS Cluster: Hosts the deployed application.
   o	GitOps (Argo CD): Monitors the Git repository for Kubernetes manifest changes and auto-deploys updates to AKS.
  	
2.	Workflow:
 o	Continuous Integration (CI):
   	Triggered by code commits to Azure Repos.
   	Builds Docker images for each microservice (Python, .NET, Node.js).
   	Pushes images to ACR with dynamic tags (e.g., voting-app:65).
 o	Continuous Delivery (CD):
   	Update Stage: A shell script updates Kubernetes manifests in Git with the new image tag.
   	Argo CD: Detects Git changes and deploys the updated manifests to AKS.
  	
3.	Key Tools:
   o	Azure Pipelines: For CI stages (build, push, update).
   o	ACR: Stores Docker images.
   o	AKS: Kubernetes cluster for deployment.
   o	Argo CD: GitOps tool for declarative Kubernetes deployments.

4. Azure Repos → CI Pipeline → ACR → GitOps (Argo CD) → AKS.
