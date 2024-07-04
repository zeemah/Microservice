pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: 
                                   [[caCertificate: '', 
                                     clusterName: 'EKS-2', 
                                     contextName: '', 
                                     credentialsId: 'k8-token', 
                                     namespace: 'webapps', 
                                     serverUrl: 'https://9E79FEF4BAE4E842DD8BCA86C32E60E8.gr7.ap-south-1.eks.amazonaws.com']]) 
                 {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: 
                                   [[caCertificate: '', 
                                     clusterName: 'EKS-2', 
                                     contextName: '', 
                                     credentialsId: 'k8-token', 
                                     namespace: 'webapps', 
                                     serverUrl: 'https://9E79FEF4BAE4E842DD8BCA86C32E60E8.gr7.ap-south-1.eks.amazonaws.com']]) 
                 {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
