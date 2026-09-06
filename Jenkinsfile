pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Frontend') {
            steps {
                bat 'cd frontend && npm install && set CI=false && npm run build'
            }
        }

        stage('Build Backend') {
            steps {
                bat 'cd backend && npm install'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t raksha321/attendance-backend:latest ./backend'
                bat 'docker build -t raksha321/attendance-frontend:latest ./frontend'
            }
        }

        stage('Docker Hub Push') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKER_USERNAME',
                    passwordVariable: 'DOCKER_PASSWORD'
                )]) {

                    bat 'echo %DOCKER_PASSWORD% | docker login -u %DOCKER_USERNAME% --password-stdin'

                    bat 'docker push raksha321/attendance-backend:latest'
                    bat 'docker push raksha321/attendance-frontend:latest'
                }
            }
        }
    }
}