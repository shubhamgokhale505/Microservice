pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    withKubeConfig([credentialsId: 'k8-token', serverUrl: 'https://D61B74613E2B3D4FFD2B35BA203A8BE3.gr7.us-east-1.eks.amazonaws.com']) {
                        sh "kubectl apply -f deployment-service.yml --namespace=webapps"
                        // Add a sleep if necessary
                        sleep time: 30, unit: 'SECONDS'
                    }
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    withKubeConfig([credentialsId: 'k8-token', serverUrl: 'https://D61B74613E2B3D4FFD2B35BA203A8BE3.gr7.us-east-1.eks.amazonaws.com']) {
                        sh "kubectl get svc -n webapps"
                    }
                }
            }
        }
    }
}
