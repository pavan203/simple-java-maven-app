pipeline {
    agent any

    environment {
        IMAGE_NAME = "zangetsu203/simple-java-maven-app" // Replace with your Docker Hub repo
        DOCKERHUB_CREDENTIALS = "docker"   // The Jenkins credential ID
    }

    stages {
        stage('Build Docker Image') {
            steps {
                bat "docker build -t ${IMAGE_NAME}:${env.BUILD_NUMBER} ."
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('', DOCKERHUB_CREDENTIALS) {
                        // Push versioned tag
                        bat "docker push ${IMAGE_NAME}:${env.BUILD_NUMBER}"
                        // Push latest tag
                        bat "docker tag ${IMAGE_NAME}:${env.BUILD_NUMBER} ${IMAGE_NAME}:latest"
                        bat "docker push ${IMAGE_NAME}:latest"
                    }
                }
            }
        }
    }
}
