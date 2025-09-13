pipeline {
    agent {
        docker {
            image 'your-docker-image-with-maven-and-git'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                sh 'git clone -b master https://github.com/pavan203/simple-java-maven-app.git'
                sh 'cd simple-java-maven-app'
            }
        }
        stage('Build') {
            steps {
                sh 'cd simple-java-maven-app && mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'cd simple-java-maven-app && mvn test'
            }
        }
    }
}
