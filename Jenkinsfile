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
        /*stage('Build') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }*/

        stage('Docker Build') {
            steps {
                bat "docker build -t ${IMAGE_NAME}:${env.BUILD_NUMBER} ."
            }
        }
        
        stage('Docker Push') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKERHUB_CREDENTIALS) {
                        docker.image('my-image').push()
                    }
                }
            }
        }


        stage('Docker Run') {
            steps {
                bat "docker rm -f ${CONTAINER_NAME} || echo Container not found"
            }
        }
    }
}
