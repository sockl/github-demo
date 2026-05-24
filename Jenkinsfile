pipeline {
    agent any
    stages {
        stage('Verify') {
            steps {
                sh 'dir'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sockl/github-demo:latest .'
            }
        }
        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                    sh 'docker push sockl/github-demo:latest'
                }
            }
        }
    }
}
