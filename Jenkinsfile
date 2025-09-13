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


        stage('Run on Slave') {
            agent { label 'docker' }
            steps {
                // Use unarchive instead of copyArtifacts
                copyArtifacts(
                    projectName: "${env.JOB_NAME}",
                    filter: 'target/my-app-1.0-SNAPSHOT.jar',
                    selector: specific('${BUILD_NUMBER}')
                )
                sh 'java -jar my-app-1.0-SNAPSHOT.jar'
            }
        }
    }
}
