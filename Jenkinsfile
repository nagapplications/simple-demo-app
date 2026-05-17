pipeline {
    agent any

    environment {
            PATH = "/usr/local/bin:/opt/homebrew/bin:/usr/bin:/bin:/usr/sbin:/sbin"
        }

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
                sh 'docker build -t simple-demo-app:1.0 .'
            }
        }
    }
}