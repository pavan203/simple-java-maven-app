pipeline {
    agent none // We'll define agent per stage

    stages {
        stage('Build on Windows') {
            agent { 'built-in' } // Replace with your Windows node label
            steps {
                bat 'mvn --version'
            }
        }

        stage('Build on Docker Linux') {
            agent { label 'docker' } // Your Docker slave label
            steps {
                sh 'git --version'
                sh 'mvn --version'
                sh 'java -version'
            }
        }
    }
}
