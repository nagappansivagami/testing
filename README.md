pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps { git 'https://github.com/nagappansivagami/testing.git' }
        }
        stage('Build') {
            steps { sh 'make build' }
        }
        stage('Test') {
            steps { sh 'make test' }
        }
        stage('Deploy') {
            steps { sh 'make deploy' }
        }
    }
    post {
        always {
            archiveArtifacts 'build/**/*'
            junit 'test-results/**/*.xml'
        }
    }
}
