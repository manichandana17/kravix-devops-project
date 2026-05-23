pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/manichandana17/kravix-devops-project.git'
            }
        }

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
        bat '''
        set KUBECONFIG=C:\\ProgramData\\Jenkins\\.kube\\config
        kubectl apply -f configmap.yaml --validate=false
        kubectl apply -f secret.yaml --validate=false
        kubectl apply -f deployment.yaml --validate=false
        kubectl apply -f service.yaml --validate=false
        kubectl apply -f ingress.yaml --validate=false
        '''
    }
}    }
}