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
                docker { image 'nuimk/tn-jenkins-docker-agent' }
            }
            steps {
                sh 'whoami && pwd'
            }
        }
    }
}
