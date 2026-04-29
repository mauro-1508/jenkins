pipeline {
    agent any

    environment {
        IMAGE_NAME = 'mauro1508/jenkins-test'
    }

    stages {

        stage('Clonar repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/mauro-1508/jenkins.git'
            }
        }

        stage('Build imagen') {
            steps {
                sh 'docker build -t ${IMAGE_NAME} .'
            }
        }

        stage('Login Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Push imagen') {
            steps {
                sh 'docker push ${IMAGE_NAME}'
            }
        }
    }
}