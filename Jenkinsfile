pipeline {
    agent any

    stages {

        stage('Docker Hub Login Test') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKER_USERNAME',
                    passwordVariable: 'DOCKER_PASSWORD'
                )]) {

                    powershell '''
                        $env:DOCKER_PASSWORD | docker login --username $env:DOCKER_USERNAME --password-stdin
                    '''
                }
            }
        }
    }
}