pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Starting Build stage...'
                echo 'Simulating code build...'
                echo 'Build completed.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Starting Unit and Integration Tests stage...'
                echo 'Running unit tests...'
                echo 'Unit tests completed.'

                echo 'Running integration tests...'
                echo 'Integration tests completed.'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Starting Code Analysis stage...'
                echo 'Running code analysis...'
                echo 'Code analysis completed.'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Starting Security Scan stage...'
                echo 'Running security scan...'
                echo 'Security scan completed.'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Starting Deploy to Staging stage...'
                echo 'Deploying to staging environment...'
                echo 'Deployment to staging completed.'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Starting Integration Tests on Staging stage...'
                echo 'Running integration tests on staging...'
                echo 'Integration tests on staging completed.'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Starting Deploy to Production stage...'
                echo 'Deploying to production environment...'
                echo 'Deployment to production completed.'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
            emailext ( to: "ajojo1974@gmail.com",
                    subject: "Congras, you did it.",
                    body:"Pipeline ${currentBuild.fullDisplayName} completed with status: ${currentBuild.result}",
                    attachLog: true
                         )
        }

        failure {
            echo 'Pipeline execution failed!'
            emailext ( to: "ajojo1974@gmail.com",
                    subject: "Sorry, Failed. please did it again",
                    body:"Pipeline ${currentBuild.fullDisplayName} completed with status: ${currentBuild.result}",
                    attachLog: true
                         )        }
    }
}

