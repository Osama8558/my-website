pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t osama-portfolio:v4 .'
            }
        }

        stage('Load Image Into Kind') {
            steps {
                sh '/usr/local/bin/kind load docker-image osama-portfolio:v4 --name osama-cluster'
            }
        }

        stage('Deploy To Kubernetes') {
            steps {
                sh 'kubectl apply -f portfolio-deployment.yaml'
            }
        }

    }
}
