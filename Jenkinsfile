pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }

        stage('Stop Old Containers') {
            steps {
                sh 'docker compose down || true'
            }
        }

        stage('Build Containers') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Start Containers') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Show Running Containers') {
            steps {
                sh 'docker ps'
            }
        }
    }

    post {

        success {
            echo 'Application deployed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
