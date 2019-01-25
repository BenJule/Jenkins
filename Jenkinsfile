pipeline {
    agent none
    environment {
        MIRROR_PATH             = '/mnt/e/los-mirror/LineageOS/android.git'
        BUILD_PATH              = '/home/lineageos/android/lineage'
        BRANCH                  = 'lineage-15.1'
        DEVICE                  = 'jfltexx'
        USE_CCACHE              =  '1'
        CCACHE_COMPRESS         =  '1'
        ANDROID_JACK_VM_ARGS    =  '-Dfile.encoding=UTF-8 -XX:+TieredCompilation -Xmx4G'        
    }        
    stages {
        stage('Prepare/Checkout') {
            agent {
                 label 'android'
            }
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
