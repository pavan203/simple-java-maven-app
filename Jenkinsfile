pipeline {
    agent none

    stages {

        stage('Build') {
            agent { label 'built-in' }
            tools { maven 'MAVEN' }
            steps {
                bat 'mvn clean install -DskipTests'
                archiveArtifacts artifacts: 'target/my-app-1.0-SNAPSHOT.jar', fingerprint: true
            }
        }

        stage('Test') {
            agent { label 'built-in' }
            tools { maven 'MAVEN' }
            steps {
                bat 'mvn test'
            }
        }

        stage('Run on Slave') {
            agent { label 'docker' }
            steps {
                // Copy JAR from master to slave
                copyArtifacts(
                    projectName: env.JOB_NAME,
                    selector: lastSuccessful(),
                    filter: 'target/my-app-1.0-SNAPSHOT.jar'
                )
                sh 'java -jar my-app-1.0-SNAPSHOT.jar'
            }
        }
    }
}
