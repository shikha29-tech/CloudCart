pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                echo 'Cloning Source Code...'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cloudcart:v1 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop cloudcart-container || true'
                sh 'docker rm cloudcart-container || true'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d --name cloudcart-container -p 80:80 cloudcart:v1'
            }
        }
    }
}
