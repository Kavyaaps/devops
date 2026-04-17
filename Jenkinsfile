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
                bat 'docker build -t petclinic-app .'
            }
        }

        stage('Run Compose') {
            steps {
                bat 'docker-compose up -d'
            }
        }

        stage('Test') {
            steps {
                bat 'docker-compose run test'
            }
        }

        stage('Cleanup') {
            steps {
                bat 'docker-compose down'
            }
        }
    }
}
