pipeline {
    agent { label 'docker-cloud' }

    environment {
        IMAGE_NAME = "zangetsu203/simple-java-maven-app:latest"
    }

    stages {
        stage('Run Docker Container') {
            steps {
                bat "docker pull ${IMAGE_NAME}"
                bat "docker run -d --name my-app -p 8081:8080 ${IMAGE_NAME}"
            }
        }
    }
}
