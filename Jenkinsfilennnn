pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                sh "kubectl apply -f deployment-service.yml"
            }
        }
        
        stage('Verify Deployment') {
            steps {
                sh "kubectl get svc -n webapps"
            }
        }
    }
}
