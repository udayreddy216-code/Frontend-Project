pipeline {

    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/udayreddy216-code/Frontend-Project.git'
            }
        }

        stage('Verify Files') {
            steps {
                sh 'pwd'
                sh 'ls -la'
            }
        }

    }

}
