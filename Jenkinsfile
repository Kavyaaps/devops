pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Kavyaaps/devops.git'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t my-web-app .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker stop my-app || true'
                sh 'docker rm my-app || true'
                sh 'docker run -d -p 4000:80 --name my-app my-web-app'
            }
        }
        stage('Test') {
            steps {
                sh 'curl http://localhost:4000 || true'
            }
        }
    }
    post {
        success {
            echo 'Deployment successful! App running at http://localhost:4000'
        }
        failure {
            echo 'Pipeline failed. Check the logs above.'
        }
    }
}
