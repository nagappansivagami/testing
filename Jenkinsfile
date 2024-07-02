pipeline {
    agent any

    stages {
        stage('Checkin') {
            steps {
                echo 'Checking out code...'
                // Add code to checkout from a version control system, e.g., Git
                // git url: 'https://github.com/nagappansivagami/testing.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                // Add build steps, e.g., compile code, build artifacts
                // sh 'make build'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add test steps, e.g., unit tests, integration tests
                // sh 'make test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Add deployment steps, e.g., deploy to a server, containerize
                // sh 'make deploy'
            }
        }

        stage('Print Message') {
            steps {
                echo 'Hello, this is a single print statement in a Jenkins Pipeline!'
            }
        }
    }
}
