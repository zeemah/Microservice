pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                // withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B7C7C20487B2624AAB0AD54DF1469566.yl4.ap-south-1.eks.amazonaws.com']]) 
                  withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9E79FEF4BAE4E842DD8BCA86C32E60E8.gr7.ap-south-1.eks.amazonaws.com']]) {
                        // some block
                    }
                {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                // withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B7C7C20487B2624AAB0AD54DF1469566.yl4.ap-south-1.eks.amazonaws.com']]) 
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9E79FEF4BAE4E842DD8BCA86C32E60E8.gr7.ap-south-1.eks.amazonaws.com']]) {
                        // some block
                    }
                {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
