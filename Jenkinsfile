pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t osama-portfolio:v4 .'
            }
        }

        stage('Deploy To Kubernetes') {
            steps {
                sh '/snap/bin/kubectl apply -f portfolio-deployment.yaml'
            }
        }
    }
}
