
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/react-node-cicd-sample.git'
            }
        }

        stage('Build Backend') {
            steps {
                sh 'docker build -t backend-app ./backend'
            }
        }

        stage('Build Frontend') {
            steps {
                sh 'docker build -t frontend-app ./frontend'
            }
        }

        stage('Run Containers') {
            steps {
                sh '''
                docker rm -f backend frontend || true
                docker run -d --name backend -p 5000:5000 backend-app
                docker run -d --name frontend -p 80:80 frontend-app
                '''
            }
        }
    }
}
