pipeline {
    agent {
        docker {
            image 'your-docker-image-with-maven-and-git'
            args '-u root:root' // optional: run as root to avoid permission issues
        }
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}
