pipeline {
    agent 'docker'
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}
