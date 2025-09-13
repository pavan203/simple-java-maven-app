pipeline {
    agent none

    stages {
stage('Build') {
    agent { label 'built-in' }
    tools { maven 'MAVEN' }
    steps {
        bat 'mvn clean install -DskipTests'
        stash includes: 'target/my-app-1.0-SNAPSHOT.jar', name: 'app-jar'
    }
}

stage('Run on Slave') {
    agent { label 'docker' }
    steps {
        unstash 'app-jar'
        sh 'java -jar my-app-1.0-SNAPSHOT.jar'
    }
}

    }
}
