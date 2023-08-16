pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '/usr/local/Cellar/maven/3.9.4/libexec/bin/mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                sh '/usr/local/Cellar/maven/3.9.4/libexec/bin/mvn test'
                sh '/usr/local/Cellar/maven/3.9.4/libexec/bin/mvn integration-test'
                
                // Send email notification for test stage
                emailext (
                    to: 'recipient@example.com', // Add recipient email address here
                    subject: "Unit and Integration Tests ${currentBuild.currentResult}",
                    body: "Unit and Integration Tests stage status: ${currentBuild.currentResult}",
                    attachmentsPattern: 'target/test-reports/*.xml' // Attach test reports
                )
            }
        }

        stage('Code Analysis') {
            steps {
                // Add steps to run code analysis tools (if applicable)
            }
        }

        stage('Security Scan') {
            steps {
                // Add steps to run security scan tools (if applicable)
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Add steps to deploy to staging server
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                // Add steps to run integration tests on staging environment
            }
        }

        stage('Deploy to Production') {
            steps {
                // Add steps to deploy to production server
            }
        }
    }
}
