pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', 
                url: 'https://github.com/RamRatan07/applebite-php-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t applebite-php-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 80:80 --name php-app applebite-php-app'
            }
        }
    }

    post {
        failure {
            sh 'docker stop php-app || true'
            sh 'docker rm php-app || true'
        }
    }
}
