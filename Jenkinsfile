pipeline {
    agent any 

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-TB5', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8A0930EB715F9D188F788798DA44C4C9.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                 }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-TB5', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8A0930EB715F9D188F788798DA44C4C9.gr7.us-east-1.eks.amazonaws.com']]) {
                     sh "kubectl get svc -n webapps"
                  }
            }
        }
    }
}
