pipeline {
    agent any

    stages {
        stage("Build") {
            environment {
                DB_HOST = credentials("34.224.74.83")
                DB_DATABASE = credentials("laravel")
                DB_USERNAME = credentials("app")
                DB_PASSWORD = credentials("admin123")
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
    }
}