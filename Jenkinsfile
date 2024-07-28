pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://BF2A70568C0096D966C802D3A9443DD2.gr7.ap-south-1.eks.amazonaws.com']]) {                
                   sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://BF2A70568C0096D966C802D3A9443DD2.gr7.ap-south-1.eks.amazonaws.com']]) {                
                   sh "kubectl get svc -n webapps"
            }
        }
    }
}
