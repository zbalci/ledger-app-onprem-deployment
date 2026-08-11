# Ledger App — On-Premises Deployment

This repository contains the deployment configuration for the on-premises version of **Ledger App**.

The application source code and CI pipeline are maintained separately in [**ledger-app-onprem**](https://github.com/zbalci/ledger-app-onprem).

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
