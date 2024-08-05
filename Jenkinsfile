pipeline {
    agent any

    stages {
        stage("Build") {
            environment {
                DB_HOST = 'localhost'
                DB_DATABASE = 'laravel'
                DB_USERNAME = 'app'
                DB_PASSWORD = 'admin123'
            }
            steps {
                sh 'php --version'
                sh 'composer install'
                sh 'composer --version'
                sh 'cp .env.example .env'
                sh 'echo DB_HOST=${DB_HOST} >> .env'
                sh 'echo DB_USERNAME=${DB_USERNAME} >> .env'
                sh 'echo DB_DATABASE=${DB_DATABASE} >> .env'
                sh 'echo DB_PASSWORD=${DB_PASSWORD} >> .env'
                sh 'php artisan key:generate'
                sh 'cp .env .env.testing'
                sh 'php artisan migrate'
            }
        }
        stage("Docker build") {
            steps {
                sh "docker build -t abhijith99954/laravel8cd ."
            }
        }
        stage("Deploy to staging") {
            steps {
                sh "docker run -d --rm -p 82:80 --name laravel8cd abhijith99954/laravel8cd"
            }
        }
        
    }
}
