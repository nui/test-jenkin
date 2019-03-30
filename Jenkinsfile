pipeline {
    agent none
    stages {
        stage('Back-end') {
            agent {
                docker { image 'node:8-alpine' }
            }
            steps {
                withCredentials([file(credentialsId: 'edfe3042-a622-4a62-bae8-ef9cbdff4561', variable: 'FILE')]) {
                    sh 'cat $FILE'
                }
            }
        }
        stage('Front-end') {
            withCredentials([file(credentialsId: 'edfe3042-a622-4a62-bae8-ef9cbdff4561', variable: 'FILE')]) {
                agent {
                    docker {
                        image 'nuimk/tn-jenkins-docker-agent'
                        args '-v $FILE:/.kube/.config -e KUBECONFIG=/.kube/config'
                        alwaysPull true
                    }
                }
                steps {
                    sh 'kubectl get pod'
                }
            }
        }
    }
}
