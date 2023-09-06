pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "~/Desktop/SIT_5.1P/"
        TESTING_ENVIRONMENT = "Staging"
        PRODUCTION_ENVIRONMENT = "NATHAN_NGUYEN_DEPLOYMENT"
    }
    stages {
        stage('Build') {
            steps {
                echo "Fetching code from $DIRECTORY_PATH"
                echo "compile the code and generate any necessary artifacts"
            }
        }
        stage('Test') {
            steps {
                echo "Unit testing and Intergration testing"
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Checking  quality of the code"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying the app to $TESTING_ENVIRONMENT environment"
            }
        }
        stage('Approval') {
            steps {
                echo "Waiting for approval"
                sleep 10
            }
        }
        stage('Deploy to production') {
            steps {
                echo "Deploying to production at $PRODUCTION_ENVIRONMENT"
            }
        }
    }
}
