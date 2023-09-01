pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "building"
            }
             post {
       
           always{ 
                subject: "Pipeline Successful",
                body: "The pipeline has completed successfully.",
                to: "deakin.com"
           }
        }
    }

        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests
                echo "Testing..."
            }
        }


        stage('Deploy') {
            steps {
                echo "Deploying..."
            }
        }
    }
}
