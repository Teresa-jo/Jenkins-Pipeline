pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Compile and package code using Maven
                    sh 'mvn clean package'
                }
            }
        }

        stage('Unit Tests') {
            steps {
                script {
                    // Run unit tests
                    sh 'mvn test'
                }
            }
        }

        stage('Integration Tests') {
            steps {
                script {
                    // Run integration tests using Maven
                    sh 'mvn integration-test'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    // Perform code analysis using SonarQube
                    withSonarQubeEnv('Your SonarQube Server') {
                        sh 'mvn sonar:sonar'
                    }
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    // Perform security scan using OWASP ZAP
                    sh 'zap-cli --zap-url http://localhost -f openapi -t /path/to/openapi.yaml'
                }
            }
        }

        stage('Deploy Staging') {
            steps {
                script {
                    // Deploy to staging using Ansible or SSH
                    sh 'ansible-playbook -i inventory/staging deploy.yml'
                }
            }
        }

        stage('Staging Tests') {
            steps {
                script {
                    // Run additional integration tests on staging
                    sh 'mvn integration-test'
                }
            }
        }

        stage('Deploy Production') {
            steps {
                script {
                    // Deploy to production using Ansible or SSH
                    sh 'ansible-playbook -i inventory/production deploy.yml'
                }
            }
        }
    }
}

