pipeline {

    agent any

    tools {
        jdk 'JDK-17'
        maven 'Maven-3'
    }
    // Automatic build test
    // triggers {
    //     pollSCM('H/2 * * * *')
    // }
    //githubPush()
    triggers {
        githubPush()
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'master',
                url: 'https://github.com/kamakshi0101/jenkins-maven-demo.git'
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