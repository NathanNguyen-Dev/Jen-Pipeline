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
                    script {
                        archiveArtifacts artifacts: '**/test.log', allowEmptyArchive: true
                        
                        // Send success email
                        emailext (
                            to: 'nathan.nguyennhat@gmail.com',
                            subject: "Jenkins Test Stage: SUCCESS",
                            body: """\
                                The Test stage has completed successfully.
                                Please find the logs attached.
                            """,
                            attachmentsPattern: '**/test.log'
                        )
                    }
                }
                failure {
                    script {
                        archiveArtifacts artifacts: '**/test.log', allowEmptyArchive: true
                        
                        // Send failure email
                        emailext (
                            to: 'nathan.nguyennhat@gmail.com',
                            subject: "Jenkins Test Stage: FAILURE",
                            body: """\
                                The Test stage has failed.
                                Please find the logs attached.
                            """,
                            attachmentsPattern: '**/test.log'
                        )
                    }
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
