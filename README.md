
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from version control
                git url: 'https://github.com/nagappansivagami/testing.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                // Run your build commands
                sh 'make build'
            }
        }
        stage('Test') {
            steps {
                // Run your test commands
                sh 'make test'
            }
        }
        stage('Deploy') {
            steps {
                // Run your deploy commands
                sh 'make deploy'
            }
        }
    }
    post {
        always {
            // Archive the build artifacts and test results
            archiveArtifacts artifacts: 'build/**/*'
            junit 'test-results/**/*.xml'
        }
        success {
            // Notify on success
            echo 'Build, Test, and Deploy stages completed successfully.'
        }
        failure {
            // Notify on failure
            echo 'Build, Test, or Deploy stage failed.'
        }
    }
}
