
# Jenkins Pipeline for Application Deployment
This lab demonstrates an automated CI/CD pipeline using **Jenkins**, **Docker**, and **Kubernetes**. The pipeline clones the application repository, executes unit tests, builds the application, packages it into a Docker image, pushes the image to Docker Hub, updates the deployment manifest with the dynamic build tag, and deploys the updated workload to a Kubernetes cluster.

---

## Step 1: Clone the Repository
Clone the application source code and Dockerfile to inspect the project structure.

```bash
git clone https://github.com/ahmeddhussain/ivolve-jenkins-1.git
cd ivolve-jenkins-1
```
## Step 2: Create a file named `Jenkinsfile` at the root of your GitHub repository and paste the following code:
```bash
pipeline {
    agent any
    tools {
        maven 'Maven3'
    }
    environment {
        DOCKERHUB_CREDS = credentials('docker')
        IMAGE_NAME      = "khairyops/jenkins-app"
        IMAGE_TAG       = "${BUILD_NUMBER}"
        JAR_NAME        = "demo-0.0.1-SNAPSHOT.jar"
    }

    stages {

        stage('Run Unit Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Build App') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
            post {
                success {
                    sh "ls -la target/${JAR_NAME}"
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                sh """
                    echo \$DOCKERHUB_CREDS_PSW | docker login -u \$DOCKERHUB_CREDS_USR --password-stdin
                    docker push ${IMAGE_NAME}:${IMAGE_TAG}
                """
            }
        }

        stage('Delete Image Locally') {
            steps {
                sh "docker rmi ${IMAGE_NAME}:${IMAGE_TAG}"
            }
        }

        stage('Update deployment.yaml') {
            steps {
                sh "sed -i 's|image:.*|image: ${IMAGE_NAME}:${IMAGE_TAG}|' deployment.yaml"
            }
        }

        stage('Deploy to K8s Cluster') {
            steps {
                withCredentials([file(credentialsId: 'jenkins-sa-token', variable: 'SA_TOKEN_FILE')]) {
                    sh '''
                        kubectl apply -f deployment.yaml \
                          --server=https://<K8S_API_SERVER>:6443 \
                          --insecure-skip-tls-verify=true \
                          --token=$(cat $SA_TOKEN_FILE) \
                          -n ivolve
                    '''
                }
            }
        }
    }

    post {
        always {
            sh 'docker logout || true'
        }
        success {
            echo 'Pipeline completed successfully — deployment finished.'
        }
        failure {
            echo 'Pipeline failed — check the stage logs above.'
        }
    }
}
```

## Step 3: Add Required Credentials in Jenkins
Go to Jenkins Dashboard > Manage Jenkins > Credentials.

Add Docker Hub credentials (Username with password) with ID: docker-hub-credentials.

Add Kubeconfig configuration with ID: kubeconfig-credentials.

## Step 3: Create Jenkins Pipeline Job
In Jenkins Dashboard, click New Item.

Enter Lab22-Jenkins-Pipeline as the item name, select Pipeline, and click OK.

Under the Pipeline configuration section:

Definition: Pipeline script from SCM

SCM: Git

Repository URL: https://github.com/Ibrahim-Adel15/Jenkins_App.git

Script Path: Jenkinsfile

Click Save.
