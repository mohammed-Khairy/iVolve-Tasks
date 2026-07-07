Dockerized Spring Boot Application
This repository demonstrates the containerization of a Spring Boot application using Docker. It covers building a custom Docker image, managing multi-architecture scenarios, configuring container port mapping, and testing the application lifecycle in isolated environments.

🚀 Features & Concepts Covered
Custom Dockerfile Creation: Standardizing images for Java-based Spring Boot artifacts.

Port Forwarding & Mapping: Binding internal container ports to host machine interfaces for external traffic accessibility.

Container Lifecycle Management: Resolving application state conflicts, container reuse, and cleaning up legacy resources.

Cloud Playground Networking: Accessing exposed services through reverse-proxy architectures on interactive learning platforms.

📁 Repository Structure
Plaintext
.
├── Dockerfile          # Docker configuration instructions
├── target/
│   └── app1.jar        # Compiled Spring Boot executable JAR file
└── README.md           # Project documentation
🛠️ Step-by-Step Implementation
1. The Dockerfile Configuration
The application is containerized using a standardized Dockerfile. Ensure the file is named exactly Dockerfile (case-sensitive, with no extension) to allow the Docker engine to auto-detect it.

Dockerfile
# Use an official OpenJDK runtime as a parent image
FROM openjdk:17-jdk-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the executable JAR into the container
COPY target/app1.jar app.jar

# Expose the application's internal port
EXPOSE 8080

# Execute the application
ENTRYPOINT ["java", "-jar", "app.jar"]
2. Building the Docker Image
To build the Docker image with the tag app1:latest, navigate to the root directory containing the Dockerfile and execute:

Bash
docker build -t app1 .
(Note: If you use a non-standard name like Dockerfile.dev, append the -f flag: docker build -f Dockerfile.dev -t app1 .)

3. Running the Container & Port Mapping
To deploy the application securely, map an available host port to the container's internal application port (8080).

Run the container in detached mode (-d) and map it to host port 77:

Bash
docker run -d --name container1 -p 77:8080 app1
If you encounter a naming conflict error (Conflict. The container name "/container1" is already in use...), remove the legacy container first before spinning up the new instance:

Bash
# Force remove the conflicting container
docker rm -f container1

# Re-run with the updated port configuration
docker run -d --name container1 -p 77:8080 app1
🌐 Verification and Testing
Inside the Host Environment
Verify that the application is running and responding locally within the host by executing a curl command against the mapped host port (77):

Bash
curl http://localhost:77
Expected Response Output:

Plaintext
Hello from Dockerized Spring Boot!
Accessing via the Browser (Cloud Environments)
When running inside isolated lab environments like Killercoda or LabEx, internal ports are isolated from your local machine's web browser. To access the web interface externally:

Navigate to the interface panel or use the Traffic / Ports extension tab.

Request a public endpoint mapping for port 77.

The platform generates an authenticated reverse-proxy URL, rendering the Spring Boot web app natively on your browser.
