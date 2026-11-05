pipeline {
    agent any

    environment {
        KUBECONFIG = '/var/lib/jenkins/.kube/config'
        PATH = "/usr/local/bin:${env.PATH}"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building DevOps Lab 2 project...'
                sh 'ls -la'
                sh 'test -f Lab-2-Containerization/Dockerfile'
            }
        }

        stage('Test') {
            steps {
                echo 'Checking application and Kubernetes files...'
                sh 'test -f Lab-2-Containerization/app/app.py'
                sh 'test -f Lab-2-Containerization/kubernetes/deployment.yaml'
                sh 'test -f Lab-2-Containerization/kubernetes/service.yaml'
                echo 'All required files are present!'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo 'Applying Kubernetes manifests...'
                sh '''
                    kubectl apply -f Lab-2-Containerization/kubernetes/deployment.yaml
                    kubectl apply -f Lab-2-Containerization/kubernetes/service.yaml
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                echo 'Checking Kubernetes deployment...'
                sh '''
                    kubectl rollout status deployment/lab2-flask-deployment --timeout=180s
                    kubectl get deployments
                    kubectl get pods
                    kubectl get services
                '''
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
