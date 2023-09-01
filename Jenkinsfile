pipeline {
    agent any
    environment {
        // Define global environment variables here
        GRADLE_HOME = tool name: 'Gradle', type: 'Gradle'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Use the GRADLE_HOME variable to run Gradle build
                    sh "${GRADLE_HOME}/bin/gradle build"
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit and integration tests here
                // Example: sh "npm test"
            }
        }
        stage('Code Analysis') {
            steps {
                // Integrate a code analysis tool (e.g., SonarQube)
                // and run code analysis
                // Example: sh "sonar-scanner"
            }
        }
        stage('Security Scan') {
            steps {
                // Perform a security scan using a tool (e.g., OWASP ZAP)
                // Example: sh "owasp-zap-scan"
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging server (e.g., AWS EC2)
                // Example: sh "deploy-to-staging-script.sh"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment
                // Example: sh "run-staging-tests.sh"
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy the application to a production server (e.g., AWS EC2)
                // Example: sh "deploy-to-production-script.sh"
            }
        }
    }
    post {
        success {
            // Send success notification email with logs as attachment
            emailext subject: 'Pipeline Success',
                body: 'The Jenkins pipeline has completed successfully.',
                to: 'your-email@example.com',
                attachLog: true
        }
        failure {
            // Send failure notification email with logs as attachment
            emailext subject: 'Pipeline Failure',
                body: 'The Jenkins pipeline has failed.',
                to: 'your-email@example.com',
                attachLog: true
        }
    }
}
