pipeline {
    agent none
    stages {
        stage('Prepare/Checkout') {
            steps {
                echo "I don't need no node"
            }
        }
        stage('build') {
             agent {
                 label 'master'
             }
             steps {   
                checkout scm
                sh 'echo from master'
            }
        }
        stage('deploy') {
            agent {
                label 'android'
            }
            steps {
                sh 'echo from android'
            }
        }
    }
}
