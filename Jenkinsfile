pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: 
                                   [[caCertificate: 'LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURCVENDQWUyZ0F3SUJBZ0lJTDRRdEs1dmpLd013RFFZSktvWklodmNOQVFFTEJRQXdGVEVUTUJFR0ExVUUKQXhNS2EzVmlaWEp1WlhSbGN6QWVGdzB5TkRBM01EUXhNalF3TXpkYUZ3MHpOREEzTURJeE1qUTFNemRhTUJVeApFekFSQmdOVkJBTVRDbXQxWW1WeWJtVjBaWE13Z2dFaU1BMEdDU3FHU0liM0RRRUJBUVVBQTRJQkR3QXdnZ0VLCkFvSUJBUUNsR2FtWmFYZDJUd0orSHZnRlV3T3lJcTNDZHVWTEd6UEZvSk93a1BjUlhsdFRhL09IVkl1NXVscGYKYW5MR240ak5HbzBoMGp4WVFzcEp2MEFUMDlTZWpTNFZvMER1d2V5ZXdnWkk0Y21oWmJQUjh1cnJDeGUxMU1tbwpPc0NtdWlPME1HNkgxMUt2R0FyMm9ETlVqOGR5NmdXT3k4Z3VwWHIwUmQwd09xUUlyR2dGd1E4dVB0VEwydCtEClFiTkgzTnAxbVFQN2dNM1k4M1RZeUdSNUVydFQxTkRFcVNReVVqaGlOdUpNNjI2blhuenNtSi9TcTkxTHJzcmgKWlYyV0Jwa2ZDeHN1NGZYUDVYVkN5WVh4ckcvdVN1OVNhaVFjaHBDSzNZRGhFbjRkem04aHFKNUM3SlpMUUgrQgpyTGdxYnZvQmRNV00zci95bUdQSTVaR0gva2d4QWdNQkFBR2pXVEJYTUE0R0ExVWREd0VCL3dRRUF3SUNwREFQCkJnTlZIUk1CQWY4RUJUQURBUUgvTUIwR0ExVWREZ1FXQkJRWkpjV3pyL1hOMEZ6SW5aT1pmamFBK1luRTVEQVYKQmdOVkhSRUVEakFNZ2dwcmRXSmxjbTVsZEdWek1BMEdDU3FHU0liM0RRRUJDd1VBQTRJQkFRQURWS3E4WUFuOAo5UjcvNnFvTlI2Sncva0pCOU5HYVA4L2lTMTFpdEpYMFNIa1ZTYTJPZ0xUa3RPdnY3QUtjUzRINjFoUXNmSVZYCm4zN1lOcTllOHU0eStLZTJBMjNyOStqUkw2ZkpVc0NkZ25lSk9uV2ZqdGxZSTg3ZmNELzBFQWowcDlNWGt0K0wKMnJYaFQ0UnpSTnJwVk9acUh2ZmllMmt1M2V0SFBad0p5WFA0WkFlcUx6MGV1SkRUa1Z1Y2hock9kTXJwSkh3bgpWNW0xSlNqMlN4dStHd2xUcHZ5MGI5WEdSV0tmNGJHM2YrRHMyOHpEWVpmdmMxS1BhLzJGY3pkaUFmblZiN2Y1Cks4QktNVWtNTmFHSXV4MGpyMzE1UUNwM3g0bzdjWmZnWFh3SmFidE5ONlRweDNKenVrbTErS3FjdEx6RmZRaWoKc25HVVZMMERDTHZyCi0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K', 
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
                                   [[caCertificate: 'LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURCVENDQWUyZ0F3SUJBZ0lJTDRRdEs1dmpLd013RFFZSktvWklodmNOQVFFTEJRQXdGVEVUTUJFR0ExVUUKQXhNS2EzVmlaWEp1WlhSbGN6QWVGdzB5TkRBM01EUXhNalF3TXpkYUZ3MHpOREEzTURJeE1qUTFNemRhTUJVeApFekFSQmdOVkJBTVRDbXQxWW1WeWJtVjBaWE13Z2dFaU1BMEdDU3FHU0liM0RRRUJBUVVBQTRJQkR3QXdnZ0VLCkFvSUJBUUNsR2FtWmFYZDJUd0orSHZnRlV3T3lJcTNDZHVWTEd6UEZvSk93a1BjUlhsdFRhL09IVkl1NXVscGYKYW5MR240ak5HbzBoMGp4WVFzcEp2MEFUMDlTZWpTNFZvMER1d2V5ZXdnWkk0Y21oWmJQUjh1cnJDeGUxMU1tbwpPc0NtdWlPME1HNkgxMUt2R0FyMm9ETlVqOGR5NmdXT3k4Z3VwWHIwUmQwd09xUUlyR2dGd1E4dVB0VEwydCtEClFiTkgzTnAxbVFQN2dNM1k4M1RZeUdSNUVydFQxTkRFcVNReVVqaGlOdUpNNjI2blhuenNtSi9TcTkxTHJzcmgKWlYyV0Jwa2ZDeHN1NGZYUDVYVkN5WVh4ckcvdVN1OVNhaVFjaHBDSzNZRGhFbjRkem04aHFKNUM3SlpMUUgrQgpyTGdxYnZvQmRNV00zci95bUdQSTVaR0gva2d4QWdNQkFBR2pXVEJYTUE0R0ExVWREd0VCL3dRRUF3SUNwREFQCkJnTlZIUk1CQWY4RUJUQURBUUgvTUIwR0ExVWREZ1FXQkJRWkpjV3pyL1hOMEZ6SW5aT1pmamFBK1luRTVEQVYKQmdOVkhSRUVEakFNZ2dwcmRXSmxjbTVsZEdWek1BMEdDU3FHU0liM0RRRUJDd1VBQTRJQkFRQURWS3E4WUFuOAo5UjcvNnFvTlI2Sncva0pCOU5HYVA4L2lTMTFpdEpYMFNIa1ZTYTJPZ0xUa3RPdnY3QUtjUzRINjFoUXNmSVZYCm4zN1lOcTllOHU0eStLZTJBMjNyOStqUkw2ZkpVc0NkZ25lSk9uV2ZqdGxZSTg3ZmNELzBFQWowcDlNWGt0K0wKMnJYaFQ0UnpSTnJwVk9acUh2ZmllMmt1M2V0SFBad0p5WFA0WkFlcUx6MGV1SkRUa1Z1Y2hock9kTXJwSkh3bgpWNW0xSlNqMlN4dStHd2xUcHZ5MGI5WEdSV0tmNGJHM2YrRHMyOHpEWVpmdmMxS1BhLzJGY3pkaUFmblZiN2Y1Cks4QktNVWtNTmFHSXV4MGpyMzE1UUNwM3g0bzdjWmZnWFh3SmFidE5ONlRweDNKenVrbTErS3FjdEx6RmZRaWoKc25HVVZMMERDTHZyCi0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K', 
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
