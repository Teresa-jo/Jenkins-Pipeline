pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                sh 'mvn test'
                sh 'mvn integration-test'
                
                // Send email notification for test stage
                emailext (
                    to: 's222186709@deakin.edu.au', // Add recipient email address here
                    subject: "Unit and Integration Tests ${currentBuild.currentResult}",
                    body: "Unit and Integration Tests stage status: ${currentBuild.currentResult}",
                    attachmentsPattern: 'target/test-reports/*.xml' // Attach test reports
                )
            }
        }

        stage('Code Analysis') {
            steps {
                sh 'mvn sonar:sonar'
            }
        }

        stage('Security Scan') {
            steps {
                sh 'zap-cli --zap-url http://localhost -f openapi -t /path/to/openapi.yaml'
                
                // Send email notification for security scan stage
                emailext (
                    to: 's222186709@deakin.edu.au', // Add recipient email address here
                    subject: "Security Scan ${currentBuild.currentResult}",
                    body: "Security Scan stage status: ${currentBuild.currentResult}",
                    attachmentsPattern: 'zap-report/*.html' // Attach ZAP security scan report
                )
            }
        }

        stage('Deploy to Staging') {
            steps {
                sh 'ansible-playbook -i inventory/staging deploy.yml'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                sh 'mvn integration-test'
                
                // Send email notification for staging tests stage
                emailext (
                    to: 's222186709@deakin.edu.au', // Add recipient email address here
                    subject: "Integration Tests on Staging ${currentBuild.currentResult}",
                    body: "Integration Tests on Staging stage status: ${currentBuild.currentResult}",
                    attachmentsPattern: 'target/test-reports/*.xml' // Attach test reports
                )
            }
        }

        stage('Deploy to Production') {
            steps {
                sh 'ansible-playbook -i inventory/production deploy.yml'
            }
        }
    }
}

