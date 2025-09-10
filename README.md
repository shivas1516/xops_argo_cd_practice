# Argo CD

This repo contains the Kubernetes **Deployment** and **Service** manifests for the [Java Spring App](https://github.com/shivas1516/xops_docker_practice).

## CI/CD Pipeline
- The `ci.yml` pipeline in the Spring App repo:
  1. Builds a new Docker image
  2. Pushes it to the registry
  3. Updates the [`deployment.yml`](./deployment.yml) in this repo
- Argo CD then syncs the changes from this repo to the Kubernetes cluster.

![ci-pipeline](https://github.com/user-attachments/assets/058d869c-a4e6-4ced-a62d-f426a913e8ab)  
*CI pipeline flow: build → push → update deployment manifest*

## Argo CD
The `firstapp` Argo CD application watches this repo and applies updates automatically whenever `deployment.yml` changes.

![argocd-ui](https://github.com/user-attachments/assets/64b78227-ce23-48ee-bd2e-5fe8482a19d5)  
*Argo CD interface showing sync from repo to Kubernetes cluster*

## Before
![before-1](https://github.com/user-attachments/assets/54ab7a9b-c6d4-471e-a15a-2de38be6e496)  
*Deployment status before the update*  

![before-2](https://github.com/user-attachments/assets/af76d85a-b84c-4b7c-ae2a-41e72e8b314f)  
*Pods running the old image version*

## After
![after-1](https://github.com/user-attachments/assets/288870b8-c791-4d81-ab78-be93058841e2)  
*Deployment status after the update*  

![after-2](https://github.com/user-attachments/assets/686e3446-7c5b-4624-9729-6dc0ba60fe1d)  
*Pods running the new image version*
