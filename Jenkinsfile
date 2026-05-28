pipeline {

    agent any

    tools {
        jdk 'JDK-17'
        maven 'Maven-3'
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/YOUR-USERNAME/jenkins-maven-demo.git'
            }
        }

        stage('Run Tests with JaCoCo') {
            steps {
                bat 'mvn clean test'
            }
        }
    }

    post {

        always {

            junit 'target/surefire-reports/*.xml'

            publishHTML([
                reportDir: 'target/site/jacoco',
                reportFiles: 'index.html',
                reportName: 'JaCoCo Coverage Report',
                keepAll: true,
                alwaysLinkToLastBuild: true,
                allowMissing: false
            ])
        }
    }
}
