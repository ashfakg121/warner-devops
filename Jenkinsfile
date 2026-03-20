pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'cd warnerapp && docker build -t warner-django .'
            }
        }

        stage('Load Image to Minikube') {
            steps {
                sh 'minikube image load warner-django'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'cd warnerapp && kubectl apply -f deployment.yaml'
                sh 'cd warnerapp && kubectl apply -f service.yaml'
            }
        }

    }
}
