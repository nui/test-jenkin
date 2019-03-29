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
                    args '-v $HOME/.kube:/root/.kube -e KUBECONFIG=/root/.kube/config --pull'
                }
            }
            steps {
                sh 'kubectl get pod'
            }
        }
    }
}
