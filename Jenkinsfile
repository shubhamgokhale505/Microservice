pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeConfig([credentialsId: 'your-credentials-id', serverUrl: 'https://8EBA8D72E981E5BEDAA5CD58AE88D03A.gr7.us-east-1.eks.amazonaws.com']) {
                    sh "kubectl apply -f deployment-service.yml --namespace=webapps"
                }
            }
        }

        stage('Verify Deployments') {
            steps {
                withKubeConfig([credentialsId: 'your-credentials-id', serverUrl: 'https://8EBA8D72E981E5BEDAA5CD58AE88D03A.gr7.us-east-1.eks.amazonaws.com']) {
                    sh "kubectl get all --namespace=webapps"
                }
            }
        }
    }
}
