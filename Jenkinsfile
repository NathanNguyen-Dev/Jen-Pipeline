pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Fetching code from GIT"
                echo "Compile and build using Maven"
            }
        }
        stage('Unit Testing') {
            steps {
                echo "Unit testing using PyTest"
            }
            post {
                success {
                    // Send success email
                    mail to:"nathan.nguyennhat@gmail.com",
                    subject:"Success email from Jenkins",
                    body:"Test is completed"
                    }
                }
                failure {
                    // Send failure email
                    mail to:"nathan.nguyennhat@gmail.com",
                    subject:"Failure email from Jenkins",
                    body:"Test is not completed"

                }
        }  
        stage('Code Quality Check') {
            steps {
                echo "Checking  quality of the code using Codacy"
            }
        }
        stage('Sercurity Scan') {
            steps {
                echo "Scanning vulnerabilities using Snyk"
            }
        }
        stage('Intergration Testing') {
            steps {
                echo "Integration testing using Playwrights on staging server"
                sleep 10
            }
        }
        stage('Deploy to production') {
            steps {
                echo "Deploying to production on EC2 instances"
            }
        }
    }
}
