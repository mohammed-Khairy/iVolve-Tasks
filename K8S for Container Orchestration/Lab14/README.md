#  StatefulSet with Headless Service
This guide provides a step-by-step walkthrough to deploy a StatefulSet with a Headless Service running MySQL on Kubernetes.

---

## Step 1: Create the Database Secret
We secure the MySQL root password by creating a Kubernetes Secret resource.

<img src="Screenshots/1.png" alt="1" width="700">

## Step 2: Configure MySQL Headless Service
To establish fixed network identities for our StatefulSet pods, we create a Headless Service.

Create a file named `mysql-service.yaml`.

<img src="Screenshots/2.png" alt="1" width="300">

Apply the service configuration:

<img src="Screenshots/3.png" alt="1" width="500">

## Step 3: Deploy MySQL Using a StatefulSet
We deploy a stable, stateful instance of MySQL that leverages data persistence and mounts our secret credentials.

Create a file named `mysql-statefulset.yaml`

<img src="Screenshots/4.png" alt="1" width="500">

Apply the StatefulSet:

<img src="Screenshots/5.png" alt="1" width="500">

## Step 4: Deploy the Node.js Web Application
We deploy our custom frontend/backend container application and link it to the MySQL database backend.

Create a file named `app-deployment.yaml`.

<img src="Screenshots/6.png" alt="1" width="500">

Apply the deployment manifest:

<img src="Screenshots/7.png" alt="1" width="500">

## Step 5: Expose the Web Application (NodePort Service)
To access the running application outside the cluster via port 30030, we deploy a standard NodePort service.

Create a file named `app-service.yaml`.

<img src="Screenshots/8.png" alt="1" width="300">

Apply the application service configuration:

<img src="Screenshots/9.png" alt="1" width="500">

## Step 6: Verification and Status Checks
To ensure that both the backend database and frontend web services are fully operational, execute the status command below:

<img src="Screenshots/10.png" alt="1" width="500">

<img src="Screenshots/11.png" alt="1" width="500">

