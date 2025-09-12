pipeline {
    agent any

    environment {
        IMAGE_NAME = "zangetsu203/simple-java-maven-app"
        DOCKER_USER = credentials('docker') // Jenkins credential ID containing Docker username/password
    }

    stages {
        stage('Build Docker Image') {
            steps {
                bat "docker build -t ${IMAGE_NAME}:${env.BUILD_NUMBER} ."
            }
        }

    stage('Push Docker Image') {
        steps {
            bat """
            docker login -u %DOCKER_USER_USR% -p %DOCKER_USER_PSW%
            docker push %IMAGE_NAME%:%BUILD_NUMBER%
            docker logout
            """
        }
    }

    }
}
