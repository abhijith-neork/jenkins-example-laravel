pipeline {
    agent any

    stages {
        stage("Build") {
             environment {
                DB_HOST = credentials("laravel-host")
                DB_DATABASE = credentials("laravel-database")
                DB_USERNAME = credentials("laravel-user")
                DB_PASSWORD = credentials("laravel-password")
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
}
