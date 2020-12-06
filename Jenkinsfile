pipeline {
    environment {
        registry = "aleda145/flask_backend"
        registryCredential = 'dockerhub_id' 
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
                sh 'python -m pytest test_hello_world.py'
            }
        }
        stage('Build') {
            steps {
                script {
                    dockerImage = docker.build registry + ":jenkins" 
                }      
            }
        }
        stage('Publish') {
            steps {
                script {
                    docker.withRegistry( '', registryCredential ) {
                        dockerImage.push() 
                    } 
                }
            }
        }
    }
}
