pipeline {
    environment {
        registry = "aleda145/flask_backend"
        registryCredential = 'aleda145' 
        dockerImage = '' 
    }
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    dockerImage = docker.build registry + ":latest" 
                }      
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
