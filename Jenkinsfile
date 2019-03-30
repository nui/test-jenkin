pipeline {
    agent none
    stages {
        stage('Back-end') {
            agent {
                docker { image 'node:8-alpine' }
            }
            steps {
                sh 'node --version'
            }
        }
        stage('Front-end') {
            agent {
                docker {
                    image 'nuimk/tn-jenkins-docker-agent'
                    alwaysPull true
                }
            }
            steps {
                withCredentials([file(credentialsId: 'edfe3042-a622-4a62-bae8-ef9cbdff4561', variable: 'KUBECONFIG')]) {
                    sh 'kubectl get pod'
                }
            }
        }
    }
}
