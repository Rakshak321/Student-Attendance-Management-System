pipeline {
    agent any

    stages {
        stage('Check Docker Environment') {
            steps {
                bat '''
                    echo ===== DOCKER VARIABLES =====
                    set DOCKER

                    echo ===== PROXY VARIABLES =====
                    set HTTP_PROXY
                    set HTTPS_PROXY
                    set NO_PROXY
                '''
            }
        }
    }
}