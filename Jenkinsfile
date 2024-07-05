pipeline {
    agent any
    
    stages {
        stage('Fetch Code') {
            steps {
                git <your-github-repository>
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
