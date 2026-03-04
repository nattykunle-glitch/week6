
pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/nattykunle-glitch/week6.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ayokay1978/week6:latest .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub-password', variable: 'DOCKER_PASS')]) {
                    sh 'docker login -u ayokay1978 -p $DOCKER_PASS'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push ayokay1978/week6:latest'
            }
        }

    }
}
