pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t jenkin-microservice .'
            }
        }
        stage('Deploy Microservice to eks') {
            steps {
                sh "aws eks update-kubeconfig --region us-east-1 --name eks"
                sh 'kubectl apply -f k8s-deployment.yaml'
                sh 'kubectl get pods'
            }
        }
    }
}
