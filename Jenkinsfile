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
                bat '''
                docker stop cicd-app || exit 0
                docker rm cicd-app || exit 0

                docker run -d ^
                --name cicd-app ^
                -p 8081:80 ^
                cicd-app
                '''
            }
        }
    }
}