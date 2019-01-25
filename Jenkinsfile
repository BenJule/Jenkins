pipeline {
    agent none
    stages {
        stage('Prepare/Checkout') {
            steps {
                echo "I don't need no node"
            }
        }
        stage('Syncing Repo') {
             agent {
                 label 'android'
             }
             steps {   
                checkout scm
                sh 'echo from master'
            }
        }
        stage('Syncing Device') {
            agent {
                label 'jfltexx'
            }
            steps {
                sh 'echo from jfltexx'
            }
        }
    }
}
