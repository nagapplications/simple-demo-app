pipeline {
    agent any

    tools {
        maven 'Maven'
        git 'Default'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/nagapplications/simple-demo-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
    }
}