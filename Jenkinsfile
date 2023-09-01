pipeline {
    agent any
    environment {
        // Define global environment variables here
        MAVEN_HOME = tool name: 'Maven', type: 'Maven'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Use the MAVEN_HOME variable to run Maven build
                    sh "${MAVEN_HOME}/bin/mvn clean install"
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit and integration tests here
                // You can use tools like JUnit or TestNG for testing
            }
        }
        stage('Code Analysis') {
            steps {
                // Integrate a code analysis tool (e.g., SonarQube)
                // and run code analysis
            }
        }
        stage('Security Scan') {
            steps {
                // Perform a security scan using a tool (e.g., OWASP ZAP)
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging server (e.g., AWS EC2)
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy the application to a production server (e.g., AWS EC2)
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
