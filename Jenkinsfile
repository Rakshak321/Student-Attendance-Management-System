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

        stage('Check Kubernetes') {
            steps {
                bat 'kubectl version --client'
                bat 'kubectl get nodes'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl set image deployment/attendance-backend backend=raksha321/attendance-backend:latest'
                bat 'kubectl set image deployment/attendance-frontend frontend=raksha321/attendance-frontend:latest'

                bat 'kubectl rollout status deployment/attendance-backend'
                bat 'kubectl rollout status deployment/attendance-frontend'
            }
        }
    }
}