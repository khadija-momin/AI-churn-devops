pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t churn-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop churn-container || true'
                sh 'docker rm churn-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5001:5000 --name churn-container churn-app'
            }
        }
    }
}