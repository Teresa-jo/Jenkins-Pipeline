pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Starting Build stage...'
                echo 'Simulating code build...'
                // Replace this with your actual build commands
                echo 'Build completed.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Starting Unit and Integration Tests stage...'
                echo 'Running unit tests...'
                // Replace this with your actual unit test commands
                echo 'Unit tests completed.'

                echo 'Running integration tests...'
                // Replace this with your actual integration test commands
                echo 'Integration tests completed.'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Starting Code Analysis stage...'
                echo 'Running code analysis...'
                // Replace this with your actual code analysis commands
                echo 'Code analysis completed.'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Starting Security Scan stage...'
                echo 'Running security scan...'
                // Replace this with your actual security scan commands
                echo 'Security scan completed.'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Starting Deploy to Staging stage...'
                echo 'Deploying to staging environment...'
                // Replace this with your actual deployment commands
                echo 'Deployment to staging completed.'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Starting Integration Tests on Staging stage...'
                echo 'Running integration tests on staging...'
                // Replace this with your actual integration test commands
                echo 'Integration tests on staging completed.'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Starting Deploy to Production stage...'
                echo 'Deploying to production environment...'
                // Replace this with your actual deployment commands
                echo 'Deployment to production completed.'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
            emailext ( to: "ajojo1974@gmail.com",
                    subject: "Build Status Email",
                    body:"Pipeline ${currentBuild.fullDisplayName} completed with status: ${currentBuild.result}",
                    attachLog: true
                         )
        }

        failure {
            echo 'Pipeline execution failed!'
            emailext ( to: "ajojo1974@gmail.com",
                    subject: "Build Status Email",
                    body:"Pipeline ${currentBuild.fullDisplayName} completed with status: ${currentBuild.result}",
                    attachLog: true
                         )        }
    }
}

