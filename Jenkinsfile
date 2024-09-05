pipeline {
    agent any

    stages {
        stage('Deploy to Kubernets') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'balraj-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://7A88D591B76582F68E890F414CBE194C.gr7.us-east-1.eks.amazonaws.com']]) {
                     sh "kubectl apply -f deployment-service.yml"
                     sleep 60
               }
            }
        }    
  
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'balraj-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://7A88D591B76582F68E890F414CBE194C.gr7.us-east-1.eks.amazonaws.com']]) {
                     sh "kubectl get svc -n webapps"
                }
            }
        }
      }
    }
