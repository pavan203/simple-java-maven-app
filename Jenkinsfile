pipeline {
    agent none // We'll define agent per stage

    stages {


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
