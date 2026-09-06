pipeline {
    agent any

    stages {
        stage('Docker Credential Test') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKER_USERNAME',
                    passwordVariable: 'DOCKER_PASSWORD'
                )]) {
                    bat 'echo Docker username is: %DOCKER_USERNAME%'
                    bat 'if defined DOCKER_PASSWORD (echo Docker password variable is SET) else (echo Docker password variable is NOT SET)'
                }
            }
        }
    }
}