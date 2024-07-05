pipeline {
    agent any

    stages {
        stage('Check-out') {
            steps {
                echo 'Checking out code...'
                // git url: 'https://github.com/nagappansivagami/testing.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the application...'
                // sh 'make build'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // sh 'make test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
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
