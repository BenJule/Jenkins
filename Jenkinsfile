pipeline {
    agent none
    environment {
        MIRROR_PATH             = '/mnt/e/los-mirror/LineageOS/android.git'
        BUILD_PATH              = '/home/lineageos/android/lineage'
    }        
    stages {
        stage('Prepare/Checkout') {
            steps {
                dir("${BUILD_PATH}") {
                    sh("pwd")
                    sh 'mkdir -p ~/bin'
                    sh 'curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo'
                    sh '''#!/bin/bash\nset -x\nsource ~/.profile\nrepo init -u ${MIRROR_PATH} -b ${BRANCH}'''
                    sh 'repo init -u ${MIRROR_PATH} -b ${BRANCH}'
                }
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
        stage('Syncing Dev') {
            agent {
                label 'jfltexx'
            }
            steps {
                sh 'echo from jfltexx'
            }
        }
        stage('Syncing Kernel') {
            agent {
                label 'jfltexx'
            }
            steps {
                sh 'echo from jfltexx'
            }
        }
    }
}
