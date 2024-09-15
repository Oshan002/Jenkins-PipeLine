pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project.'
                echo 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests.'
                echo 'mvn test'
            }
            post {
                always {
                    script {
                        try {
                            emailext(
                                attachLog: true,
                                to: 'oshan3929@gmail.com',
                                subject: "Unit and Integration Tests: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                                body: "Unit and Integration Tests have been executed. Please check the results."
                            )
                        } catch (Exception e) {
                            echo "Failed to send email: ${e.getMessage()}"
                        }
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis...'
                echo 'sonar-scanner -Dsonar.projectKey=my_project -Dsonar.sources=src'
            }
            post {
                always {
                    script {
                        try {
                            emailext(
                                attachLog: true,
                                to: 'oshan3929@gmail.com',
                                subject: "Code Analysis: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                                body: "Code Analysis has been executed. Please check the results."
                            )
                        } catch (Exception e) {
                            echo "Failed to send email: ${e.getMessage()}"
                        }
                    }
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                echo 'dependency-check.bat --project my_project --out . --scan ./src'
            }
            post {
                always {
                    script {
                        try {
                            emailext(
                                attachLog: true,
                                to: 'oshan3929@gmail.com',
                                subject: "Security Scan: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                                body: "Security Scan has been executed. Please check the results."
                            )
                        } catch (Exception e) {
                            echo "Failed to send email: ${e.getMessage()}"
                        }
                    }
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                echo 'Copy-Item target'
            }
            post {
                always {
                    script {
                        try {
                            emailext(
                                attachLog: true,
                                to: 'oshan3929@gmail.com',
                                subject: "Deploy to Staging: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                                body: "Deployment to Staging has been executed. Please check the results."
                            )
                        } catch (Exception e) {
                            echo "Failed to send email: ${e.getMessage()}"
                        }
                    }
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                echo 'Invoke-WebRequest -Uri http://staging-server/api/tests -UseBasicParsing'
            }
            post {
                always {
                    script {
                        try {
                            emailext(
                                attachLog: true,
                                to: 'oshan3929@gmail.com',
                                subject: "Integration Tests on Staging: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                                body: "Integration Tests on Staging have been executed. Please check the results."
                            )
                        } catch (Exception e) {
                            echo "Failed to send email: ${e.getMessage()}"
                        }
                    }
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                echo 'Copy-Item target'
            }
            post {
                always {
                    script {
                        try {
                            emailext(
                                attachLog: true,
                                to: 'oshan3929@gmail.com',
                                subject: "Deploy to Production: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                                body: "Deployment to Production has been executed. Please check the results."
                            )
                        } catch (Exception e) {
                            echo "Failed to send email: ${e.getMessage()}"
                        }
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }

        success {
            script {
                try {
                    emailext(
                        attachLog: true,
                        to: 'oshan3929@gmail.com',
                        subject: "SUCCESS: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                        body: "The pipeline completed successfully."
                    )
                } catch (Exception e) {
                    echo "Failed to send email: ${e.getMessage()}"
                }
            }
        }

        failure {
            echo 'Build failed!'
            script {
                try {
                    emailext(
                        attachLog: true,
                        to: 'oshan3929@gmail.com',
                        subject: "FAILURE: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                        body: "The pipeline failed. Please check the logs for details."
                    )
                } catch (Exception e) {
                    echo "Failed to send email: ${e.getMessage()}"
                }
            }
        }
    }
}
