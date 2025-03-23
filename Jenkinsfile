pipeline {
    agent any
    stages {
        stage('Clone Code') {
            steps {
                git 'git@github.com:vncharyhub/AWS_DevOps_Python_Project.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t itschary/flask-app .'
            }
        }
        stage('Push Docker Image') {
            steps {
                withDockerRegistry([credentialsId: 'Dockerhub', url: '']) {
                    sh 'docker push itschary/flask-app'
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
            }
        }
    }
}
