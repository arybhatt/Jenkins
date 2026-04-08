pipeline {
    agent any
    
    environment {
        // Using a variable for the image name to keep things "DRY" (Don't Repeat Yourself)
        APP_NAME = "my-web-app"
        CONTAINER_NAME = "my-web-app-container"
    }

    stages {
        stage('Checkout') {
            steps {
                // Pulls the latest code from your configured Git repo
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                echo "Building Docker Image: ${APP_NAME}..."
                // Build using the specific Jenkins Build Number for traceability
                sh "docker build -t ${APP_NAME}:${BUILD_NUMBER} ."
                // Tag it as 'latest' so our run command always points to the newest version
                sh "docker tag ${APP_NAME}:${BUILD_NUMBER} ${APP_NAME}:latest"
            }
        }

        stage('Cleanup Old Container') {
            steps {
                echo "Stopping and removing existing container if it exists..."
                // '|| true' ensures the pipeline doesn't fail if the container isn't found
                sh "docker rm -f ${CONTAINER_NAME} || true"
            }
        }

        stage('Deploy Container') {
            steps {
                echo "Deploying new container on Port 80..."
                // Runs the container in detached mode (-d)
                sh "docker run -d --name ${CONTAINER_NAME} -p 80:80 ${APP_NAME}:latest"
            }
        }
        
        stage('Verify Deployment') {
            steps {
                echo "Verifying service status..."
                // A quick check to see if the container is actually running
                sh "docker ps | grep ${CONTAINER_NAME}"
            }
        }
    }

    post {
        success {
            echo "-----------------------------------------------------------"
            echo "SUCCESS: Pipeline finished!"
            echo "Access your app at http://your-ec2-public-ip"
            echo "-----------------------------------------------------------"
        }
        failure {
            echo "ERROR: Pipeline failed. Check the console output above."
        }
        always {
            echo "Cleaning up local workspace..."
            // Keeps your Jenkins server from getting cluttered
            cleanWs()
        }
    }
}