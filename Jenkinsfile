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
        stage('Preparation') {
            agent any
            steps {
                dir("${BUILD_PATH}") {
                    sh("pwd")
                    sh 'mkdir -p ~/bin'
                    sh 'curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo'
                    sh '''#!/bin/bash\nset -x\nsource ~/.profile\nrepo init -u ${MIRROR_PATH} -b ${BRANCH}'''
                }
            }
        }
        stage('Repo syncing') {
            agent {
                label 'master'
            }            
            steps {
                echo 'Repo syncing'
                dir("${BUILD_PATH}") {
                    sh '''#!/bin/bash\nset -x\nrepo sync -f --force-sync --force-broken --no-clone-bundle --no-tags -j$(nproc --all)'''
                }
            }
        }
        stage('Dev syncing') {
            agent {
                label 'master'
            }            
            steps {
                echo 'Code syncing'
                dir("${BUILD_PATH}") {
                    /* android_device_samsung_jfltexx */
                    checkout([$class: 'GitSCM',
					branches: [[name: 'origin/lineage-15.1']],
                    extensions: [[$class: 'RelativeTargetDirectory', 
                        relativeTargetDir: 'device/samsung/jfltexx']],
					userRemoteConfigs: [[url: 'https://github.com/los-legacy/android_device_samsung_jfltexx.git']]
					])
                    
                    /* android_device_samsung_jf-common */
                    checkout([$class: 'GitSCM',
					branches: [[name: 'origin/lineage-15.1']],
                    extensions: [[$class: 'RelativeTargetDirectory', 
                        relativeTargetDir: 'device/samsung/jf-common']],                              
					userRemoteConfigs: [[url: 'https://github.com/los-legacy/android_device_samsung_jf-common.git']]
					])
                    
                    /* android_device_samsung_qcom-common */
                    checkout([$class: 'GitSCM',
					branches: [[name: 'origin/lineage-15.1']],
					extensions: [[$class: 'RelativeTargetDirectory', 
                        relativeTargetDir: 'device/samsung/qcom-common']],
					userRemoteConfigs: [[url: 'https://github.com/LineageOS/android_device_samsung_qcom-common.git']]
					])
                    
                    /* android_device_qcom_common */
                    checkout([$class: 'GitSCM',
					branches: [[name: 'origin/lineage-15.1']],
					extensions: [[$class: 'RelativeTargetDirectory', 
                        relativeTargetDir: 'device/qcom/common']],
					userRemoteConfigs: [[url: 'https://github.com/LineageOS/android_device_qcom_common.git']]
					])
                    
                    /* android_hardware_samsung */
                    checkout([$class: 'GitSCM',
					branches: [[name: 'origin/lineage-15.1']],
					extensions: [[$class: 'RelativeTargetDirectory', 
                        relativeTargetDir: 'hardware/samsung']],
					userRemoteConfigs: [[url: 'https://github.com/LineageOS/android_hardware_samsung.git']]
					])
                    
                    /* proprietary_vendor_samsung_jf */
                    checkout([$class: 'GitSCM',
					branches: [[name: 'origin/lineage-15.1']],
					extensions: [[$class: 'RelativeTargetDirectory', 
                        relativeTargetDir: 'vendor/samsung']],
					userRemoteConfigs: [[url: 'https://github.com/los-legacy/proprietary_vendor_samsung_jf.git']]
					])
                    
                    /* android_kernel_samsung_jf */
                    checkout([$class: 'GitSCM',
					branches: [[name: 'origin/lineage-15.1']],
					extensions: [[$class: 'RelativeTargetDirectory', 
                        relativeTargetDir: 'kernel/samsung/jf']],
					userRemoteConfigs: [[url: 'https://github.com/los-legacy/android_kernel_samsung_jf.git']]
					])
                    
                    /* android_packages_resources_devicesettings */
                    checkout([$class: 'GitSCM',
					branches: [[name: 'origin/lineage-15.1']],
					extensions: [[$class: 'RelativeTargetDirectory', 
                        relativeTargetDir: 'packages/resources/devicesettings']],
					userRemoteConfigs: [[url: 'https://github.com/LineageOS/android_packages_resources_devicesettings.git']]
					])
                }
            }
        }
        stage('Build process') {
            agent {
                label 'build'
            }
            steps {
                sh 'echo from build'
            }
        }
        stage('OTA Package') {
            agent {
                label 'build'
            }
            steps {
                sh 'echo from build'
            }
        }
        stage('Archiving') {
            agent {
                label 'build'
            }
            steps {
                sh 'echo from build'
            }
        }	    
        stage('Publishing') {
            agent {
                label 'build'
            }
            steps {
                sh 'echo from build'
            }
        }	    
    }
}
