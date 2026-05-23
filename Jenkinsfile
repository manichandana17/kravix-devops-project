pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t chandana172/kravix-project:v1 .'
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker push chandana172/kravix-project:v1'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f configmap.yaml'
                bat 'kubectl apply -f secret.yaml'
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
                bat 'kubectl apply -f ingress.yaml'
            }
        }
    }
}