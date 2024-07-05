pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/nagappansivagami/testing.git', branch: 'main'
            }
        }
        stage('SonarQube Analysis') {
            environment {
                scannerHome = tool 'SonarQube_scanner'
            }
            steps {
                withSonarQubeEnv('server-sonar') {
                    sh """
                    ${scannerHome}/bin/sonar-scanner -X \
                    -Dsonar.projectKey=testing-jenkins-project \
                    -Dsonar.projectName=testing-jenkins-project \
                    -Dsonar.language=java \
                    -Dsonar.projectVersion=1.0 \
                    -Dsonar.sources=src \
                    -Dsonar.projectBaseDir=${WORKSPACE}
                    """
                }
            }
        }
    }
}
