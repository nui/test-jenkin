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
                    args '-v $HOME/.kube:/.kube -e KUBECONFIG=/.kube/config'
                    alwaysPull true
                }
            }
            steps {
                sh 'kubectl get pod'
            }
        }
    }
}
