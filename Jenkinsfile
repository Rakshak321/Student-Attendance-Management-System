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
                bat 'cd frontend && npm install && npm run build'
            }
        }

        stage('Build Backend') {
            steps {
                bat 'cd backend && npm install'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t attendance-backend:jenkins ./backend'
                bat 'docker build -t attendance-frontend:jenkins ./frontend'
            }
        }
    }
}