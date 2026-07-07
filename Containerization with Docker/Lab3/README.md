
# Dockerized Spring Boot Application

This repository demonstrates the containerization of a Spring Boot application using Docker. It covers building a custom Docker image, managing multi-architecture scenarios, configuring container port mapping, and testing the application lifecycle in isolated environments.

---

##  Step 1: Cloning the Repository


Clone the source code from GitHub:
```bash
git clone https://github.com/Ibrahim-Adel15/Docker-1.git
cd Docker-1
```
<img src="Screenshots/1.png" alt="1" width="500">

##  Step 2: Write the Dockerfile
Create a file named Dockerfile and add the following content:

<img src="Screenshots/2.png" alt="1" width="500">

## Step 3: Build the app1 Image
Execute the build command and to check the image size run:
```bash
docker build -t app1 .
docker images
```
<img src="Screenshots/3.png" alt="1" width="500">
<img src="Screenshots/4.png" alt="1" width="500">


## Step 4: Run container1 from app1 Image
Run the container in detached mode (-d) and map the host's port 77 (or 8080) to the container's internal port 8080:
```bash
docker run -d --name container1 -p 77:8080 app1
```
<img src="Screenshots/5.png" alt="1" width="500">

## step 5: Test the Application
Verify that the Spring Boot application is serving traffic successfully:

<img src="Screenshots/6.png" alt="1" width="500">

