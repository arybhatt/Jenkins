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

        stage ('webhook setup') {

            steps {
                 echo 'No Please Smoking'
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
