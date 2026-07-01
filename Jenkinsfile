pipeline {
    agent any

    environment {
        IMAGE_NAME = "frontendd-login"
        IMAGE_TAG = "v2"
        CONTAINER_NAME = "frontendd-container"
    }

    stages {

        stage('Verify') {
            steps {
                sh '''
                pwd
                ls -la
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop ${CONTAINER_NAME} || true
                docker rm ${CONTAINER_NAME} || true

                docker run -d \
                  --name ${CONTAINER_NAME} \
                  -p 8081:80 \
                  ${IMAGE_NAME}:${IMAGE_TAG}
                '''
            }
        }

        stage('Verify Container') {
            steps {
                sh '''
                docker ps
                docker images
                '''
            }
        }
    }
}
