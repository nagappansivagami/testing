pipeline {
    agent any

    environment {
        SONAR_SCANNER_HOME = tool name: 'SonarQube_scanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
        SONAR_URL = 'http://192.168.101.41:9000'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/nagappansivagami/testing.git', branch: 'main'
            }
        }

        stage('SonarQube Analysis') {
            environment {
                SONAR_TOKEN = credentials('sonar-token') // Ensure this matches the credential ID
            }
            steps {
                script {
                    def scannerHome = tool 'SonarQube_scanner'
                    withSonarQubeEnv('server-sonar') {
                        sh "${scannerHome}/bin/sonar-scanner " +
                           "-Dsonar.host.url=${SONAR_URL} " +
                           "-Dsonar.projectKey=testing-jenkins-project " +
                           "-Dsonar.projectName=testing-jenkins-project " +
                           "-Dsonar.language=java " +
                           "-Dsonar.projectVersion=1.0 " +
                           "-Dsonar.sources=src/main/java " +
                           "-Dsonar.projectBaseDir=${env.WORKSPACE} " +
                           "-Dsonar.login=${SONAR_TOKEN}"
                    }
                }
            }
        }
    }

    post {
        failure {
            echo 'Build failed!'
        }
        success {
            echo 'Build succeeded!'
        }
    }
}
