pipeline {
    agent any
    environment {
        MIRROR_PATH             = '/mnt/e/los-mirror/LineageOS/android.git'
    }
    stages {
        stage('Get Repo') {
            steps {
                echo 'Get Repo'
                sh 'mkdir -p ~/bin'
                sh 'curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo'
            }
        }
        stage('Sync Mirror Repo') {
            steps {
                echo 'Sync Mirror Repo'
                dir("${MIRROR_PATH}") {
                sh 'repo sync -f --force-sync --force-broken --no-clone-bundle -j$(nproc --all)'
                }
            }
        }
    }
    post { 
        always { 
            echo 'Syncing done!'
        }
    }
}
