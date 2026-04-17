pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Kavyaaps/devops.git'
            }
        }

      stage('Build') {
    steps {
        sh 'docker run --rm -v $PWD:/app -w /app maven:3.9.6-eclipse-temurin-17 mvn clean package'
    }
}

        stage('Docker Build') {
            steps {
                sh 'docker build -t petclinic-app .'
            }
        }

        stage('Run Compose') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Test') {
            steps {
                sh 'curl http://localhost:8080 || true'
            }
        }

        stage('Cleanup') {
            steps {
                sh 'docker compose down'
            }
        }
    }
}
