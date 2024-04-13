pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'https://8EBA8D72E981E5BEDAA5CD58AE88D03A.gr7.us-east-1.eks.amazonaws.com']]) {
                 sh "kubectl apply -f deployment-service.yml"
               }
            }
        }
        
        stages {
        stage('Verify Deployments') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'https://8EBA8D72E981E5BEDAA5CD58AE88D03A.gr7.us-east-1.eks.amazonaws.com']]) {
                 sh "kubectl get all -n webapps"
           }
       }
    }
}

