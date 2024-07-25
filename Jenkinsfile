pipeline {
    agent any
    
    environment {
        scannerHome = tool name: 'SonarQube Scanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
    }
    
    stages {
        stage('Fetch Code') {
            steps {
                git 'https://github.com/nagappansivagami/testing.git'  // Corrected git step syntax
            }
        }
        
        stage('Code Analysis') {
            steps {
                script {
                    def scannerHome = tool name: 'SonarQube Scanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                    
                    withSonarQubeEnv('SonarQube Community Edition v10.6 (92116)') {
                        withEnv(["PATH+SONAR=${scannerHome}/bin"]) {
                            sh 'echo $PATH'  // Debugging step to check PATH
                            sh 'which sonar-scanner'  // Debugging step to locate sonar-scanner
                            sh '''
                            sonar-scanner \
                            -Dsonar.projectKey=fullstack-next-node-postgres-main \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=http://localhost:9000
                            '''
                        }
                    }
                }
            }
        }
    }
}
