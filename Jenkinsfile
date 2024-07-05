pipeline {
    agent any
    
    stages {
        stage('Fetch Code') {
            steps {
                git <https://github.com/nagappansivagami/testing.git>
            }
        }
        stage('Code Analysis') {
            environment {
                scannerHome = tool 'Sonar'
            }
            steps {
                script {
                    withSonarQubeEnv('Sonar') {
                        sh "${scannerHome}/bin/sonar-scanner \
                            -Dsonar.projectKey=<project-key> \
                            -Dsonar.projectName=<project-name> \
                            -Dsonar.projectVersion=<project-version> \
                            -Dsonar.sources=<project-path>"
                    }
                }
            }
        }
    }
}
