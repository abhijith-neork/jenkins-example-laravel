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
            }
        }
        stage("Docker build") {
            steps {
                sh "docker build -t danielgara/laravel8cd ."
            }
        }
        stage("Docker push") {
            environment {
                DOCKER_USERNAME = 'abhijith99954'
                DOCKER_PASSWORD = 'Abhijith@1'
            }
            steps {
                sh "docker login --username ${DOCKER_USERNAME} --password ${DOCKER_PASSWORD}"
                sh "docker push danielgara/laravel8cd"
            }
        }
        stage("Deploy to staging") {
            steps {
                sh "docker run -d --rm -p 80:80 --name laravel8cd danielgara/laravel8cd"
            }
        }
        
    }
}
