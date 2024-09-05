pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add a build tool command here like Maven or Gradle, e.g., sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                // Add a test automation tool command like JUnit, e.g., sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Running Code Analysis...'
                // Integrate code analysis tool like SonarQube, e.g., sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                // Add a security scan tool like OWASP Dependency-Check, e.g., sh 'dependency-check.sh'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Deploy to a staging environment like AWS EC2
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Run tests on the staging environment
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Deploy to production environment
            }
        }
    }

    post {
        always {
            mail to: 'oshan3929@gmail.com',
                 subject: "Pipeline ${currentBuild.fullDisplayName}",
                 body: "Pipeline completed with status ${currentBuild.currentResult}. Check console output at ${env.BUILD_URL}"
        }
    }
}
