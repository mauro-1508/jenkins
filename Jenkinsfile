pipeline {
    agent any

    environment {
        IMAGE_NAME = 'tuusuario/jenkins-test'
    }

    stages {

        stage('Clonar repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/mauro-1508/jenkins.git'
            }
        }

        stage('Build imagen') {
            steps {
                sh 'docker build -t %IMAGE_NAME% .'
            }
        }

        stage('Login Docker Hub') {
            steps {
                sh 'docker login -u TU_USUARIO -p TU_PASSWORD'
            }
        }

        stage('Push imagen') {
            steps {
                sh 'docker push %IMAGE_NAME%'
            }
        }
    }
}