pipeline {

    agent any

    environment {
        NAME = 'Sapphire'
        BASE_NAME = 'sapphire'
        ZIP_NAME = 'SAPP-Electrum'
    }

    stages {

        stage("cleaning") {

            steps {
                echo 'building linux ...'
                sh '''#!/bin/bash
                    rm -f dist/*
                '''
            }
        }

        stage("build_linux") {

            steps {
                echo 'building linux ...'
                sh '''#!/bin/bash
                    cd contrib
                    cd build-linux
                    cd appimage
                    ELECBUILD_COMMIT=HEAD ELECBUILD_NOCACHE=1 ./build.sh
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
                    cd contrib
                    cd build-wine
                    ELECBUILD_COMMIT=HEAD ELECBUILD_NOCACHE=1 ./build.sh
                '''
            }
        }

        stage("deploy_windows") {

            steps {
                echo 'deploy windows ...'
                sh """#!/bin/bash
                    cd contrib
                    cd build-wine
                    cd dist
                    zip ${ZIP_NAME}-\$(../../../dist/electrum-*.AppImage version --offline)-Portable-Windows.zip *portable.exe
                    zip ${ZIP_NAME}-\$(../../../dist/electrum-*.AppImage version --offline)-Setup-Windows.zip *setup.exe
                    cp *.zip ../../../dist/
                """
            }
        }
    }
}