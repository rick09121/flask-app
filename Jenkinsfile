pipeline {
    agent any

    stages {
        stage('Clone code') {
            steps {
                git 'https://github.com/rick09121/flask-app.git'
            }
        }

        stage('Build image') {
            steps {
                script {
                    docker.build('flask-app')
                }
            }
        }

        stage('Run container') {
            steps {
                script {
                    sh 'docker rm -f flask-container || true'
                    sh 'docker run -d -p 5000:5000 --name flask-container flask-app'
                }
            }
        }
    }
}
