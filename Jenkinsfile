pipeline {
    environment {
        registry = "aleda145/flask_backend"
        registryCredential = 'aleda145' 
        dockerImage = '' 
    }
    agent any

    stages {
        stage('Test') {
            agent {
                docker {
                    image 'python:3-alpine'
                }
            }
            steps {
                sh 'pip install --user -r requirements.txt'
                sh 'pytest'
            }
        }
        stage('Build') {
            steps {
                script {
                    dockerImage = docker.build registry + ":latest" 
                }      
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
