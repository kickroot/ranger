#!/usr/bin/env groovy

pipeline {

    node {
        git url: 'https://github.com/kickroot/ranger.git'
        stages {
            stage('Build') {
                steps {
                    sh "mvn clean compile -DskipTests"
                }
            }

            stage('Scan') {
                environment {
                    SRCCLR_API_TOKEN = $ { env.SRCCLR_API_TOKEN }
                }

                steps {
                    sh "curl -sSL https://download.sourceclear.com/ci.sh | sh"
                }
            }
        }
    }
}

