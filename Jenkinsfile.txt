pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning from GitHub...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
            }
        }

        stage ('smoke test') {

            steps {
                 echo 'smoking'
           } 
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }
}