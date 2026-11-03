pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building DevOps Lab 1 project...'
                sh 'ls -la'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing project files...'
                sh 'test -f README.md && test -f feature.txt'
                echo 'All required files are present!'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                echo 'Deployment simulation completed!'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }
        failure {
            echo 'CI/CD Pipeline failed!'
        }
    }
}
