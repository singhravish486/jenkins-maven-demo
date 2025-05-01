pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Clone your repo
                git url: 'https://github.com/singhravish486/jenkins-maven-demo.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                // Use Windows batch command to build
                bat 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
    }
    post {
        always {
            // Archive JUnit test results
            junit '**/target/surefire-reports/*.xml'
        }
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}
