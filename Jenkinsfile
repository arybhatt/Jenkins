pipeline {
    /* 1. Define where the job runs */
    agent any 

    /* 2. Define the individual stages of the process */
    stages {
        
        stage('Checkout') {
            steps {
                // This is where you'd usually pull from Git
                echo 'Checking out code from the repository...'
            }
        }

        stage('Build') {
            steps {
                // Compile code or install dependencies here
                echo 'Building the application...'
                sh 'java -version' // Running a shell command to check Java
            }
        }

        stage('Test') {
            steps {
                // Run your unit tests
                echo 'Running unit tests...'
                echo 'Tests passed with flying colors!'
            }
        }

        stage('Deploy') {
            steps {
                // Move the code to production or a web server
                echo 'Deploying to Amazon Linux server...'
            }
        }
    }

    /* 3. Define what happens after the stages finish */
    post {
        always {
            echo 'The job is finished. Cleaning up...'
        }
        success {
            echo 'Everything went off without a hitch!'
        }
        failure {
            echo 'Something went south. Please check the logs.'
        }
    }
}