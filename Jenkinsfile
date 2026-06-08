pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Repository checked out'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                export KUBECONFIG=/var/jenkins_home/kubeconfig

                kubectl apply -f deployment.yaml
                kubectl apply -f service.yaml
                '''
            }
        }

        stage('Verify') {
            steps {
                sh '''
                export KUBECONFIG=/var/jenkins_home/kubeconfig

                kubectl get pods
                kubectl get svc
                '''
            }
        }
    }
}
