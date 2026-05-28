pipeline {
    agent any

    tools {
        jdk 'JDK-17'
        maven 'Maven-3'
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'master',
                url: 'https://github.com/kamakshi0101/jenkins-maven-demo.git'
            }
        }

        stage('Maven Build') {
            steps {
                bat 'mvn clean package'
            }
        }
    }
}
