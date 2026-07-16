# Persistent Storage Setup for Application Logging

This repository contains the Kubernetes manifests and step-by-step instructions to set up persistent storage using a **Persistent Volume (PV)** and a **Persistent Volume Claim (PVC)** for application logging.

---

## Step 1: Define the Persistent Volume (PV) Manifest
Create a file named `log-pv.yaml` to define a Persistent Volume. This volume allocates `1Gi` of storage using a `hostPath` on the host system at `/mnt/app-logs` with a `Retain` reclaim policy.

<img src="Screenshots/1.png" alt="1" width="500">

## Step 2: Define the Persistent Volume Claim (PVC) Manifest
Create a file named log-pvc.yaml to define a Persistent Volume Claim that requests 1Gi of storage with an access mode matching the PV (ReadWriteMany).

<img src="Screenshots/2.png" alt="1" width="500">

## Step 3: Apply the Manifests to the Cluster
Deploy both resources to your Kubernetes cluster using kubectl apply:

<img src="Screenshots/3.png" alt="1" width="500">

## Step 4: Verify the Persistent Volume (PV)
Check the status of the created Persistent Volume. It should show a status of Bound and be linked to your PVC.

<img src="Screenshots/4.png" alt="1" width="800">

## Step 5: Verify the Persistent Volume Claim (PVC)
Confirm that the Persistent Volume Claim has successfully bound to the volume.

<img src="Screenshots/5.png" alt="1" width="800">
