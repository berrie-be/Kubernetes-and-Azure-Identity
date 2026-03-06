# AKS Workload Identity Explained

This document explains Azure Kubernetes Service (AKS) Workload Identity from beginner level to practical setup.

It covers:

- Why Workload Identity is needed
- Core components involved
- Step-by-step setup
- Runtime authentication flow
- Why both federated credential and service account annotation are required

---

## 1. The Problem Workload Identity Solves

Applications running inside AKS pods often need to access Azure services such as:

- Azure Key Vault
- Azure Storage
- Azure OpenAI
- Azure SQL
- Azure Service Bus

Azure requires authentication before allowing access.

However, pods do not have an Azure identity by default.

A common but insecure approach is to store credentials like:

```text
CLIENT_ID
CLIENT_SECRET
TENANT_ID
```

---

## Problems with this approach  
Secrets can leak
Credentials must be rotated
Higher security risk
Increased operational overhead
Workload Identity solves this by allowing pods to authenticate to Azure without storing secrets.
