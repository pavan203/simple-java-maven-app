pipeline {
    agent any

    tools {
        maven "MAVEN"
    }

    stages {
        stage('Build') {
            steps {
                // Build the Java project using Maven
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                // Build the Docker image using CLI
                bat 'docker build -t simple-java-maven-app .'
            }
        }

        stage('Docker Run') {
            steps {
                // Run the Docker container in detached mode
                bat 'docker run -d -p 8080:8080 simple-java-maven-app'
            }
        }
    }
}
