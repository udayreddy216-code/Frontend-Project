pipeline {

    agent any

    environment {
        IMAGE_NAME = "frontend-login"
        IMAGE_TAG = "v1"
        CONTAINER_NAME = "frontend-container"
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

        stage('Run Docker Container') {
            steps {
                sh '''
                # Stop and remove the existing container if it exists
                docker stop ${CONTAINER_NAME} || true
                docker rm ${CONTAINER_NAME} || true

                # Run a new container
                docker run -d \
                    --name ${CONTAINER_NAME} \
                    -p 8080:80 \
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
