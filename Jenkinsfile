#!/usr/bin/env groovy

node {
    environment {
        PATH = $ { env.PATH }
    }
            stage('Git') {
                git url: 'https://github.com/kickroot/ranger.git'

            }

            stage('Build') {
                echo "Using path: ${env.PATH}"
                sh "mvn clean compile -DskipTests"
            }

            stage('Scan') {
                environment {
                    SRCCLR_API_TOKEN = $ { env.SRCCLR_API_TOKEN }
                }

                sh "curl -sSL https://download.sourceclear.com/ci.sh | sh"
            }

}

