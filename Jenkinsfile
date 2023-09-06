pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Fetching code from GIT"
                echo "Compile and build using Maven"
                echo "This is build number: ${env.BUILD_NUMBER}"
                echo "This is build number: ${BUILD_NUMBER}"
                echo "This is build URL: ${BUILD_URL}"
            }
        }
        stage('Unit Test') {
            steps {
                echo "Unit testing using PyTest"
            }
            post {
                    always {
                        script {
                        // Check the Jenkins log if needed
                        sh 'ls -la'
                    }
                }
                success {
                    emailext to:"nathan.nguyennhat@gmail.com",
                    subject:"Success email from Jenkins",
                    body:"Test is completed",
                    attachmentsPattern: 'generatedFile.txt'
                }
                failure {
                    mail to:"nathan.nguyennhat@gmail.com",
                    subject:"Failure email from Jenkins",
                    body:"Test failed"
                }
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
