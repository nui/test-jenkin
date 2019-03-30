pipeline {
    agent none
    stages {
        stage('Back-end') {
            agent {
                docker { image 'node:8-alpine' }
            }
            steps {
                withCredentials([file(credentialsId: 'edfe3042-a622-4a62-bae8-ef9cbdff4561', variable: 'FILE')]) {
                    sh 'echo $FILE'
                }
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
