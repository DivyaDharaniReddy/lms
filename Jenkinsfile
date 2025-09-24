pipeline {
    agent any

    environment {
        BACKEND_IMAGE = "libraryms-app-rest"
        FRONTEND_IMAGE = "libraryms-app-web"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/DivyaDharaniReddy/lms.git'
            }
        }

        stage('Build Backend Docker Image') {
            steps {
                dir('libraryms-app-rest') {
                    bat 'docker build -t %BACKEND_IMAGE% .'
                }
            }
        }

        stage('Build Frontend Docker Image') {
            steps {
                dir('libraryms-app-web') {
                    bat 'docker build -t %FRONTEND_IMAGE% .'
                }
            }
        }

        stage('Push Images (Optional)') {
            steps {
                bat 'docker push %BACKEND_IMAGE%'
                bat 'docker push %FRONTEND_IMAGE%'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker-compose up -d'
            }
        }
    }
}
