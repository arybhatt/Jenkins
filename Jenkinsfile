pipeline {
    agent any
    
    environment {
        APP_NAME = "my-web-app"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                echo "Building Docker Image..."
                sh "docker build -t ${APP_NAME}:${BUILD_NUMBER} ."
                sh "docker tag ${APP_NAME}:${BUILD_NUMBER} ${APP_NAME}:latest"
            }
        }

        stage('Deploy Container') {
            steps {
                echo "Deploying Container..."
                // Remove old container if it exists to avoid port conflicts
                sh "docker rm -f ${APP_NAME}-container || true"
                // Run the new one on Port 80
                sh "docker run -d --name ${APP_NAME}-container -p 80:80 ${APP_NAME}:latest"
            }
        }
    }

    post {
        success {
            echo "Pipeline finished! Check your EC2 Public IP on Port 80."
        }
    }
}