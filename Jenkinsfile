pipeline {
    agent none  // no global agent; define per stage

    stages {
        stage('Build & Test on Master') {
            agent { label 'built-in' }  // your Windows master
            steps {
                bat 'mvn clean install'
                bat 'mvn test'
            }
        }

        stage('Run on Slave') {
            agent { label 'docker' }  // your slave node label
            steps {
                sh 'java -jar target/my-app-1.0-SNAPSHOT.jar'
            }
        }
    }
}
