# Managing Docker Environment Variables Across Build and Runtime
This repository demonstrates how to manage environment variables efficiently across both build time and runtime using Docker. It covers fetching code, using python-slim base image, configuring Flask, and applying three different approaches to inject environment variables (via runtime flags, environment files, and inline Dockerfile configuration).

---
## Step 1: Cloning the Repository

Clone the application source code from GitHub and navigate into the project directory:
```bash
git clone https://github.com/Ibrahim-Adel15/Docker-3.git
cd Docker-3
```
<img src="Screenshots/1.png" alt="1" width="500">

## Step 2: Write the Dockerfile (Initial Setup)
Create a file named `Dockerfile` to configure the Python Flask application. In this initial setup, we will keep it clean from environment variables to test runtime injection first.

<img src="Screenshots/2.png" alt="1" width="500">

## Step 3: Build the Docker Image
Build the base Docker image and name it pythonapp:
```bash
docker build -t pythonapp .
```
<img src="Screenshots/3.png" alt="1" width="500">

## Step 4: [Approach 1] Inject Variables via Runtime Command (-e flag)
Run the first container (container-dev) for the development environment by passing the variables directly in the command line using the -e flag, then test the response:
```bash
docker run -d -p 8080:8080 --name container-dev -e APP_MODE=development -e APP_REGION=us-east pythonapp
curl localhost:8080
```

<img src="Screenshots/4.png" alt="1" width="500">

## Step 5: [Approach 2] Inject Variables via Environment File (.env file)
Create an environment file named staging.env containing the configuration for the staging environment:
```bash
APP_MODE=staging
APP_REGION=us-west
```
Run the second container (container-staging) by passing the filename using the --env-file flag, then test the response:
```bash
docker run -d -p 8081:8080 --name container-staging --env-file staging.env pythonapp
curl localhost:8081
```
<img src="Screenshots/5.png" alt="1" width="500">

## Step 6: [Approach 3] Embed Variables inside the Container (Dockerfile ENV)
Modify the `Dockerfile` to include the production environment variables as built-in defaults using the ENV instruction:

<img src="Screenshots/6.png" alt="1" width="500">


