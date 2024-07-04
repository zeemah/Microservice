pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                script {
                    withKubeCredentials(kubectlCredentials: 
                                        [[caCertificate: '', 
                                          clusterName: 'EKS-2', 
                                          contextName: 'husman@EKS-2.ap-south-1.eksctl.io', 
                                          credentialsId: 'secret-token', 
                                          namespace: 'webapps', 
                                          serverUrl: 'https://9E79FEF4BAE4E842DD8BCA86C32E60E8.gr7.ap-south-1.eks.amazonaws.com']])
                     {
                        sh "kubectl apply -f deployment.yaml"
                    }
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                script {
                    withKubeCredentials(kubectlCredentials: 
                                        [[caCertificate: '', 
                                          clusterName: 'EKS-2', 
                                          contextName: 'husman@EKS-2.ap-south-1.eksctl.io', 
                                          credentialsId: 'secret-token', 
                                          namespace: 'webapps', 
                                          serverUrl: 'https://9E79FEF4BAE4E842DD8BCA86C32E60E8.gr7.ap-south-1.eks.amazonaws.com']])
                    {
                        sh "kubectl get svc -n webapps"
                    }
                }
            }
        }
    }
}
