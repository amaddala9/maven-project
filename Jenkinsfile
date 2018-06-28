pipeline {
/* A declarative Pipeline */
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
        /* agent section could go here as well */
            steps {
                echo 'Deploying....'
            }
        }
    }
}