pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {stages {
        stage('Build') {
            steps {
                git 'https://github.com/Kennibravo/jenkins-laravel.git'
                sh 'composer install'
                sh 'cp .env.example .env'
                sh 'php artisan key:generate'
            }
        }
        stage('Test') {
            steps {
                sh './vendor/bin/phpunit'
            }
        }
    }

    post {
        success {
            // Send a notification or perform actions when the pipeline succeeds.
            echo 'Pipeline succeeded! Send notifications or perform other tasks here.'
        }
        failure {
            // Send a notification or perform actions when the pipeline fails.
            echo 'Pipeline failed! Send notifications or perform other tasks here.'
        }
    }
}
