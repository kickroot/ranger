pipeline {
    agent any
    environment { 
        SRCCLR_API_TOKEN=${env.SRCCLR_API_TOKEN}
    }

    stages {
        stage('Build') {
            steps {
                sh "mvn clean compile -DskipTests"
            }
        }

        stage('Scan') {
            steps {
              sh "curl -sSL https://download.sourceclear.com/ci.sh | sh"       
            }
        }
    }
}

