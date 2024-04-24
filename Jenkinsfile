pipeline {
    agent any

    stages {
        stage('Deploy') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://A230DAF41E95CC3915B8115B58086864.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh 'kubectl apply -f deployment-service.yml'
                    sleep 60
                }
            }
        }
        
        stage('Hello') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://A230DAF41E95CC3915B8115B58086864.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh 'kubectl get all -n webapps'
                }
            }
        }
    }
}
