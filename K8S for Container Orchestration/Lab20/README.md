# Securing Kubernetes with RBAC and Service Accounts
This repository is a step-by-step practical guide for configuring Role-Based Access Control (RBAC) and Service Accounts in Kubernetes. In this lab, we will create a dedicated Service Account named `jenkins-sa` within the `ivolve` namespace, generate an authentication token, define a Role named `pod-reader` granting read-only permissions (`get`, `list`) exclusively for Pods, bind the Role to the Service Account using a `RoleBinding`, and finally validate that the Service Account is restricted to only listing Pods without any unauthorized access.

---
## Step 1: Create the Manifest File (rbac-lab.yaml)
Create a unified declarative manifest containing all RBAC objects

<img src="Screenshots/1.png" alt="1" width="500">
