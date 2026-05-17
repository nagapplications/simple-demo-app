pipeline {
    agent any

    tools {
        maven 'Maven'
        git 'Git'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',                                              // ✅ add this
                    url: 'https://github.com/nagapplications/simple-demo-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
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

        stage('Docker Build') {
            steps {
                sh '/usr/local/bin/docker docker build -t simple-demo-app:1.0 .'
            }
        }
    }
}