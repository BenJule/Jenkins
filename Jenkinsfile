pipeline {
    agent {
        label 'android'
    }
    environment {
        MIRROR_PATH             = '/mnt/e/los-mirror/LineageOS/android.git'
    }
    stages {
        stage('Preparation') {
            steps {
                echo 'Get Repo'
                sh 'mkdir -p ~/bin'
                sh 'curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo'
            }
        }
        stage('Code syncing') {
            steps {
                echo 'Sync Mirror Repo'
                dir("${MIRROR_PATH}") {
                sh 'repo sync -f --force-sync --force-broken --no-clone-bundle -j$(nproc --all)'
                }
            }
        }
    }
}
