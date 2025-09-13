pipeline {
    agent { label 'docker' }  // Use the label of your Docker agent
    stages {
        stage('Build') {
            steps {
                sh 'git --version'
                sh 'mvn --version'
            }
        }
    }
}
