pipeline {

    agent any

    environment {
        IMAGE_NAME = "frontend-login"
        IMAGE_TAG = "v1"
    }

    stages {

        stage('Clone Repository') {
            steps {
                sh '''
                git clone https://github.com/udayreddy216-code/Frontend-Project.git
                '''
            }
        }

        stage('Verify') {
            steps {
                sh '''
                cd Frontend-Project
                pwd
                ls -la
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                cd Frontend-Project
                docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
                '''
            }
        }

    }

}
