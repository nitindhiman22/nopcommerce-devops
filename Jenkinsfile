pipeline {

    agent any

    environment {
        PROJECT_NAME = "nopcommerce"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/nitindhiman22/nopcommerce-devops.git'
            }
        }

        stage('Stop Existing Containers') {
            steps {
                sh 'docker compose down || true'
            }
        }

        stage('Build Docker Containers') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Run Docker Containers') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Verify Running Containers') {
            steps {
                sh 'docker ps'
            }
        }
    }

    post {

        success {
            echo 'Deployment Successful!'
        }

        failure {
            echo 'Deployment Failed!'
        }
    }
}
