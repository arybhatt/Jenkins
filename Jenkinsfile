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

        stage ('Yourwebhook setup') {

            steps {
                 echo 'smoking'
           } 
        }
       
       stage('Info') {
             steps {
             echo 'Triggered via Jenkinsfile change'
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
