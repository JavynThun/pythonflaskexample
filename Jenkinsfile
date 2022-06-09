pipeline {
    agent { docker { image 'python:3.10.1-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
        stage('sonarqube') {
            environment {
                scannerHome = tool 'sonarqube'
            }
            steps {
                withSonarQubeEnv(installationName: 'sonarqube') {
                    sh "${scannerHome}/bin/sonar-scanner -X"
                }
            }
        }
    }
}
