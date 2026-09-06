pipeline {
    agent any

    stages {

        stage('Build Frontend') {
            steps {
                bat '''
                    cd frontend
                    npm install
                    set "CI=false"
                    npm run build
                '''
            }
        }

        stage('Build Backend') {
            steps {
                bat '''
                    cd backend
                    npm install
                '''
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
                bat 'docker push raksha321/attendance-backend:latest'
                bat 'docker push raksha321/attendance-frontend:latest'
            }
        }
    }
}