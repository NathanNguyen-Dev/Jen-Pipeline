pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Fetching code from GIT"
                echo "Compile and build using Maven"
                echo "This is build number: ${BUILD_NUMBER}"
                echo "This is build URL: ${BUILD_URL}"
                sh "cd ~/.jenkins/jobs/${env.JOB_NAME}/builds/${BUILD_NUMBER}/"
                sh "ls -la"
            }
        }
        stage('Unit Test') {
            steps {
                echo "Unit testing using PyTest"
                
            }
            post {

                success {
                    emailext (
                    to:"nathan.nguyennhat@gmail.com",
                    subject:"Success Unit Test from Jenkins",
                    body:"Test is completed",
                    attachLog: true
                    )
                }
                failure {
                    emailext(
                    to:"nathan.nguyennhat@gmail.com",
                    subject:"Failure Unit Test from Jenkins",
                    body:"Test failed",
                    attachLog: true
                    )
                }
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Checking  quality of the code using Codacy"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Scanning vulnerabilities using Snyk"
            }
            post {

                success {
                    emailext (
                    to:"nathan.nguyennhat@gmail.com",
                    subject:"Success Security Test from Jenkins",
                    body:" Security Test is completed",
                    attachLog: true
                    )
                }
                failure {
                    emailext(
                    to:"nathan.nguyennhat@gmail.com",
                    subject:"Failure Security Test from Jenkins",
                    body:"Security Test failed",
                    attachLog: true
                    )
                }
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
