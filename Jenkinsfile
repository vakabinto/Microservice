pipeline {
    agent any

    stages {
        stage(' KUBERNETES') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-lad', contextName: '', credentialsId: 'k8s-cred', namespace: 'webapps', serverUrl: 'https://20D55E1CCB3EF2039457B6FFBE82BE6A.gr7.us-east-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
                  sleep 60
                }
            }
        }
        stage('DEPLOY TO KUBERNETES') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-lad', contextName: '', credentialsId: 'k8s-cred', namespace: 'webapps', serverUrl: 'https://20D55E1CCB3EF2039457B6FFBE82BE6A.gr7.us-east-1.eks.amazonaws.com']]) {
                  sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
