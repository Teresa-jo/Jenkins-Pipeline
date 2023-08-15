pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Use a build automation tool like Maven
                    sh 'mvn clean package'
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    // Run unit tests using JUnit
                    sh 'mvn test'

                    // Run integration tests using a separate command
                    sh './run_integration_tests.sh'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    // Integrate with a code analysis tool like SonarQube
                    withSonarQubeEnv('SonarQubeServer') {
                        sh 'mvn sonar:sonar'
                    }
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    // Integrate with a security scanning tool like OWASP Dependency-Check
                    sh 'dependency-check.sh'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    // Deploy to staging environment using deployment tools
                    sh 'aws ecs deploy-to-staging'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    // Run integration tests on the staged environment
                    sh './run_staging_integration_tests.sh'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    // Deploy to production environment
                    sh 'aws ecs deploy-to-production'
                }
            }
        }
    }

    post {
        failure {
            emailext (
                subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                body: "${currentBuild.fullDisplayName} has failed. Check the logs for more details.",
                recipientProviders: [developers()]
            )
        }
        success {
            emailext (
                subject: "Pipeline Successful: ${currentBuild.fullDisplayName}",
                body: "${currentBuild.fullDisplayName} has completed successfully.",
                recipientProviders: [developers()]
            )
        }
    }
}
