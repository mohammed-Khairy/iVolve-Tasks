# Containerized Node.js and MySQL Stack Using Docker Compose

This repository contains a containerized Node.js web application connected to a MySQL database backend, configured and managed using Docker Compose.

---

## step 1: Clone the Repository
Clone the application source code and navigate into the project directory:

<img src="Screenshots/1.png" alt="1" width="500">

## step 2: Configure Environment Variables (.env)
To ensure sensitive data (like database credentials) are kept secure and decoupled from the infrastructure setup,
- create a `.env` file in the project's root directory 
- Add the environment variables inside the .env file:
  
<img src="Screenshots/2.png" alt="1" width="500">

## step 3: Configure Docker Compose
Create a `docker-compose.yml` file in the root directory. Docker Compose will automatically read the variables from the `.env` file created in the previous step:

<img src="Screenshots/3.png" alt="1" width="350">

## step 4: Build and Run the Stack
Start the services in detached mode using Docker Compose:

<img src="Screenshots/4.png" alt="1" width="350">

To verify that both containers are successfully running, use:
```bash
docker-compose ps
```
<img src="Screenshots/5.png" alt="1" width="500">

## step 5: Check Health and Readiness Endpoints
Test the application's health status and readiness checks:

<img src="Screenshots/6.png" alt="1" width="500">

