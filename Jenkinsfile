pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                script {
                    def serverUrl = 'https://9E79FEF4BAE4E842DD8BCA86C32E60E8.gr7.ap-south-1.eks.amazonaws.com'
                    def namespace = 'webapps'
                    def credentialsId = 'secret-token'
                    
                    def token = credentials(credentialsId)
                    
                    withKubeConfig(
                        credentialsId: credentialsId,
                        serverUrl: serverUrl,
                        namespace: namespace,
                        kubeconfigId: ''
                    ) {
                        sh "kubectl apply -f deployment.yaml"
                    }
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                script {
                    def serverUrl = 'https://9E79FEF4BAE4E842DD8BCA86C32E60E8.gr7.ap-south-1.eks.amazonaws.com'
                    def namespace = 'webapps'
                    def credentialsId = 'secret-token'
                    

                    def token = credentials(credentialsId)
                    
                    withKubeConfig(
                        credentialsId: credentialsId,
                        serverUrl: serverUrl,
                        namespace: namespace,
                        kubeconfigId: ''
                    ) {
                        sh "kubectl get svc -n webapps"
                    }
                }
            }
        }
    }
}
