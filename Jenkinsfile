pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            sh "kubectl apply -f deployment-service.yml"    
        }
        
        stage('verify Deployment') {
            sh "kubectl get svc -n webapps"
        }
    }
}
