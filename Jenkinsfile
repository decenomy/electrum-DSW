pipeline {

    agent any

    environment {
        ELECBUILD_COMMIT = 'HEAD'
        ELECBUILD_NOCACHE = '1'
    }

    stages {

        stage("build_linux") {

            steps {
                echo 'building linux ...'
                sh '''#!/bin/bash
                    cd contrib
                    cd build-linux
                    cd appimage
                    ./build.sh
                '''
            }
        }

        stage("deploy_linux") {

            steps {
                echo 'deploy linux ...'

                sh """#!/bin/bash
                    
                """
            }
        }

        stage("build_windows") {

            steps {
                echo 'building windows ...'
                sh '''#!/bin/bash
                    
                '''
            }
        }

        stage("deploy_windows") {

            steps {
                echo 'deploy windows ...'
                sh """#!/bin/bash
                    
                """
            }
        }
    }
}