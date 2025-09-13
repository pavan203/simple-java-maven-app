pipeline {
    agent {label 'docker'}
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}
