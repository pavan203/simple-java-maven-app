pipeline {
    agent any

    tools {
        maven "MAVEN"
    }

    environment {
        DOCKERHUB_CREDENTIALS = 'dockerhub-cred-id'
        IMAGE_NAME = 'pavan203/simple-java-maven-app'
        CONTAINER_NAME = 'simple-java-maven-app-container'
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                bat "docker build -t ${IMAGE_NAME}:${env.BUILD_NUMBER} ."
            }
        }

        stage('Docker Push') {
            steps {
                docker.withRegistry('https://index.docker.io/v1/', DOCKERHUB_CREDENTIALS) {
                    bat "docker push ${IMAGE_NAME}:${env.BUILD_NUMBER}"
                    bat "docker tag ${IMAGE_NAME}:${env.BUILD_NUMBER} ${IMAGE_NAME}:latest"
                    bat "docker push ${IMAGE_NAME}:latest"
                }
            }
        }

        stage('Docker Run') {
            steps {
                bat "docker rm -f ${CONTAINER_NAME} || echo Container not found"
                bat "docker run -d --name ${CONTAINER_NAME} -p 8081:8080 ${IMAGE_NAME}:${env.BUILD_NUMBER}"
            }
        }
    }
}
