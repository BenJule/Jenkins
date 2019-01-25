pipeline {
    agent none
    stages {
        stage('say hi') {
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
                sh './deploy-code-here'
            }
        }
    }
}
