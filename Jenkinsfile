pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your version control system (e.g., Git).
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh "sudo chmod +x -R ${env.WORKSPACE}"
                // Install PHP and Composer
                sh 'sudo apt-get update && sudo apt-get install -y php-cli php-mbstring composer'

                // Install Laravel project dependencies
                sh 'composer install'
            }
        }

        stage('Run Tests') {
            steps {
                // Run PHPUnit tests
                sh 'php vendor/bin/phpunit'
            }
        }

        stage('Build and Deploy') {
            steps {
                // Build and deploy your Laravel application as needed.
                // You might use tools like Laravel Envoyer or deploy to a web server.

                // Example: Deploy to a remote server using SSH (customize accordingly).
                sh 'ssh root@103.16.222.38 "cd /var/www/html/laravel_cicd_tutorial && git pull && composer install && php artisan migrate"'
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
