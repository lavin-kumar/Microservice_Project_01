pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes ') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://F6366963166581BC0D3FF798B1D76405.gr7.ap-south-1.eks.amazonaws.com']]) {
                        sh "kubectl apply -y deployment-service.yml" // some block
                        sleep 60
                }
            }
        }
        
        stage('Verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://F6366963166581BC0D3FF798B1D76405.gr7.ap-south-1.eks.amazonaws.com']]) {
                        sh "kubectl get all -n webapps" // some block
                }
            }
        }
    }
}
