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
                script {
                    echo "Connecting to database at ${DB_HOST} with user ${DB_USERNAME}"
                    // Add your build steps here
                }
            }
        }
    }
}
