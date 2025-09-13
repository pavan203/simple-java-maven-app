pipeline {
    agent { label 'docker-slave' }

    environment {
        IMAGE_NAME = "zangetsu203/simple-java-maven-app"
    }

    stages {
        stage('Run Docker Image') {
            steps {
                bat "docker run --rm ${IMAGE_NAME}:latest"
            }
        }
    }
}
