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
                sh 'cp .env.example .env'
                script {
                    echo "Connecting to database at ${DB_HOST} with user ${DB_USERNAME}"
                    // Add your build steps here
                }
            }
        }
    }
}
