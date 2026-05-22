pipeline {
    agent any

    environment {
        IMAGE_NAME = "expense-tracker"
        IMAGE_TAG = "latest"
    }

    stages {

        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
                }
            }
        }

        stage('Show Docker Images') {
            steps {
                sh 'docker images'
            }
        }

    }

    post {
        success {
            echo 'Docker Image Built Successfully!'
        }

        failure {
            echo 'Build Failed!'
        }
    }
}