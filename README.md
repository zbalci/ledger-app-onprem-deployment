# Ledger App — On-Premises Deployment

This repository contains the deployment configuration for the on-premises version of **Ledger App**.

The application source code and CI pipeline are maintained separately in [**ledger-app-onprem**](https://github.com/zbalci/ledger-app-onprem).

<img width="4142" height="1917" alt="cicd-diagram" src="https://github.com/user-attachments/assets/0578e6a7-eda7-4735-a6f7-ef7e53eeafd1" />

## Purpose

Keeping deployment configuration separate from application source code allows environment-specific configuration to be managed independently and prevents deployment changes from being mixed with application development branches.

## Contents

    .
    ├── helm/
    │   ├── Chart.yaml
    │   ├── templates/
    │   ├── values-dev.yaml
    │   └── values-prod.yaml

## GitOps

[**ArgoCD**](https://argo-cd.readthedocs.io/) monitors this repository and synchronizes the desired state with the Kubernetes cluster.

The Helm values files define the environment-specific configuration, including the container image to be deployed.

    Application Repository
            │
            │ CI / Build
            ▼
       Container Image
            │
            ▼
    Deployment Repository
            │
            │ GitOps
            ▼
          ArgoCD
            │
            ▼
       Kubernetes
