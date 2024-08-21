pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://A02375881BACA7128B2D89414B7203F9.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://A02375881BACA7128B2D89414B7203F9.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
