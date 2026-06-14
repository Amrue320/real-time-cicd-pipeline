pipeline {
    agent any

    stages {

        stage('Test') {
            steps {
                bat 'type index.html'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t cicd-app:%BUILD_NUMBER% .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat 'docker rm -f cicd-app-run || exit /b 0'
                bat 'docker run -d --name cicd-app-run -p 8082:80 cicd-app:%BUILD_NUMBER%'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'docker ps'
            }
        }
    }
}
