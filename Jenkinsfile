pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Git Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/fenotoky/demo-jenkins.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t fenotokyrak/demo-jenkins:1.0 .'
            }
        }

        stage('Docker Push') {
            steps {
                bat 'docker push fenotokyrak/demo-jenkins:1.0'
            }
        }
    }
}