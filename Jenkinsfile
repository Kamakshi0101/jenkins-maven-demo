pipeline {
    agent any
    tools {
        jdk 'JDK-17'
        maven 'Maven-3'
    }
    stages {
        stage('Test') {
            steps {
                bat 'mvn clean test'
            }
        }
    }
    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
}
