pipeline {
    agent any

    stages {

        stage('Clonar repositorio') {
            steps {
                git 'https://github.com/mauro-1508/jenkins.git'
            }
        }

        stage('Construir imagen Docker') {
            steps {
                sh 'docker build -t jenkins-test .'
            }
        }

        stage('Ejecutar contenedor') {
            steps {
                sh 'docker run -d -p 8001:8000 jenkins-test'
            }
        }
    }
}