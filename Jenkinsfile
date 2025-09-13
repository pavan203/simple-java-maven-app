pipeline {
    agent none  // no global agent; define per stage

    stages {
       
        stage('Build') {
             agent {label 'built-in'}
            steps {
                // Skip tests during build
                bat 'mvn clean install -DskipTests'
            }
        }
        stage('Test') {
            steps {
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
