# Real-Time CI/CD Pipeline Using Jenkins and Docker

## Project Overview

This project demonstrates a complete CI/CD (Continuous Integration and Continuous Deployment) pipeline using Jenkins, GitHub, and Docker.

Whenever code is pushed to the GitHub repository, Jenkins pulls the latest code, builds a Docker image, and deploys the application inside a Docker container.

## Architecture

```text
Developer
    ↓
Git Push
    ↓
GitHub Repository
    ↓
Jenkins Pipeline
    ↓
Docker Build
    ↓
Docker Container Deployment
    ↓
Application Running on localhost:8082
```

## Technologies Used

* Jenkins
* Docker
* Git
* GitHub
* Nginx
* CI/CD Pipeline
* Windows

## Project Structure

```text
real-time-cicd-pipeline/
│
├── Jenkinsfile
├── Dockerfile
├── index.html
└── README.md
```

## Pipeline Stages

### Stage 1: Source Code Checkout

Jenkins fetches the latest code from the GitHub repository.

### Stage 2: Build Docker Image

Docker image is built automatically using the Dockerfile.

```bash
docker build -t cicd-app .
```

### Stage 3: Deploy Container

Existing container is removed and a new container is deployed automatically.

```bash
docker rm -f cicd-app-run
docker run -d --name cicd-app-run -p 8082:80 cicd-app
```

## Dockerfile

```dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
```

## Jenkins Pipeline

```groovy
pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t cicd-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat 'docker rm -f cicd-app-run || exit /b 0'
                bat 'docker run -d --name cicd-app-run -p 8082:80 cicd-app'
            }
        }
    }
}
```

## Features

* Automated CI/CD pipeline
* GitHub integration
* Docker image creation
* Automated container deployment
* Jenkins Pipeline as Code
* Real-time application deployment

## Learning Outcomes

Through this project I gained hands-on experience with:

* Jenkins Pipeline
* Docker containerization
* Git and GitHub integration
* Continuous Integration
* Continuous Deployment
* DevOps automation workflows

## Features:
✔ Automated CI/CD pipeline
✔ Docker image versioning using Jenkins Build Number
✔ Automated deployment
✔ Deployment verification
✔ GitHub integration
✔ Jenkins Pipeline as Code

## Author

Amruthesh S P

DevOps & Cloud Engineering Enthusiast
