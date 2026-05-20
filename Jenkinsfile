pipeline {
    agent any
    stages {
        stage('Verify') {
            steps {
                bat 'dir'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t sockl/github-demo:latest .'
            }
        }
        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    bat 'docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%'
                    bat 'docker push sockl/github-demo:latest'
                }
            }
        }
    }
}
