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

        stage('Push to Docker Hub') {
            steps {
                // Login, push versioned, tag latest, push latest
                bat """
                echo ${DOCKER_USER_PSW} | docker login -u ${DOCKER_USER_USR} --password-stdin
                docker push ${IMAGE_NAME}:${env.BUILD_NUMBER}
                docker tag ${IMAGE_NAME}:${env.BUILD_NUMBER} ${IMAGE_NAME}:latest
                docker push ${IMAGE_NAME}:latest
                docker logout
                """
            }
        }
    }
}
