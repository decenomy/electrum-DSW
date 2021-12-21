pipeline {

    agent any

    environment {
        NAME = 'Sapphire'
        BASE_NAME = 'sapphire'
        ZIP_NAME = 'SAPP-Electrum'
    }

    stages {

        stage("build_linux") {

            steps {
                echo 'building linux ...'
                sh '''#!/bin/bash
                    cd dist
                    rm -f *.AppImage
                    cd ..
                    cd contrib
                    cd build-linux
                    cd appimage
                    ELECBUILD_COMMIT=HEAD ELECBUILD_NOCACHE=1 ./build.sh
                    cd ..
                    cd ..
                    cd ..
                '''
            }
        }

        stage("deploy_linux") {

            steps {
                echo 'deploy linux ...'

                sh """#!/bin/bash
                    cd dist
                    zip ${ZIP_NAME}-\$(./electrum-*.AppImage version --offline)-Linux.zip electrum-*.AppImage
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