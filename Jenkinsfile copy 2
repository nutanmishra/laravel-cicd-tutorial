pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Deploy') {
            steps {
                script {
                    // Build Docker image for Laravel
                    def laravelImage = docker.build('laravel-app', './var/www/html/laravel-cicd-tutorial')

                    // Push the image to a Docker registry if needed
                    // laravelImage.push()

                    // Deploy the Docker container
                    laravelImage.withRun('-p 80:80') {
                        // Container is running
                        sh 'docker ps'
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! Send notifications or perform other tasks here.'
        }
        failure {
            echo 'Pipeline failed! Send notifications or perform other tasks here.'
        }
    }
}
