pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-cluster-1 ', contextName: '', credentialsId: 'k8s-token', namespace: 'jai', serverUrl: 'https://46D4F487BBD8CA258AD04BCC5E9D6842.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-cluster-1', contextName: '', credentialsId: 'k8s-token', namespace: 'jai', serverUrl: 'https://46D4F487BBD8CA258AD04BCC5E9D6842.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n jai"
                }
            }
        }
    }
}
