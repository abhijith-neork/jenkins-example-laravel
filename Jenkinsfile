pipeline {
    agent any

    stages {
        stage("Build") {
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
