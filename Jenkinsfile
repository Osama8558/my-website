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
                sh 'docker save osama-portfolio:v4 | docker exec -i osama-cluster-control-plane ctr -n k8s.io images import -'
            }
        }

        stage('Deploy To Kubernetes') {
            steps {
                sh 'docker cp portfolio-deployment.yaml osama-cluster-control-plane:/tmp/portfolio-deployment.yaml'
                sh 'docker exec osama-cluster-control-plane kubectl apply -f /tmp/portfolio-deployment.yaml'
            }
        }
    }
}
