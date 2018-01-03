#!/usr/bin/env groovy

node {
    environment {
        PATH = "/usr/bin:/bin/usr/local/bin:/Users/jason/maven/latest/bin"
    }
            stage('Git') {
                git url: 'https://github.com/kickroot/ranger.git'

            }

            stage('Build') {
                sh 'printenv'
                sh "mvn clean compile -DskipTests"
            }

            stage('Scan') {
                environment {
                    SRCCLR_API_TOKEN = $ { env.SRCCLR_API_TOKEN }
                }

                env.PATH = "/usr/bin:/bin/usr/local/bin:/Users/jason/maven/latest/bin"
                sh "curl -sSL https://download.sourceclear.com/ci.sh | sh"
            }

}

